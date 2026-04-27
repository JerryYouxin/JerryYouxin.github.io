# Xin You - Personal Academic Homepage

A **Jekyll**-based academic homepage hosted on **GitHub Pages**.

Live site: https://jerryyouxin.github.io

---

## Directory Structure

```
个人主页/
├── _config.yml              # Site-wide configuration (name, email, social links, etc.)
├── _data/
│   ├── publications.yml     # Publication list (add new papers here)
│   └── projects.yml         # Project list (add new projects here)
├── index.md                 # Home page (bio)
├── publications.md          # Publications page
├── projects.md              # Projects page
├── _layouts/default.html    # Page layout (usually no need to edit)
├── _includes/navigation.html# Navigation bar (usually no need to edit)
├── assets/
│   ├── css/main.scss        # Stylesheet
│   ├── images/              # Avatar, project cover images
│   └── files/               # Paper PDFs, etc.
├── Gemfile                  # Ruby dependencies
└── README.md                # This file
```

---

## Quick Start (First Deployment)

### Step 1: Create a GitHub Repository

1. Log into GitHub, click **+** (top right) → **New repository**
2. Repository name must be **`JerryYouxin.github.io`** (exact match of your username)
3. Set to **Public**, no need to initialize README
4. Create

### Step 2: Push Code to GitHub

In this folder, open a terminal (PowerShell / Git Bash):

```bash
git init
git add .
git commit -m "Initial commit: academic homepage"
git branch -M main
git remote add origin https://github.com/JerryYouxin/JerryYouxin.github.io.git
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Open the repo → **Settings** → **Pages** in the left sidebar
2. **Source**: select **Deploy from a branch**, Branch = **main** / **root**
3. Save. In ~1-2 minutes, visit `https://jerryyouxin.github.io` to see the site.

GitHub Pages builds Jekyll automatically — no Actions configuration needed.

---

## Regular Maintenance

### 1. Edit Personal Info

Edit `_config.yml`:

```yaml
author:
  name: "Xin You"
  title: "Lecturer"
  affiliation: "School of Computer Science and Engineering, Beihang University"
  email: "your@email.com"
  github: "JerryYouxin"
  google_scholar: "https://scholar.google.com/citations?user=..."
  orcid: "0000-0000-0000-0000"
  dblp: "https://dblp.org/pid/xxx/xxx"
```

### 2. Edit Bio Text

Edit `index.md` (replace placeholders like `[your research area]` with your own text).

### 3. Add / Update Publications

Edit `_data/publications.yml`, append at the end:

```yaml
- title: "Your New Paper Title"
  authors: "A. Collaborator, me, B. Advisor"  # "me" is auto-bolded to your name
  venue: "ACM International Conference on Supercomputing (ICS)"
  venue_short: "ICS"
  year: 2026
  type: conference                    # conference / journal / preprint / workshop
  ccf: "A"                            # CCF rank: A / B / C, leave "" to hide
  core: ""                            # CORE rank (optional)
  pdf: "/assets/files/papers/2026-xyz.pdf"
  code: "https://github.com/JerryYouxin/xyz"
  project: ""
  bibtex: ""
  highlight: true                     # true = feature on homepage as representative work
  note: "Oral Presentation"           # note (optional), e.g. Best Paper / Oral / Co-first author
```

After saving and pushing, the homepage and publications page will auto-update, grouped by year.

**CCF Badge Colors:**

- `ccf: "A"` — red badge, CCF-A
- `ccf: "B"` — orange badge, CCF-B
- `ccf: "C"` — green badge, CCF-C
- For venues not in the CCF recommendation list (e.g. arXiv, some workshops), leave `ccf` empty
- CCF ranking reference: https://www.ccf.org.cn/

### 4. Add / Update Projects

Edit `_data/projects.yml`:

```yaml
- name: "My New Project"
  description: "One-line English description."
  image: "/assets/images/projects/newproj.png"
  tags: ["Python", "NLP"]
  url: "https://github.com/JerryYouxin/newproj"
  demo: "https://newproj.demo/"
  paper: ""
```

Put project cover images in `assets/images/projects/`.

### 5. Update News

Add `<li>` entries to the News section of `index.md` directly:

```html
<li><span class="date">2026-05</span><span>Short description...</span></li>
```

### 6. Upload Avatar

Place `assets/images/avatar.jpg` (400×400 square recommended).
Without it, the page falls back to a default Gravatar placeholder.

---

## How to Publish Changes

After editing local files:

```bash
git add .
git commit -m "Update publications"
git push
```

About 1 minute after pushing, the site auto-updates.

---

## Local Preview (Optional)

To preview locally before publishing, you need **Ruby >= 2.7** and **Bundler**:

```bash
bundle install
bundle exec jekyll serve
# Open http://localhost:4000
```

You can skip local preview — GitHub Pages builds automatically on push.

---

## Style Customization (Advanced)

To change colors/fonts, edit the CSS variables at the top of `assets/css/main.scss`:

```scss
:root {
  --color-accent: #2980b9;       /* primary color (links, buttons) */
  --color-text: #2c3e50;         /* body text color */
  --max-width: 860px;            /* max page width */
}
```

---

## Custom Domain (Optional)

To use your own domain (e.g. `xinyou.com`):

1. Create a `CNAME` file at the repo root, write your domain in it
2. Add a CNAME record at your DNS provider pointing to `jerryyouxin.github.io`
3. In the GitHub repo Settings → Pages → Custom domain, fill in the domain and enable Enforce HTTPS

---

## FAQ

**Q: The site did not update after pushing?**
A: Check the repo's Actions tab for build status, or wait ~2 minutes. Sometimes the browser caches — try an incognito window.

**Q: How are homepage representative works selected?**
A: In `_data/publications.yml`, set `highlight: true` on the paper. If no entries have `highlight: true`, the first 3 are shown automatically.

**Q: How do I add a new section (e.g. Teaching)?**
A: Copy `projects.md` as `teaching.md`, update `permalink` and content; then add a link in `_includes/navigation.html`.

---

## Credits

Design inspired by [academicpages](https://academicpages.github.io/) and [al-folio](https://github.com/alshedivat/al-folio), built on [Jekyll](https://jekyllrb.com/).
