# Fashion News Digest

A nightly digest of the most relevant and influential news on fashion, fashion tech, apparel tech, fashion e-commerce and AI in fashion, plus adjacent stories that move fashion attention (celebrity outfits at major events, viral fashion moments, big launches, deals and funding).

Built every night at about 03:35 Europe/Rome by a scheduled Claude task for PiktID / On-Model, from X, TikTok and major fashion and tech news sources.

## How agents should use this

1. Start with `data/latest.json` (structured) or `latest.md` (readable).
2. Items are ranked: `rank` 1 is the most important. `influence_score` (1-10) combines reach, engagement, source authority and relevance for a fashion e-commerce / AI imagery company.
3. Cite `source_urls`, not this repo. Summaries are paraphrased; open the source for exact wording.
4. `verified: false` marks a social claim not yet confirmed by a news source. Treat it with care.
5. `is_update: true` marks a story already covered on an earlier day, with a new development.
6. Images: `image.preview_path` is a small copy in this repo (max 800 px). `image.drive_url` is the full-resolution file in Google Drive. There are no photos of real, identifiable people; celebrity outfits are described in words.

## Layout

```
README.md
latest.md                      # today's digest (image paths relative to repo root)
index.md                       # newest-first list of all digests
digests/YYYY/YYYY-MM-DD.md     # daily digest, readable
data/YYYY-MM-DD.json           # daily digest, structured
data/latest.json               # copy of the newest daily JSON
images/YYYY/MM-DD/<slug>.jpg   # previews, max 800 px wide
```

Full-resolution images: Google Drive folder "Fashion News Digest – Images", subfolders `YYYY/MM-DD/`:
https://drive.google.com/drive/folders/14geDgVbwkEN3mN51MtqKK1jYKNpevL5A

## Categories

- Fashion tech & AI
- E-commerce & retail business
- Brands, launches & deals
- Celebrity & red carpet
- Social trends (X/TikTok)

## JSON schema

```json
{
  "date": "YYYY-MM-DD",
  "generated_at": "ISO 8601 timestamp",
  "drive_day_folder_url": "https://drive.google.com/...",
  "sources_checked": ["x.com (signed in)", "tiktok.com", "theinterline.com", "..."],
  "items": [
    {
      "id": "YYYY-MM-DD-<slug>",
      "rank": 1,
      "category": "Fashion tech & AI",
      "headline": "string",
      "summary": "2-4 sentences, paraphrased",
      "why_it_matters": "one line on the angle for On-Model / PiktID, or null",
      "influence_score": 8,
      "engagement": { "views": 0, "likes": 0, "reposts": 0, "comments": 0 },
      "entities": { "brands": [], "people": [], "companies": [], "events": [] },
      "source_urls": ["https://..."],
      "image": null,
      "published_at": "ISO 8601 or YYYY-MM-DD",
      "verified": true,
      "is_update": false
    }
  ]
}
```

When an item has an image, `image` is:

```json
{
  "preview_path": "images/YYYY/MM-DD/<slug>.jpg",
  "drive_url": "https://drive.google.com/file/d/...",
  "drive_file_id": "string",
  "original_url": "https://...",
  "width": 0,
  "height": 0,
  "bytes": 0
}
```

Engagement fields hold only numbers actually seen on the source; missing ones are left out.
