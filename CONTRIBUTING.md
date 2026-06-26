# Adding a new race report

The site is a single `index.html` file. Race reports live in a JavaScript array called
`SEED_RACES` near the bottom of the `<script>` section (around line 1082). To add a new
report, edit that array and commit.

---

## 1. Add your photos first

Put photos in `images/<event-slug>/`, e.g.:

```
images/2026-07-isle-of-man/photo1.jpg
images/2026-07-isle-of-man/start-line.jpg
```

See [`images/README.md`](images/README.md) for the full naming convention.

---

## 2. Add a new entry to `SEED_RACES`

Open `index.html` and find `const SEED_RACES = [`. Add a new object at the **end of
the array** (before the closing `];`). Copy this template and fill it in:

```js
{
  id: "seed-12",                    // increment from the last entry
  type: "race",                     // "race" or "journal"
  event: "Event name here",
  date: "2026-07-05",               // ISO date YYYY-MM-DD
  result: "3rd in class",           // short result string shown on the card
  location: "Isle of Man, UK",
  image: "images/2026-07-isle-of-man/photo1.jpg",   // card hero image
  gallery: [                        // optional extra photos shown in the modal
    "images/2026-07-isle-of-man/start-line.jpg"
  ],
  video: "",                        // YouTube embed URL, or leave empty ""
  tags: ["championship", "podium"], // lowercase, used for filtering
  donateUrl: "",                    // GoFundMe link if relevant, or leave empty ""
  featured: false,                  // set true to pin to the top of the feed
  report: "Your race report text.\n\nSupports \\n for paragraph breaks.",
  seed: true                        // always set this to true
},
```

### Field reference

| Field | Required | Notes |
|---|---|---|
| `id` | yes | Unique string — keep incrementing `seed-N` |
| `type` | yes | `"race"` or `"journal"` |
| `event` | yes | Full event name |
| `date` | yes | `YYYY-MM-DD` — controls sort order |
| `result` | yes | Short string shown on the card, e.g. `"3rd in class"` |
| `location` | no | Free text |
| `image` | yes | Hero image — relative path like `images/slug/photo1.jpg` |
| `gallery` | no | Array of additional image paths |
| `video` | no | YouTube embed URL or empty string |
| `tags` | no | Array of lowercase strings |
| `donateUrl` | no | Full URL to a donation/fundraiser page |
| `featured` | no | `true` to pin at the top of the feed |
| `report` | yes | Full report text; use `\n\n` for paragraph breaks |
| `seed` | yes | Always `true` |

---

## 3. Commit and push

```bash
git add index.html images/
git commit -m "Add race report: <event name>"
git push
```

GitHub Pages redeploys automatically within a minute or two. Refresh
`https://charlottek28.github.io/Charlotte-Knight-Racing/` to see the update.

---

## Notes

- The in-browser "Add race report" form only works in the Claude chat environment —
  it won't save anything when the site is live. This is expected. All reports are added
  by editing `SEED_RACES` directly.
- The current hero images in existing entries are base64-encoded inline. New entries
  should always use a relative file path instead.
- Don't use Imgur or other external image hosts — they may be blocked for UK visitors.
