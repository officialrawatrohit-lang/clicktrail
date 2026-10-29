# ClickTrail — demo dashboard

A clickable demo of a post-click reporting product for e-commerce founders. It's one file (`index.html`) with no build step, no backend and no API keys. Every number is dummy data generated in the browser. No real Google, Meta, Shopify or GA4 account is ever contacted.

## Make it live (pick one, ~2 minutes)

**Netlify Drop (easiest, no account setup):**
1. Go to app.netlify.com/drop
2. Drag the folder containing `index.html` onto the page
3. You get a live link immediately. Rename the site in Site settings if you want a nicer URL.

**Vercel:**
1. Put `index.html` in a folder, then run `npx vercel` in that folder (or import the folder/repo at vercel.com/new)
2. Framework preset: "Other". No build command. Output directory: `.`

**GitHub Pages:**
1. Create a repo, upload `index.html` to the root
2. Settings → Pages → Deploy from branch → `main` / root

## How to run the demo for a founder

1. Open the link. You land on **Integrations**.
2. Click **Connect** on Google Ads, Meta Ads, Shopify and GA4. Each one shows a permissions screen, an authorizing step, an account picker and a data import. (All simulated.)
3. Click **View report** → the **Post-click report**: KPIs, the click → order journey with the biggest leak highlighted, trend chart, Google vs Meta, campaigns (click a row to filter), landing pages, mobile vs desktop.
4. Use the filters: date range, channel, campaign, device, landing page.
5. Click **Ask AI about your report** (bottom right) or **Ask AI** in the sidebar and ask questions, e.g.
   - Where am I losing customers after the click?
   - Which campaign should I scale? / Which campaign is wasting money?
   - Google vs Meta — which is better?
   - Why is my Meta ROAS dropping?
   - How is mobile checkout doing? / Which landing page is hurting me?
   - Summary of yesterday / What should I fix first?
   The assistant answers from the same numbers as the report and respects the active filters.
6. **WhatsApp reports** shows the daily report as it would arrive on the phone.
7. To start fresh before the next demo: **Settings → Reset**, or open the link with `?reset` at the end.

## Customising

Edit the `CONFIG` block near the top of the `<script>` in `index.html`:

```js
const CONFIG = {
  appName: 'ClickTrail',          // your product name
  storeName: 'Kesar Lane',        // demo brand shown in the dashboard
  storeDomain: 'kesarlane.in',
  shopifyHandle: 'kesar-lane',
  whatsappNumber: '+91 98XXX X4321',
  breakevenRoas: 2.0,
  seed: 20261030                  // change for different (stable) numbers
};
```

Campaign names, landing pages and their behaviour are in the `CAMPAIGNS` and `LPS` lists right below it.

## Notes

- The chatbot is rule-based on purpose: it works offline, never makes up numbers, and needs no API key. It can be swapped for a real LLM later by sending the filtered data to a small serverless function.
- Connection state and chat history are saved in the viewer's browser only.
