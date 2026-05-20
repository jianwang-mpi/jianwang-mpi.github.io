---
name: jianwang-homepage-updater
description: Update Jian Wang's static academic homepage when there are new papers, profile changes, links, metrics, or project updates. Use for maintaining index.html, stylesheet.css, README.md, image thumbnails, and the compact site structure.
---

# Jian Wang Homepage Updater

## Scope

Maintain this repository as a compact static personal homepage for Jian Wang. Keep publication thumbnails in `image/` as `*_teaser.jpg`. Do not add local subdirectories for papers, project pages, PDFs, or generated project assets. Use authoritative external links for papers, project pages, code, videos, and profile pages.

## Files

- `index.html`: biography, profile links, news, publications with teaser thumbnails, education, and footer.
- `stylesheet.css`: site styling adapted from the Jon Barron template.
- `README.md`: short repository note.
- `SKILL.md`: this update workflow.
- `image/*_teaser.jpg`: publication thumbnails extracted from each paper's first teaser/figure or from the authoritative project page.

## Update Workflow

1. Gather facts from authoritative sources before editing:
   - Current homepage or user-provided biography text.
   - LinkedIn: `https://www.linkedin.com/in/jian-wang-05a4438a/` when publicly accessible.
   - Existing project pages, PDFs, code repositories, and videos linked from the old homepage.
2. For profile updates, revise the title, meta description, intro paragraphs, profile links, and education only where the source confirms the change.
3. For a new publication:
   - Add it to `Selected Publications` if it is recent, first-author, high-impact, or user-requested.
   - Otherwise add it to `Other Publications`.
   - Sort publications reverse-chronologically.
   - Use the project page as the title link; fall back to arXiv, OpenAccess, or the publication page.
   - Add PDF, Project, Code, Video, ArXiv, and Supp. Mat. links only when the URL is known and authoritative. Search for a project page before falling back to a publication page or Scholar.
   - Keep author formatting consistent and mark Jian Wang as `<strong>Jian Wang</strong>`.
   - Add a teaser thumbnail under `image/`. Prefer the paper's first teaser/figure from the arXiv/source package; otherwise use the authoritative project-page teaser/overview image. Name it `shortname_teaser.jpg`.
4. For news updates, add concise dated items and remove stale entries if the list grows too long.
5. For assets, use `image/` for local images only. Do not create other asset subdirectories.
6. Do not recreate template subdirectories such as `data/`, `images/`, `mipnerf/`, `mipnerf360/`, `zipnerf/`, `publication/`, or `projects/`.

## Publication Row Pattern

```html
<tr class="publication">
  <td class="pub-image">
    <a href="PROJECT_URL"><img src="image/SHORTNAME_teaser.jpg" alt="TITLE teaser" loading="lazy"></a>
  </td>
  <td>
    <a href="PROJECT_URL"><span class="papertitle">TITLE</span></a>
    <br>
    AUTHORS WITH <strong>Jian Wang</strong>
    <br>
    <em>VENUE_ABBR YEAR</em>
    <br>
    VENUE FULL NAME.
    <br>
    <a href="PDF_URL">PDF</a> /
    <a href="PROJECT_URL">Project</a> /
    <a href="CODE_URL">Code</a>
  </td>
</tr>
```

## Validation

After edits:

1. Run `find . -maxdepth 2 -type d -not -path './.git*' -print` and confirm the only non-git subdirectory is `./image`.
2. Run `grep -R "images/\\|data/\\|publication/\\|projects/" -n index.html stylesheet.css README.md SKILL.md` and confirm matches are intentional external URLs or forbidden-directory notes in this skill.
3. Run `python3 -m http.server` and verify the profile image, each publication thumbnail, links, publication layout, and mobile wrapping in a browser.
4. Run `git diff --stat` and review the full diff before reporting completion.
