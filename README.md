# Personal website (Quarto)

## What's in this folder

| File | What it is |
|---|---|
| `shawn-website.Rproj` | Double-click to open the project in RStudio |
| `_quarto.yml` | Site settings: title, navigation bar, footer, theme |
| `index.qmd` | Home / About page (photo, bio, links, education, news) |
| `research.qmd` | Research themes and current projects |
| `publications.qmd` | Publications page (reads from `publications.yml`) |
| `publications.yml` | **Your paper list** — add one block per paper |
| `images/profile.jpg` | Placeholder photo — replace with your own (square works best) |
| `images/favicon.png` | Browser-tab icon |
| `theme-light.scss`, `theme-dark.scss`, `styles.css`, `publications.ejs` | Design files — no need to touch |

## 1. Preview the site on your Mac

1. Double-click `shawn-website.Rproj` to open it in RStudio (Quarto is bundled with RStudio).
2. In the **Build** pane, click **Render Website**, or in the **Terminal** tab run:
   ```
   quarto preview
   ```
   The site opens in your browser and refreshes every time you save a file.

## 2. Fill in your details

Search the project for `[Surname]`, `USERNAME`, `you@imperial.ac.uk` and `[University]` and replace them (RStudio: Edit → Find in Files).

- **Bio, links, news:** `index.qmd`
- **Papers:** `publications.yml`. Also set `me:` in `publications.qmd` to your name exactly as it appears in author lists, so it's shown in bold.
- **Photo:** replace `images/profile.jpg` with your own photo, keeping the same filename.

## 3. Publish free on GitHub Pages (first time, ~15 minutes)

You need a GitHub account and Git. On a Mac, running `git --version` in the Terminal will offer to install Git if it's missing.

1. **Create the repository.** On github.com, create a new **public** repository named `USERNAME.github.io` (replace USERNAME with your GitHub username). Don't add a README.
2. **Push the project.** In RStudio's **Terminal** tab, run:
   ```
   git init
   git add .
   git commit -m "First version of website"
   git branch -M main
   git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
   git push -u origin main
   ```
   If Git asks for a password, GitHub needs a personal access token instead. The easiest fix is to install GitHub Desktop and sign in once, which stores your credentials.
3. **Publish.**
   ```
   quarto publish gh-pages
   ```
   Answer `Y` when asked. Quarto renders the site and pushes it to a `gh-pages` branch.
4. **Switch Pages on.** On GitHub, go to the repository's **Settings → Pages**. Under "Build and deployment", choose **Deploy from a branch**, then **gh-pages** and **/ (root)**, and save.

After a minute or two, your site is live at `https://USERNAME.github.io`. Update `site-url` in `_quarto.yml` to match.

## 4. Updating the site later

Edit the files, check with `quarto preview`, then run:
```
quarto publish gh-pages
```
To keep your source files backed up as well:
```
git add . && git commit -m "Update" && git push
```

## 5. Optional: your own domain (e.g. shawnsurname.com)

1. Buy the domain from any registrar (roughly £10 a year).
2. On GitHub, go to **Settings → Pages → Custom domain**, enter it, and follow GitHub's instructions for the DNS records at your registrar.
3. Create a file called `CNAME` in this folder containing just the domain, e.g. `shawnsurname.com`. Then add it to `_quarto.yml` so it survives each publish:
   ```yaml
   project:
     type: website
     resources:
       - CNAME
   ```
4. Run `quarto publish gh-pages` again.
