# Deploying Next.js to a Plesk server

Once, I had to deploy a Next.js app to a Plesk server for a client. It took some time to figure out, since existing guides had drawbacks, such as functionality loss or the need to do a lot of things manually.

This way will work exactly as it should (SSR, app directory, API routes, TRPC if you end up using it, etc.), and, once set up, it'll be the same as deploying any other Node.js app (so you should be able to deploy any other Node.js app to Plesk as well to benefit from this guide).

The app is the default one bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app), but slightly modified. It serves more as a guide than a template, so applying the following modifications should make your app ready for deployment on a Plesk server:

- First, there is an additional `server.js` file. It serves as an entry point for the whole app.
- Second, the `package.json` file has a new script: `"start": "node server.js"`. This script is used to start the app in production mode, instead of the default Next.js script `next start`.

## How to deploy

1. Clone this repository to your local machine.
2. Somehow upload the files to your Plesk server. You can use the Plesk File Manager, the Git extension, or whatever you like.
3. Follow the regular Node.js flow according to your version (setting up the URL, installing dependencies, etc. ), but, as the application entry point, use `server.js`.
4. Run `npm run build` to build the app (includes the backend stuff, as well as SSG and frontend build).
5. Run the app according to your Plesk version.

**Note**: if you seem to have done everything correctly and it does not work, restarting the server might help. Happened a few times when I was doing this.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
