# Fulbright proposal landing page

Single-page academic presentation of Jan Saro's Fulbright--Masaryk Postdoctoral
proposal: *A Minimum-Viable, Explainable Digital Twin for Dairy Cows*.

## Layout

```
index.html              the page itself
style.css               clean academic styling, no external dependencies
.nojekyll               tells GitHub Pages to skip Jekyll processing
assets/
  photo.jpg             portrait
  proposal-wisconsin.pdf
  proposal-cornell.pdf
  personal-statement.pdf
  cv.pdf
```

## Local preview

```sh
cd web
python3 -m http.server 4000
# open http://localhost:4000
```

## Publish on GitHub Pages

1. Create a new repository on GitHub, e.g. `fulbright-proposal`.
2. From the repo root (not from `web/`):
   ```sh
   git init
   git add web
   git commit -m "Initial proposal site"
   git branch -M main
   git remote add origin git@github.com:<your-user>/fulbright-proposal.git
   git push -u origin main
   ```
3. In the repo on GitHub, go to **Settings &rarr; Pages**:
   - **Source:** *Deploy from a branch*
   - **Branch:** `main` / `/web` (root)
   - Click **Save**.
4. After ~30 seconds the site will be live at
   `https://<your-user>.github.io/fulbright-proposal/`.

### Alternative: publish at the repo root

If you'd rather have the site at the root of the repo, move the contents of `web/`
to the top level and set GitHub Pages **Branch** to `main` / `/ (root)`.

### Custom domain (optional)

Add a `CNAME` file in `web/` containing your domain, e.g. `jansaro.com`, and add the
matching DNS record at your registrar.

## Refreshing the PDFs

The PDFs in `assets/` are static copies of the latest build. When you rebuild the
LaTeX sources, re-copy:

```sh
cp output/project_statement_wisconsin.pdf web/assets/proposal-wisconsin.pdf
cp output/project_statement_cornell.pdf   web/assets/proposal-cornell.pdf
cp output/personal_statement.pdf          web/assets/personal-statement.pdf
cp output/cv.pdf                          web/assets/cv.pdf
```
