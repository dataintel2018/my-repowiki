# RepoWiki ⚡

> An AI-powered GitHub Pages wiki for all your repositories — like DeepWiki, but yours.

**Live demo:** `https://YOUR_USERNAME.github.io/repowiki`

## What it does

- Fetches all repos for any GitHub user via the GitHub API
- Generates AI wiki summaries per repo using Claude (via Anthropic API)
- Displays README, file tree, and repo stats
- Filterable by language, sortable by stars/forks/activity
- Fully static — no backend, deploys to GitHub Pages for free

## Deploy in 3 steps

### 1. Fork or create the repo

```bash
# Option A: clone this repo
git clone https://github.com/YOUR_USERNAME/repowiki
cd repowiki

# Option B: create a new repo and copy index.html into it
```

### 2. Push to GitHub

```bash
git add .
git commit -m "initial repowiki"
git push origin main
```

### 3. Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select: `Deploy from a branch`
3. Branch: `main` / Folder: `/ (root)`
4. Click **Save**

Your site will be live at: `https://YOUR_USERNAME.github.io/repowiki`

## Usage

1. Open the site
2. Enter any GitHub username
3. Optionally add a [Personal Access Token](https://github.com/settings/tokens/new?scopes=repo&description=RepoWiki) (read-only, for private repos + higher rate limits)
4. Click **Generate →**

## Pre-load your own username

Edit `index.html` and find this line:

```html
<input type="text" id="username-input" placeholder="github-username" autocomplete="off" />
```

Change it to:

```html
<input type="text" id="username-input" value="YOUR_GITHUB_USERNAME" autocomplete="off" />
```

Then optionally auto-trigger on load by adding at the bottom of the `<script>` block:

```js
// Auto-load on page open
window.addEventListener('load', () => fetchRepos());
```

## Tech stack

- Pure HTML/CSS/JS — zero dependencies, zero build step
- GitHub REST API v3 (public, no auth needed for public repos)
- Anthropic Claude API (claude-sonnet-4) for AI summaries
- Google Fonts (IBM Plex Sans + Mono)
- Deploys to GitHub Pages (free static hosting)

## Rate limits

| Scenario | Limit |
|---|---|
| No token | 60 requests/hour |
| With token | 5,000 requests/hour |
| AI summaries | Uses Anthropic API (your claude.ai account) |

## License

MIT
