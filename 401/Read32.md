# Permissions & Postgresql

## DRF Permissions
- permissions determine whether a request should be granted or denied access.
- request.user and request.auth properties: determine if the incoming request should be permitted.
- IsAuthenticated class in REST framework: allow or deny access.
- IsAuthenticatedOrReadOnly class in REST framework: full access vs read only.
- Permissions in REST framework: always defined as a list of permission classes.
- exceptions.PermissionDenied or exceptions.NotAuthenticated exception will be raised if any of the permission checks fail. 
- DIfferent HTTP responses:
```
HTTP 403 Forbidden response: request was successfully authenticated, but permission was denied OR request was not successfully authenticated, and the highest priority authentication class does not use WWW-Authenticate headers.

HTTP 401 Unauthorized response, with an appropriate WWW-Authenticate header:  request was not successfully authenticated, and the highest priority authentication class does use WWW-Authenticate headers.
```
- Object level permissions are used to determine if a user should be allowed to act on a particular object, which will typically be a model instance.
- ^ the above permissions are run by REST framework's generic views when .get_object() is called. Code example:
```
def get_object(self):
    obj = get_object_or_404(self.get_queryset(), pk=self.kwargs["pk"])
    self.check_object_permissions(self.request, obj)
    return obj
```
- call the .check_object_permissions(request, obj) method on the view at the point at which you've retrieved the object if you are writing your own views and want to enforce object level permissions.
- Defaults to allow unrestricted access:
```
'DEFAULT_PERMISSION_CLASSES': [
   'rest_framework.permissions.AllowAny',
]
```
- Example of setting the authentication policy on a per-view, or per-viewset basis, using the APIView class-based views:
```
from rest_framework.permissions import IsAuthenticated
from rest_framework.response import Response
from rest_framework.views import APIView

class ExampleView(APIView):
    permission_classes = [IsAuthenticated]

    def get(self, request, format=None):
        content = {
            'status': 'request was permitted'
        }
        return Response(content)
```
- AllowAny: will allow unrestricted access, regardless of if the request was authenticated or unauthenticated.
- IsAuthenticated: deny permission to any unauthenticated user, and allow permission otherwise.
- IsAdminUser: deny permission to any user, unless user.is_staff is True in which case permission will be allowed.
- IsAuthenticatedOrReadOnly: allow authenticated users to perform any request. Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; GET, HEAD or OPTIONS. 
- Django model permissions:
  - POST requests require the user to have the add permission on the model.
  - PUT and PATCH requests require the user to have the change permission on the model.
  - DELETE requests require the user to have the delete permission on the model.
- DjangoModelPermissionsOrAnonReadOnly: Similar to DjangoModelPermissions, but also allows unauthenticated users to have read-only access to the API.
- Django object permissions:
  - POST requests require the user to have the add permission on the model instance.
  - PUT and PATCH requests require the user to have the change permission on the model instance.
  - DELETE requests require the user to have the delete permission on the model instance.
- test if a request is a read operation or a write operation, you should check the request method against the constant SAFE_METHODS, which is a tuple containing 'GET', 'OPTIONS' and 'HEAD':
```
if request.method in permissions.SAFE_METHODS:
    # Check permissions for read-only request
else:
    # Check permissions for write request
```
- example of a permission class that checks the incoming request's IP address against a blocklist, and denies the request if the IP has been blocked:
```
from rest_framework import permissions

class BlocklistPermission(permissions.BasePermission):
    """
    Global permission check for blocked IPs.
    """

    def has_permission(self, request, view):
        ip_addr = request.META['REMOTE_ADDR']
        blocked = Blocklist.objects.filter(ip_addr=ip_addr).exists()
        return not blocked
```
- object-level permissions, that are only run against operations that affect a particular object instance:
```
class IsOwnerOrReadOnly(permissions.BasePermission):
    """
    Object-level permission to only allow owners of an object to edit it.
    Assumes the model instance has an `owner` attribute.
    """

    def has_object_permission(self, request, view, obj):
        # Read permissions are allowed to any request,
        # so we'll always allow GET, HEAD or OPTIONS requests.
        if request.method in permissions.SAFE_METHODS:
            return True

        # Instance must have an attribute named `owner`.
        return obj.owner == request.user
```
