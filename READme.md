# Serene Bay

A static nature website. No build tools, no CMS, no dependencies. Just upload and go.

## Quick Deploy on GitHub Pages

1. Create a new GitHub repository
2. Upload **everything inside this folder** to the repo root
3. Go to **Settings → Pages**
4. Under **Source**, select **Deploy from a branch**
5. Choose **main** branch and **/ (root)** folder
6. Click **Save** — your site goes live in ~1 minute at `https://yourusername.github.io/your-repo-name/`

> ⚠️ **Important:** Also go to **Settings → Actions → General** and make sure **"Allow all actions and reusable workflows"** is enabled. This lets the manifest auto-generator run.

## How Content Works

Each post is its own markdown file. When you add a new `.md` file to a content folder, a GitHub Action automatically updates the manifest, and the new post appears on the website — no manual indexing needed.

### Adding a New Post

1. Create a new `.md` file in the appropriate folder (see structure below)
2. Use the same frontmatter format as existing posts in that folder
3. Commit and push to GitHub
4. The GitHub Action runs, regenerates `content/manifest.json`, and commits it
5. Your new post now appears on the website automatically

### Ordering Posts

Files are sorted alphabetically by filename. Use number prefixes to control order:
- `01-forest-ecosystems.md` → shows first
- `02-ocean-biomes.md` → shows second
- etc.

## Folder Structure

```
serene-bay/
├── index.html                  → Home page
├── gallery.html                → Gallery page
├── flower-blog.html            → Flower Blog page
├── nature-literacy.html        → Nature Literacy page
├── about.html                  → About page
├── style.css                   → All styling
├── content-loader.js           → Fetches & renders markdown
├── .nojekyll                   → Tells GitHub Pages to skip Jekyll
├── README.md                   → This file
├── .github/
│   └── workflows/
│       └── generate-manifest.yml  → Auto-discovers new posts
└── content/
    ├── manifest.json              → Auto-generated list of all posts
    ├── site/
    │   └── settings.md            → Site title, tagline, footer quote
    ├── home.md                    → Home page features & CTA
    ├── about.md                   → About page content
    ├── gallery/                   → Gallery posts (one .md per photo)
    │   ├── 01-ancient-redwood-mist.md
    │   ├── 02-turquoise-horizon.md
    │   └── ...
    ├── flowers/                   → Flower articles (one .md per flower)
    │   ├── cherry-blossom.md
    │   ├── lotus.md
    │   └── bird-of-paradise.md
    └── literacy/                  → Ecology topics (one .md per topic)
        ├── 01-forest-ecosystems.md
        ├── 02-ocean-biomes.md
        └── ...
```

## Post Formats

### Gallery Post (`content/gallery/your-post.md`)
```markdown
---
title: Your Photo Title
category: Forests
location: Your Location, Country
image: https://images.unsplash.com/your-photo-url
---

Your description here.
```

### Flower Post (`content/flowers/your-flower.md`)
```markdown
---
name: Flower Name
latin: Latin Name
origin: Region
bloom_season: Months
color: "#HEXCOLOR"
image: https://images.unsplash.com/your-photo-url
read_time: X min read
intro: A short introduction paragraph.
---

## History & Heritage

Your history content here...

## Cultural Significance

Your significance content here...

## Field Facts

- Fact one
- Fact two
- Fact three
```

### Literacy Post (`content/literacy/your-topic.md`)
```markdown
---
title: Topic Title
subtitle: A short subtitle
icon: 🌲
color: "#52B788"
---

## Section Heading

Your content here...

## Field Facts

- Fact one
- Fact two
- Fact three
```

### Site Settings (`content/site/settings.md`)
```markdown
---
site_title: Serene Bay
tagline: Where Nature Speaks
hero_subtitle: Your hero subtitle
footer_quote: Your footer quote
footer_quote_author: Author Name
---
```
Add a New Post to a Navbar Page
Each navbar page has its own content folder. To add a new post, just create a new .md file in the matching folder:

Navbar Page	Folder	File format
Gallery	content/gallery/	title, category, location, image + description
Flower Blog	content/flowers/	name, latin, origin, bloom_season, color, image, read_time, intro + markdown body
Nature Literacy	content/literacy/	title, subtitle, icon, color + markdown body
Example — adding a new gallery photo:

Create a file: content/gallery/13-my-new-photo.md
Copy the format from any existing file in that folder (e.g. 01-ancient-redwood-mist.md)
Fill in your title, category, location, image URL, and description
Commit & push
That's it. The GitHub Action auto-updates the manifest, and your new post appears on the Gallery page automatically. No other files need editing.

Ordering: Files are sorted alphabetically, so use number prefixes (01-, 02-, 13-) to control the display order.

Important: Make sure GitHub Actions are enabled — go to Settings → Actions → General → Allow all actions and reusable workflows.