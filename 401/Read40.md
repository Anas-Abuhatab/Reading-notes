# React 4

## Next.js - Dynamic RoutesNext.js - Deployment
- Steps to statically generate pages with dynamic routes (page at path called /posts/<id> where <id> can be dynamic):
1. create a page at /pages/posts/[id].js - page must contain:
    1. A React component to render this page.
    2. getStaticPaths which returns an array of possible values for id.
    3. getStaticProps which fetches necessary data for the post with id. 
- For the getStaticPaths, we want to add the below inside lib/posts.js. This will return list of file names (excluding .md) in the 'posts' directory:
```
export function getAllPostIds() {
  const fileNames = fs.readdirSync(postsDirectory)

  return fileNames.map(fileName => {
    return {
      params: {
        id: fileName.replace(/\.md$/, '')
      }
    }
  })
}    
```

- Import and use getAllPostIds inspide the getStaticPaths()
```
import { getAllPostIds } from '../../lib/posts'

export async function getStaticPaths() {
  const paths = getAllPostIds()
  return {
    paths,
    fallback: false
  }
}
```
- In our pages/posts/[id].js file we want to:
```
Replace:
import { getAllPostIds } from '../../lib/posts'
with:
import { getAllPostIds, getPostData } from '../../lib/posts'

export async function getStaticProps({ params }) {
  const postData = getPostData(params.id)
  return {
    props: {
      postData
    }
  }
}
```
- async/await allow you to fetch data asynchronously.

## Next.js - Deployment
- Before deploying, you must push to github. 
- Create account on vercel and link your github. 
- You can give access to all repos.
- Use default settings as these are optimal build settings. 
- Build should finish in under one minute. 
- Other features of vercel:
    - Custom Domains
    - Env variables
    - Automatic HTTPS
- When you have a pull request open, Vercel automatically creates a preview deployment for that branch on every push.
- DPS: Develop, Preview, Ship. 