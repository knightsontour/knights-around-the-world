# Going live on Cloudflare Pages

The site is built and pushed. This is the **one step that needs your login** — it takes ~2 minutes in the Cloudflare dashboard. After this, every `git push` to `main` auto-rebuilds and deploys the site.

## Steps

1. Go to **https://dash.cloudflare.com** → sign in (create a free account if you don't have one).
2. Left sidebar → **Workers & Pages** → **Create** → **Pages** tab → **Connect to Git**.
3. Authorise GitHub if prompted, then pick the repo **`knightsontour/knights-around-the-world`**.
4. On the build-settings screen, enter:

   | Setting | Value |
   |---|---|
   | Production branch | `main` |
   | Framework preset | `Hugo` |
   | Build command | `hugo --gc --minify` |
   | Build output directory | `public` |

5. Expand **Environment variables (advanced)** and add:

   | Variable | Value |
   |---|---|
   | `HUGO_VERSION` | `0.162.1` |

   > If Cloudflare rejects that exact version, use the newest it offers (≥ 0.146). Beautiful Hugo needs a recent Hugo.

6. Click **Save and Deploy**. First build takes 1–3 min.
7. When it finishes you'll get a URL like **`https://knights-around-the-world.pages.dev`**.

## After the first deploy

- **If your `.pages.dev` name differs** from `knights-around-the-world`, update `baseURL` at the top of `hugo.toml` to match, then `git push` — otherwise some absolute links/RSS will point to the wrong host.
- **Custom domain** (optional): in the Pages project → **Custom domains** → add your domain and follow the DNS steps. Then set `baseURL` to that domain.

## Notes

- The theme is a **git submodule** (`themes/beautifulhugo`). Cloudflare clones submodules automatically — no action needed.
- Submodules require the repo to stay public, or Cloudflare needs access. It's currently public.
- Nothing here touches your Obsidian vault or the local `~/GitHub/hugo-output` working site.
