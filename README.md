# CLEF 2026 Web Page

For guidelines on how to edit content, see [README-content.md](README-content.md)!

## Updating Theme

If the [theme](https://github.com/clef-initiative/clef-theme) has changed, you can pull in the updates by:

```bash
git submodule update --remote --merge 
git add -f themes/clef-theme 
git commit -m "Update theme version"
git push
```

## Building the Website Locally

1. [Install Hugo](https://gohugo.io/installation/) and [Install NPM](https://nodejs.org/en/download)
2. Install tailwind
```bash
npm install --save-dev tailwindcss @tailwindcss/cli @tailwindcss/typography
```
3. (Optional) Run in local development mode to verify the page
```bash
hugo server -D --disableFastRender
```

You can view the result in your browser (usually at `localhost:1313`)

4. Built the static pages:
```bash
hugo
```

This will create a `public` directory where the rendered static site is located.

