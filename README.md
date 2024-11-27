This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.js`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.

## identified Bugs:

1. Navigation links in the layout.js file were missing a href attribute and the links weren't properly routed.

2. Multiple errors:

- Incorrect API URL causes the Pokemon list to fail.
- The "useEffect" dependency causes an infinite loop.
- No error handling for failed requests.

3. Clicking a Pokémon link routes incorrectly (e.g., pokemon?id=1 instead of /pokemon/1).

4. The About page lacked navigation back to the Home page.

5. The link was broken because the id was not properly inserted into the URL. The fetch request lacked error handling, and the Pokémon image was being accessed incorrectly.

## identified fixs:

1. Updated the navigation by integrating Next.js <Link> component to ensure proper routing between pages.

2. Multiple fixes:

- Updated the API URL to https://pokeapi.co/api/v2/pokemon?limit=10
- Removed pokemonList from the useEffect dependency array to prevent unnecessary re-renders
- Added a try-catch block for erro handling in the API request.

3. The Pokémon details link used the wrong format, leading to incorrect routing (pokemon?id=1 instead of /pokemon/1) so I updated the link to use Next.js dynamic routing syntax:

4. Added a <Link> component for navigation just like I did for the first bug regaurding the home page.

5. Corrected the link construction to use template literals such as ${id}, Added a try-catch block for error handling when fetching data, and lastly I used the correct property for displaying the Pokemon Image which was <img src={pokemon.sprites.front_default} alt={pokemon.name} />

## What I leanred:

- Through fixing the data fetching issues, I learned how dependencies in useEffect can cause infinite loops if not managed correctly. As I had actually encountered this very issue in my group project when I was trying to fetch an Image but it just kept reloading the Image over and over again never actually displaying it on the webpage. Another thing is that I also gained a better understanding of error handling in asynchronous operations with the try-catch pattern.

- The dynamic routing bug taught me how Next.js handles dynamic URL paths and the importance of using the correct syntax for generating routes. It was especially helpful since I had several pages that I had wanted to route to one another and didn't know how to accomplish that but after learning that you can use the <Link> component it became extremely helpful.

- Lastly working with the Pokémon details page helped me refine my skills with template literals, destructuring, and working with API data, including handling potential errors in the fetch process.
