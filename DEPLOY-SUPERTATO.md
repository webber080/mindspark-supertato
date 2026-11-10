# MindSpark at mind.supertato.top

The frontend is deployed as the Cloudflare Worker `mindspark-supertato` on the custom domain `mind.supertato.top`. Maps are saved to the private GitHub repository `webber080/mindspark-maps`.

## Sign in and save maps

Create a GitHub fine-grained personal access token at https://github.com/settings/personal-access-tokens/new. Select **Only select repositories** → `mindspark-maps`, then grant **Repository permissions → Contents: Read and write**. Paste the token into the sign-in form on https://mind.supertato.top. Do not commit the token or send it in a message. Create a test map, refresh the page, and confirm it remains available.

## Redeploy

Cloudflare currently hosts static files uploaded from `public/` through the dashboard. This GitHub fork is not connected to automatic deployment. From this repository root, `npm install` and `npx wrangler deploy` will deploy the same assets with `wrangler.jsonc`. The custom domain is declared in that file. Check for a conflicting DNS record before redeploying.

GitHub OAuth sign-in and live collaboration need a separate Worker from `worker/`, a GitHub OAuth App, and corresponding secrets. They are currently disabled; see `worker/README.md` before enabling them.
