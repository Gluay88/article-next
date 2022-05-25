This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

\*\*\* Gluay Note

- npx create-next-app article-next --use-npm
- npm run dev
- index.js is Home (import styles from '../styles/Home.module.css)
- global.css is only imported in \_app.js
- install ES7 extention
- rafce
- Looks like for the pages won't work if we use lowercase for the file name (about.js -> - About.js)
- fixed it by using \_middleware.js in pages folder

```
import { NextResponse } from 'next/server';

const Middleware = (req) => {
  if (req.nextUrl.pathname === req.nextUrl.pathname.toLowerCase())
    return NextResponse.next();

  return NextResponse.redirect(`${req.nextUrl.origin}${req.nextUrl.pathname.toLowerCase()}`);
};

export default Middleware;
```

- inline style css
```
<style jsx>
    {`
        .title {
            color: red;
        }
    `}
</style>
```
- conditional style inline css
```
const style = 5
<style jsx>
    {`
        .title {
            color: ${style > 3 ? 'red' : 'blue'}
        }
    `}
</style>
```
- custom Document // Html, Head, Main, NextScript
- create _document.js 
- stop the server and run npm run dev again
This site was built using [Custom Document](https://nextjs.org/docs/advanced-features/custom-document#caveats).

** Fetch Data in index.js
```
{articles.map((article) => (
    <h3>{article.title}</h3>
))}
```
- create pages -> article folder -> [id] folder -> index.js file
- useRouter 
```
import { useRouter } from "next/router"

const article = () => {
    const router = useRouter()
    const {id} = router.query
  return (
    <div>This is an article {id}</div>
  )
}

export default article
```
- fallback: false -> return 404 page

** Static page
- package.json file 
```
"scripte" : {
    "build": "next build && next export"
}
```
- then stop the server and run npm run build
- npm run build
- you get the out folder
- sudo npm i -g serve
- serve -s out -p 8000 (serve out folder and port 8000)

# Prisma is an open-source ORM that drastically simplifies data modeling, migrations, and data access for SQL databases in Node. js and TypeScript.

- use data.js
