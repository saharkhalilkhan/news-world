# News World — website project

Responsive HTML/CSS/JavaScript news site with a custom logo/favicon, topic input search, article cards, video discovery links, SEO metadata, sitemap, robots.txt, and a Netlify serverless function.

## API key safety
The key you pasted in chat should be treated as exposed. Rotate/revoke it in your API provider dashboard and use the replacement only as a Netlify environment variable. Never add a key to `app.js`, HTML, or GitHub.

## Deploy
1. Create a GitHub repository named `news-world` and upload the files.
2. In Netlify choose **Add new site → Import an existing project**, connect GitHub and select the repository.
3. Publish directory is `.`; functions directory is configured in `netlify.toml`.
4. In Netlify site environment variables, add `NEWS_API_KEY` with your newly rotated key. Redeploy.
5. If your provider has a nonstandard endpoint, set `NEWS_API_BASE_URL` to its documented search endpoint. The function defaults to NewsAPI.org's `/v2/everything` endpoint and uses `q` for user-entered topics. Provider response formats vary.

## Important about the URL you sent
`https://api.newsapi.com/v1/current.json? key=...` has a space in the query string and does not match the standard NewsAPI.org documented endpoint. NewsAPI.org's current docs use `https://newsapi.org/v2/everything?q=TOPIC&apiKey=KEY`. Check your own provider's dashboard/docs before deployment; if it is a different service, update `NEWS_API_BASE_URL` and the query/key parameter logic in `netlify/functions/news.mjs`.

## Google logo
Replace `https://YOUR-SITE-NAME.netlify.app/` in `index.html`, `robots.txt`, and `sitemap.xml` with your real site URL. Add the site to Google Search Console and submit `/sitemap.xml`. Favicon and structured data are included, but Google controls whether/when a favicon appears in search results; it is not guaranteed.

## Video and posts
Users can enter a topic to search live news. Video cards currently open YouTube searches; replace them with your own video URLs if you prefer. Confirm your API plan and content usage/copyright terms before publishing.
