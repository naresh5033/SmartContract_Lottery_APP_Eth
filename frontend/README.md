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

-   [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
-   [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Web3 UI kit

The notification provider is the web3uikit lib, as we enter the raffle the notification provider will pops up, and we did used tailwind postcss for the ui part which all us our div to set a classname for a real minimailsm,

## IPFS Deployment

This app has been deployed in the decentralized platform, which is very important for a dApp like this, the IPFS(A Distributed decentralized data structure) is the tool that we used.\
we can hash our data on the ipfs node and get our unique hash, then we can pin that hash to our node, and the athor nodes will pin our data and they can get a copy of our data on their node.\
And we keep doing this basically allow entire n/w to easily replicate any code or any data in a decentralized way\
with the cmd `yarn build and yarn next export ` we will get the pure static build dir "out" --> this we can use on our ipfs.
This dir was already pinned on my local node and the cid of this dir is (QmerirLNfCqeqipaiF3ZBp4qUxv6QjSsgnbocHGfFaLjbg) --> go to browser ipfs://QmerirLNfCqeqipaiF3ZBp4qUxv6QjSsgnbocHGfFaLjbg

## Hosting on Ipfs and Filecoin using fleek

The fleek makes it easy to build our apps on web3 - its like auto deployment(CD) for our websites, and additionally it helps us to pin our app with other nodes.
Once we deployed in fleek it will give a regular URL and also deploy our site on ipfs.

## File Coin

File coin is a BC that actually helps us to pin our data and uses decentralized storage.
