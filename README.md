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
2. Click **Connect** on Google Ads, Meta Ads, Shopify and GA4. Each shows read-only permissions, an authorizing step, an account picker and a data import. (All simulated.)
3. **Post-click report:** KPIs (revenue from Shopify), the click → order journey with the biggest leak in red, **Ad platforms vs Shopify** (what Meta/Google claim vs what Shopify confirms, platform ROAS vs true ROAS), trend, campaigns, landing pages, mobile vs desktop.
4. Filters: date range (incl. **Today so far**), channel, campaign, device, landing page.
5. **WhatsApp reports** — the core of the pitch:
   - The bot inside the team group: morning recap (total spend across channels, Shopify sales, true ROAS, overclaim, biggest leak), an alert, a team member asking a question.
   - **Type into the phone** to ask live, e.g. "aaj ka spend?" or "which channel is overclaiming?".
   - **How often it posts:** auto by spend (3x a day above ₹50k/day, otherwise morning + evening), or pick 3x / morning+evening / evening only.
   - **When to raise an alert:** "learn this brand's normal" vs "fixed rules" (with your thresholds). It shows how many alerts each would have sent last week, so the founder can see why learning mode means fewer false alarms.
6. **Ask AI** (sidebar or bottom-right button) — same brain as the WhatsApp bot. Questions from the call:
   - What's today's spend and sales across all channels?
   - Which channel is overclaiming vs Shopify? / Meta says 100 orders but Shopify shows 60, why?
   - What happened after people clicked?
   - Is anything wrong right now?
   - How do we compare with similar brands?
   Plus: which campaign to scale or cut, Meta ROAS drop, mobile checkout, landing pages, summary of yesterday, what to fix first. Every answer shows its data source.
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
