# CLEF 2026 Web Page

For guidelines on how to edit content, see [README-content.md](README-content.md)!

## Building the Website Locally

1. [Install Hugo](https://gohugo.io/installation/) and [install NPM](https://nodejs.org/en/download).
2. Update Git submodules:

   ```shell
   git submodule init
   git submodule update
   ```

3. Install NPM dependencies:

   ```shell
   npm install
   ```

4. (Optional) Run in local development mode to verify the page:

   ```shell
   hugo server -D --disableFastRender
   ```

   You can view the result in your browser (usually at [`localhost:1313`](http://localhost:1313/)).

5. Built the static pages:

   ```shell
   hugo
   ```

This will create a `public` directory where the rendered static site is located.

## Updating Theme

If the [theme](https://github.com/clef-initiative/clef-theme) has changed, you can pull in the updates by:

```bash
git submodule update --remote --merge 
git add -f themes/clef-theme 
git commit -m "Update theme version"
git push
```
