# Race Photos

Photos for the site live here, organised by event.

## Naming convention

```
images/<event-slug>/<filename>.jpg
```

- **`event-slug`** — lowercase, hyphens instead of spaces, matches the event name closely.
  Use the format `YYYY-MM-<short-name>`, e.g. `2026-03-jack-frost`, `2026-06-black-bear`.
- **Filenames** — sequential is fine: `photo1.jpg`, `photo2.jpg`, or more descriptive names
  like `start-line.jpg`, `podium.jpg`. Lowercase, no spaces.

### Example layout

```
images/
  2026-03-jack-frost/
    photo1.jpg
    photo2.jpg
    podium.jpg
  2026-06-black-bear/
    photo1.jpg
    start-line.jpg
```

## Adding a hero / card image

The first image you want to appear on the race card goes in the `image` field of the
race object in `SEED_RACES`. The rest go in the `gallery` array. Both use relative paths
from the repo root, e.g.:

```js
image: "images/2026-03-jack-frost/photo1.jpg",
gallery: [
  "images/2026-03-jack-frost/photo2.jpg",
  "images/2026-03-jack-frost/podium.jpg"
]
```

## Tips

- JPEG is fine for photos; keep files under ~1 MB for fast page loads.
- Don't use Imgur or other external image hosts — they may be blocked for UK visitors.
- Commit the images in the same commit as the race entry so everything lands together.
