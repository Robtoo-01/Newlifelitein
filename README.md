# New Life Church Litein — Website

Website for **New Life Prayer Center and Church – Litein**, Kericho County, led by Pastor Rop.
Part of Newlife Prayer Center & Church (main church: Mavueni, Kilifi County).

- Sunday worship: 8:00 AM – 12:30 PM
- Office hours: 8:00 AM – 3:00 PM
- Location: near Litein Shopping Centre, opposite Koiwa Road junction
- Phone / WhatsApp: +254 741 277 938
- M-PESA Buy Goods Till: 6887385
- YouTube: [@pastorrop](https://www.youtube.com/@pastorrop)

---

## What's in this folder

```
index.html     The whole website (all 10 pages, styles and scripts)
images/        Photos used on the site
README.md      This file
```

It is a plain static site with no build step, database or server code. Any web host can serve it.

### Pages

| Address | Page |
|---|---|
| `#home` | Home: welcome, key info, coming-up event, services, latest sermons, testimonies |
| `#visit` | Plan Your Visit: times, directions, what to expect, FAQs |
| `#services` | Sunday worship, the four Newlife services, nightly online prayer |
| `#events` | Upcoming events, weekly gatherings, archive |
| `#watch` | Live stream, sermon playlist, message themes, devotional, FM/TV |
| `#stories` | Testimonies and photo gallery |
| `#give` | M-PESA giving, giving categories, receipts |
| `#about` | Story, mission, Pastor Rop, beliefs, ministries, Newlife family |
| `#contact` | Map, address, phone, office hours |
| `#prayer` | Prayer request / testimony / counselling form |

---

## Preview it

Open `index.html` in any browser, on a computer or a phone. No internet is needed except for fonts, the map and YouTube videos.

## Put it online

Choose one option.

**GitHub Pages (free)**
1. Create a repository, for example `newlife-litein`.
2. Upload `index.html`, the `images` folder and this README.
3. Go to **Settings → Pages**, set the source to the `main` branch and the `/ (root)` folder, then save.
4. The site goes live at `https://<username>.github.io/newlife-litein/`.
5. For a custom domain (for example `newlifelitein.org`), add it under **Settings → Pages → Custom domain** and point the domain's DNS to GitHub.

**Netlify (free)**
Drag this folder onto [app.netlify.com/drop](https://app.netlify.com/drop).

**cPanel or any web host**
Upload the contents of this folder into `public_html/`.

---

## Updating content

Most routine updates happen in **one block** near the bottom of `index.html`. Search for `CONTENT DATA`.

### 1. Events

```js
const LAST_CHECKED = '2026-10-22';   // change this whenever you review dates

const EVENTS = [
  {title:'Abrahamic Star & Cross Border Anointing', service:'abrahamic',
   start:'2026-10-21', end:'2026-10-25', time:'Daily from 1:00 PM',
   desc:'Five days of worship, prophetic prayer and anointing...'},
  ...
];
```

- Dates use the `YYYY-MM-DD` format.
- `service` must be one of `communion`, `healing`, `abrahamic` or `above`. This is how each service card shows its next date.
- Add `replay:true` to show a "Watch replay" button once the event has passed.
- **The site handles everything else automatically:**
  - Before an event starts, it shows as "Coming up".
  - While it runs, it shows as "Happening now" and appears in the red top bar.
  - Once its end date has passed, it moves to the archive.
  - If nothing is scheduled, the home page shows the next Sunday service instead.

To test how the site will look on another date, add `?today=YYYY-MM-DD` to the address, for example `index.html?today=2026-11-01#events`.

### 2. Services

Each of the four services in `SERVICES` has its own text fields:

| Field | What it holds |
|---|---|
| `name` | Service name |
| `freq` | How often it runs |
| `time` | Time of day |
| `short` | Card text on the home page |
| `long` | Paragraphs on the Services page |
| `who` | Who can come |

### 3. Testimonies

```js
const TESTIMONIES = [
  {name:'Jane', place:'Litein', ctx:'Testimony Service · Oct 2026', q:'Her words here...'},
];
```

Only publish testimonies where the person gave **written or WhatsApp consent**. Use their first name and town only.

### 4. Photos

To replace a photo, keep the same file name inside `images/`. Photos should be JPG, around 1400px wide and under 300 KB each.

| File | Where it appears |
|---|---|
| `congregation.jpg` | Home banner, gallery, About |
| `banner.jpg` | Welcome poster, Plan Your Visit |
| `garden.jpg` | Events, About, gallery |
| `choir.jpg` | Testimonies page, gallery |
| `worship.jpg` | Services, Give, Prayer, gallery |
| `pastor-blue.jpg` | Watch page, gallery |
| `pastor-garden.jpg` | Pastor Rop on the About page |
| `pastor-walk.jpg` | Plan Your Visit, gallery |

Only use photos of identifiable people with their consent.

### 5. Other text

For anything else, such as the pastor's bio, beliefs, ministries or FAQs, search `index.html` for the wording you want to change and edit it directly.

---

## Links still to add

The church will share these links. When each one arrives, search `index.html` for the text in the right-hand column and update it.

| Item | Search for |
|---|---|
| Pastor Rop's Facebook page | `facebook.com/search` |
| Shine Jesus FM listen-live link | `Listen-live link coming soon` |
| Shine Jesus TV stream link | `Stream link coming soon` |
| Church email | `Email and postal address to be added` |
| Postal address | `Email and postal address to be added` |
| Exact map pin for the gate | `Koiwa%20Road%20Junction` and `Koiwa+Road+Junction` |

The yellow dashed boxes on the site mark text that still needs checking. Remove each one once its item is confirmed. You can find them all by searching for `class="note"`.

---

## How the forms work

The prayer request, testimony and counselling forms do **not** store anything on a server. When someone submits, WhatsApp opens with their message addressed to **0741 277 938**, and they tap **Send**.

- Anonymous requests leave out the person's name and phone number.
- Testimonies include a yes/no for permission to share.
- To change the receiving number, search for `254741277938` and replace every occurrence.

## Analytics (optional)

The site already records key actions: page views, plan-your-visit clicks, directions, calls, WhatsApp, video plays, prayer submissions and copying the till number. To see them:

1. Create a Google Analytics 4 property and copy its Measurement ID (it looks like `G-XXXXXXX`).
2. Paste this just before `</head>` in `index.html`:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXX"></script>
<script>window.dataLayer=window.dataLayer||[];function gtag(){dataLayer.push(arguments)}gtag('js',new Date());gtag('config','G-XXXXXXX');</script>
```

3. Review the results monthly.

---

## Maintenance routine

Track every item in **newlife-litein-content-inventory.xlsx**. Each row has an owner, an expiry date and a next action, and the review flag highlights anything expired or overdue.

| When | Task |
|---|---|
| Weekly | Update the next event and publish a new devotional on the Watch page (search `Devotional`). Check that the live stream works and that prayer requests are answered. |
| Monthly | Confirm service dates and times, add new events, add gallery photos, and test the phone, WhatsApp, map and forms. Update `LAST_CHECKED`. |
| Quarterly | Review every page on a phone, remove outdated text, and check that the giving details are correct. |

**Rule:** no event, schedule, testimony or giving change goes live until its named owner in the inventory has reviewed it.

---

## Technical notes

- The site is a single page that switches between sections, so the page links above (`#home`, `#visit` and so on) all live inside `index.html`.
- Fonts come from Google Fonts (Fraunces and Inter). Videos are embedded from YouTube and load only when someone taps play, which keeps the site fast on mobile data.
- The site works on phone and desktop screens, supports keyboard navigation, and includes structured church information for search engines.
- `newlife-litein-site.html` is a separate preview copy with the photos built in. For hosting, use the files in this folder.
