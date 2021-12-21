# React 3

## NextJs
- a page is a React Component exported from a file in the pages directory.
- Example of a new page component:
```
export default function FirstPost() {
  return <h1>First Post</h1>
}
```
- To link between pages, first import Link:
```
import Link from 'next/link'
```
- Example of using Link:
```
<h1 className="title">
  Read{' '}
  <Link href="/posts/first-post">
    <a>this page!</a>
  </Link>
</h1>

Note:

{' '} adds an empty space, which is used to divide text over multiple lines.
```
- Linking back home from our new page we linked to:
```
import Link from 'next/link'

export default function FirstPost() {
  return (
    <>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </>
  )
}
```
- The Link component enables client-side navigation between two pages in the same Next.js app.
- Client-side navigation means that the page transition happens using JavaScript, which is faster than the default navigation done by the browser.
- Next.js does code splitting automatically, so each page only loads what’s necessary for that page.
- Whenever Link components appear in the browser’s viewport, Next.js automatically prefetches the code for the linked page in the background.
- Next.js can serve static assets, like images, under the top-level public directory.
- 'next/image is an extension of the HTML <img> element, evolved for the modern web.
- Images load as they are scrolled into viewport.
- Example of using next/image:
```
import Image from 'next/image'

const YourComponent = () => (
  <Image
    src="/images/profile.jpg" // Route of the image file
    height={144} // Desired size with correct aspect ratio
    width={144} // Desired size with correct aspect ratio
    alt="Your Name"
  />
)
```
- Import Head component: 
```
import Head from 'next/head'
```
- you can add global CSS files by importing them from pages/_app.js.
- CSS modules are useful because they scope styles at the component level. 




