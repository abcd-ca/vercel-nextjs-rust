# Overview

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app). It contains a NodeJS API lambda and a Rust lambda

This works using Vercel CLI 28.16.7. Before I was on a lower 28.x.x. I forget the Xs but major number was definitely 28 and the app wouldn't deploy with the Rust lambda.

# Deploy to Vercel

1. `vercel --prod`. Accept all the defaults
3. View the endpoints at the resulting url:
  * Javascript lambda: `<url from deployment>/api/hellojs`
  * Rust lambda: `<url from deployment>/api/hellorust`

# Work locally

To get it to work locally, there's a trick, though I've been discussing this with Vercel and a ticket has been submitted with the Vercel CLI team which I expect will streamline this:

1. `vercel dev --debug` Look for a line that contains `Spawning dev command: next dev --port 50434`. The port number differ from this one but it shows that the NextJS API endpoints are running on a different port than the Rust API endpoints which are on port `3000` (Thanks to Vercel for this tip)
2. View the endpoints at the resulting url:
  * Javascript lambda: http://localhost:50434/api/hellojs
  * Rust lambda: http://localhost:3000/api/hellorust
