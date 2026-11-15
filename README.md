**[Facebook Reviews Scraper](https://apify.com/dz_omar/facebook-reviews-scraper?fpr=smcx63)** collects the reviews of any public Facebook page: who recommends it, who does not, what they wrote, when, and how the page answered. Paste page links, click **Start**, download JSON, CSV or Excel. No Facebook account, no cookies.

Perfect for **reputation monitoring**, **competitor research** and **customer-feedback analysis** when you need every review in a spreadsheet instead of scrolling a page.

## What does Facebook Reviews Scraper do?

Facebook reviews are not star ratings: each reviewer **recommends** the page or **does not recommend** it, optionally with text, tags and photos. This Actor returns all of that, plus the conversation under each review.

- **Recommends or not** on every review, so negative feedback is one filter away.
- **The page's own reply** in a dedicated field, with the full comment thread and replies.
- **Date filter** — only reviews newer than a date or a period such as `3 months`.
- **Many pages in one run**, with the page's overall recommend % and review count on every row.
- **Reviewer details**, photos with sizes, tags, reactions by type, comments and shares.

### What data can you extract from Facebook reviews?

| Category | Fields |
|---|---|
| Review | `text`, `date`, `timestamp`, `isRecommended`, `tags`, `photos`, `url`, `id`, `legacyId` |
| Engagement | `likesCount`, `reactions`, `commentsCount`, `sharesCount` |
| Conversation | `ownerReply`, `comments` (with `replies`) |
| Reviewer | `user.id`, `user.name`, `user.profileUrl`, `user.profilePic` |
| Page | `pageName`, `facebookId`, `facebookUrl`, `pageRecommendPercent`, `pageReviewsCount` |

### Why use Facebook Reviews Scraper on Apify?

Running it on Apify gives you **API access**, **scheduling**, **monitoring**, **integrations** (Make, Zapier, n8n, webhooks) and **proxy rotation** without managing infrastructure. Schedule it daily with *Only reviews newer than* `1 day` to track new feedback as it arrives.

## How to scrape Facebook reviews

1. Open Facebook Reviews Scraper in Apify Console.
2. Add the link of each Facebook page, for example `https://www.facebook.com/nasa`.
3. Set **Maximum reviews per page** (start small: `50`).
4. Optional: choose a date or **Which reviews** (all, only those that recommend, only those that do not).
5. Click **Start**, then download the results as JSON, CSV or Excel, or fetch them over the API.

## How much does it cost to scrape Facebook reviews?

You pay per review delivered, a small fee for each page that returns reviews, and a start fee. Prices depend on your Apify plan:

| Event | FREE | BRONZE | SILVER | GOLD |
|---|---|---|---|---|
| Review | $0.0020 | $0.0016 | $0.0013 | $0.0011 |
| Page scraped (once per page with reviews) | $0.0020 | $0.0020 | $0.0020 | $0.0020 |
| Actor start (once per run) | $0.0020 | $0.0020 | $0.0020 | $0.0020 |

- **1,000 reviews** cost about **$2.00** on the FREE plan and **$1.10** on GOLD (+ page and start fees).
- Example (FREE plan): 20 reviews from one page = 20 × $0.002 + $0.002 page + $0.002 start = **$0.044**.
- Pages with no visible reviews, links that are not pages, and notice rows are never charged.
- Set **Max cost per run** to cap spending: the Actor stops at the cap and delivers exactly what was charged.
- Test with `10` reviews first.

## Input and output examples

### Input

```json
{
    "startUrls": [
        { "url": "https://www.facebook.com/copperkettleyqr" },
        { "url": "https://www.facebook.com/LaTagliatella" }
    ],
    "resultsLimit": 100,
    "onlyReviewsNewerThan": "6 months",
    "recommendation": "not_recommended"
}
```

| Field | What it does |
|---|---|
| `startUrls` | Facebook page links. A link ending in `/reviews` works too. |
| `resultsLimit` | Maximum reviews per page, newest first. Use `100000` for every review available. |
| `onlyReviewsNewerThan` | A date (`2025-01-31`) or a period (`3 months`, `2 weeks`). Empty = all dates. |
| `recommendation` | `all` (default), `recommended` or `not_recommended`. |

### Output

```json
{
    "facebookUrl": "https://www.facebook.com/LaTagliatella",
    "id": "UzpfSTYxNTgw…",
    "legacyId": "122120593707001727",
    "url": "https://www.facebook.com/******/posts/pfbid0…",
    "date": "2025-12-29T21:36:23.000Z",
    "isRecommended": false,
    "text": "El peor servicio que he conocido.",
    "tags": [],
    "photos": [],
    "likesCount": 1,
    "reactions": { "sad": 1 },
    "commentsCount": 6,
    "ownerReply": {
        "text": "Sentimos lo sucedido, ¿nos puedes dar más detalles por mensaje privado?",
        "date": "2026-01-04T12:10:27.000Z",
        "author": "Restaurantes La Tagliatella"
    },
    "user": { "id": "pfbid0…", "name": "******", "profileUrl": null, "profilePic": "https://scontent…" },
    "facebookId": "100064590497842",
    "pageName": "Restaurantes La Tagliatella",
    "pageRecommendPercent": 74,
    "pageReviewsCount": 2015,
    "inputUrl": "https://www.facebook.com/LaTagliatella"
}
```

The dataset has three ready-made views: **Reviews**, **Reviewers** and **Page summary**. A row with a `notice` field instead of a review explains a link that could not be read, and is free.

## Other Actors you might need

| Actor | What it adds |
|---|---|
| **[Facebook Posts Scraper](https://apify.com/dz_omar/facebook-posts-scraper?fpr=smcx63)** | Posts from pages, profiles and public groups |
| **[Facebook Comment Scraper](https://apify.com/dz_omar/facebook-comment-scraper?fpr=smcx63)** | Comments on any post, reel or video |
| **[Trustpilot Reviews Scraper](https://apify.com/dz_omar/trustpilot-reviews-scraper?fpr=smcx63)** | Star-rated reviews with company replies |

## Frequently asked questions

### How many reviews can I get from a page?

Every review Facebook makes public to visitors who are not logged in. For small and mid-size pages that is all of them. For very large pages Facebook shows only part of what the page reports (for example 265 of 2,015); the run log tells you when this happens. The page's reported total is in `pageReviewsCount`.

### Why are some reviews missing text?

A reviewer can recommend a page without writing anything. Those reviews are still delivered, with `text` empty.

### Is it legal to scrape Facebook reviews?

The Actor reads only information that is public. You are responsible for how you use it; follow Facebook's terms and data-protection law such as GDPR and CCPA, especially for reviewer names. This is not legal advice.

### Do I need a Facebook account or cookies?

No. Public pages work with links only.

### Can I move over from another Facebook reviews scraper?

Yes. `startUrls`, `resultsLimit` and `onlyReviewsNewerThan` use the same names as other Facebook reviews scrapers, so a saved input usually runs unchanged. `id`, `legacyId`, `user`, `date`, `url`, `isRecommended`, `text`, `tags`, `likesCount`, `commentsCount`, `facebookId`, `pageName` and `inputUrl` keep their names. `commentsCount` here is Facebook's own total, including replies.

### Can I use it in Make, Zapier, n8n or my own code?

Yes — through Apify's integrations, webhooks and the API (JavaScript and Python clients).

### What happens if a link is not a page?

Group, post, photo and event links are skipped with a notice row that says what to paste instead. Nothing is charged for them.

## Support

- 🌐 **Website:** [flowextractapi.com](https://flowextractapi.com)
- 📧 **Email:** [flowextractapi@outlook.com](mailto:flowextractapi@outlook.com)
- 💬 **GitHub:** [FlowExtractAPI](https://github.com/FlowExtractAPI)
- 💼 **LinkedIn:** [flowextract-api](https://www.linkedin.com/in/flowextract-api/)
- 🐦 **X (Twitter):** [@FlowExtractAPI](https://x.com/FlowExtractAPI)
- 📱 **Facebook:** [flowextractapi](https://www.facebook.com/flowextractapi)
- 🎵 **TikTok:** [@flowextractapi](https://www.tiktok.com/@flowextractapi)

## Legal & compliance

- **Public data only** — processes publicly available data.
- **Rate limiting** — respects source-service limits and terms of use.
- **Data protection** — no storage of personal information or unauthorized data collection.
- **Commercial use** — suitable for business intelligence and research.
- No affiliation with or endorsement by Facebook or Meta is implied.

---

*Facebook Reviews Scraper — by FlowExtract API. Turn any website into structured data.*
