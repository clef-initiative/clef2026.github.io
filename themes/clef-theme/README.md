# CLEF Theme
A Hugo theme for CLEF conference websites.

## Building Locally

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

