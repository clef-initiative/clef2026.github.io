# CLEF 2026 Content Editor's Guide

## Getting Started

The CLEF website is built using [Hugo](http://gohugo.io), a static site generator that uses Markdown files to render the website. 
Each individual page on the website corresponds to a `.md` file that contains:

- **Frontmatter**: Configuration parameters that determine how a page is rendered at the top of the file (between `---` lines)
- **Content**: The actual page content written in Markdown, and may feature special elements called "shortcodes" that extend normal Markdown syntax

When editing content, make sure to follow the steps in [README.md](README.md) to set up your local environment and preview your edits, before pushing them to production.

## File Structure 

To construct your CLEF webpage, you need to edit content in three directories:
- [`content/`](content) - all your Markdown files go here
- [`assets`](assets) - content accessed via shortcodes, e.g., images in figures, goes here, organized in subfolders by type (e.g., `assets/img/` );
- [`static/`](static) - all your static content, like hosted files go here, organized in subfolders by type (e.g., `static/files/` ); these can be linked to relative to the `static` directory (e.g., `files/flyer.pdf`)
- [`data/`](data) - YAML data files to generate content from automatically (like previous conferences, or important date listings); refer to the shortcode section below for more information

## Page Types

Hugo distinguishes between two types of pages, which determines how they're displayed and organized:

1. **Single Pages** (any `*.md` file): these contain the individual standalone content pieces of a page. 
   - Each file creates its own page/URL, and files in a directory form a section.
   - For example, `conference/venue.md` will be rendered at `<base_url>/conference/venue.html`
1. **List Pages** (any `_index.md` file): these use the special filename `_index.md` and organize a sections' content.
   - After its own markdown content, it automatically renders a list of links to all child pages of its section
   - Each child entry features the childs title and summary (more on this later)

Generally, the existing content structure is sufficient to organize all information important to hosting a CLEF conference. 

## Site Configuration

How pages are rendered is configured through yaml files. These parameters can be defined in two places: the global `config.yaml` file, or in each individual markdown files' `frontmatter`.

### Global  Configuration Fields

The first lines of [config.yaml](config.yaml) look like something this (taken from the configuration for 2026 CLEF):
```yaml
baseURL: "https://clef2026.clef-initiative.eu/"
title: "CLEF 2026 - Conference and Labs of the Evaluation Forum"
params:
  logo: "img/clef2026-logo.svg"
  hero_image: "img/header.jpg"
  name: "CLEF 2026"
  dates: "September 21-24, 2026"
  location: "Jena, Germany"
  year: 2026
  email: "clef2026@clef-initiative.eu"
  color: "indigo"
  gray: "stone"
```

Adapt these parameters to your own conference. The parameters have the following meanings and can take the following values:

| Field        | Description                                 | Value                                                                                           |
|--------------|---------------------------------------------|-------------------------------------------------------------------------------------------------|
| `baseURL`    | The website's main URL                      | An URL like `https://clef2026.clef-initiative.eu/`                                              |
| `title`      | Default site title for SEO and browser tabs | A string, like `CLEF 2026 - Conference and Labs of the Evaluation Forum`                        |
| `logo`       | Site logo image path                        | A path relative to the asset folder, like `img/clef2026-logo.svg`                               |
| `hero_image` | Default hero/banner image for pages         | A path relative to the asset folder, like `img/clef2026-header.jpg`                             |
| `name`       | Short conference name                       | A string, `CLEF 2026`                                                                           |
| `dates`      | Conference dates                            | A string, like `September 21-24, 2026`                                                          |
| `location`   | Conference location                         | A string, like `Jena, Germany`                                                                  |
| `year`       | Conference year                             | A string, like `2026`                                                                           |
| `email`      | Main contact email                          | An email address, like `clef2026@uni-jena.de`                                                   |
| `color`      | Primary accent color                        | Any  [Tailwind CSS color name](https://tailwindcss.com/docs/colors) or gray tone, like `indigo` |
| `gray`       | Gray color palette                          | Any [Tailwind CSS gray tone](https://tailwindcss.com/docs/colors), like `stone`                 |


**Available Color Options:**
- The `gray` parameter can be set to any of the values `slate`, `gray`, `zinc`, `neutral`, `stone` (recommended)
- The `color` parameter can be set to any of the gray values (recommended to be the same as `gray`), or any of the colors `red`, `orange`, `amber`, `yellow`, `lime`, `green`, `emerald`, `teal`, `cyan`, `sky`, `blue`, `indigo`, `violet`, `purple`, `fuchsia`, `pink`, `rose`
- Custom colors are possible but require changes to the pages CSS configuration; follow [the custom palette guide](https://tailwindcss.com/docs/colors#using-a-custom-palette) and add your desired colors to [the root CSS file](themes/treble/assets/css/main.css). *Important*: you need to define all required shades, and reference the color name in the global config, for example like this for `color: brick`:
  ```
  --color-brick-50: oklch(0.971 0.013 17.38);
  --color-brick-100: oklch(0.936 0.032 17.717);
  --color-brick-200: oklch(0.885 0.062 18.334);
  --color-brick-300: oklch(0.808 0.114 19.571);
  --color-brick-400: oklch(0.704 0.191 22.216);
  --color-brick-500: oklch(0.637 0.237 25.331);
  --color-brick-600: oklch(0.577 0.245 27.325);
  --color-brick-700: oklch(0.505 0.213 27.518);
  --color-brick-800: oklch(0.444 0.177 26.899);
  --color-brick-900: oklch(0.396 0.141 25.723);
  --color-brick-950: oklch(0.258 0.092 26.042);
  ```

### Frontmatter Configuration Fields

Every content file starts with frontmatter - configuration data written in YAML format between two sets of three dashes (`---`). It typically looks like this:

```yaml
---
title: "Page Title"
draft: false
summary: "Brief description of the page content"
weight: 20
toc: true
params:
  author: "John Smith"
  image: "https://example.com/image.jpg"
menu:
  main:
    identifier: "unique-page-id"
    parent: "parent-section"
    weight: 20
---
```

###### General Fields

| Field     | Required | Description                                                                            | Example                                           |
|-----------|----------|----------------------------------------------------------------------------------------|---------------------------------------------------|
| `title`   | ✅        | The page title displayed in navigation and browser tabs                                | Any string, like `"Call for Papers"`              |
| `draft`   | ✅        | Set to `false` to publish, `true` to hide in final website build                       | `true`/`false`                                    |
| `summary` | ✅        | Brief description for SEO and previews; this is rendered as description in list pages. | Any string, `"Learn about submission guidelines"` |
| `toc`     | ❌        | Whether to render a table of contents on this page                                     | `true`/`false`                                    |
| `weight`  | ❌        | Controls ordering in list pages (per section; lower numbers appear first)              | Any int, like `20`                                |

###### Params Section
Custom parameters for this individual page:

| Param     | Required | Description                                | Example                                               |
|-----------|----------|--------------------------------------------|-------------------------------------------------------|
| `author`  | ❌        | Content author name                        | Any string, like `"Dr. Jane Smith"`                   |
| `image`   | ❌        | Feature image & social media preview image | Path relative to assets folder, like`"img/venue.jpg"` |

###### Menu Configuration
Controls how the page appears in navigation:

| Field        | Required | Description                                                                   | Example                                                                              |
|--------------|----------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| `identifier` | ✅        | Unique ID for this menu item                                                  | Any string, like `"conference-venue"`; needs to be unique site-wide                  |
| `parent`     | ✅        | Top-level menu item                                                           | Any of the top-level menu IDs; these are defined in the [`config.yaml`](config.yaml) |
| `name`       | ❌        | The name under which this item appears in the menu dropdown                   | Any string, like `"About"`; if unspecified, defaults to page title.                  |
| `weight`     | ❌        | Controls ordering in menu dropdowns (per section; lower numbers appear first) | `20`                                                                                 |

The global menu structure, i.e., the top-level entries visible in the menu bar, is defined in the global [`config.yaml`](config.yaml) file. Add custom entries there to expand the menu to new sections by following the existing pattern.

### Common Frontmatter Patterns

**List Page** (`_index.md`):
```yaml
---
title: "Conference"
draft: false
summary: "Information about CLEF 2026 conference"
weight: 10
menu:
  main:
    identifier: "conference-overview"
    parent: "conference"
    name: "Overview"
    weight: 1 # This should be 1 to appear first in the dropdown
---
```

**Single page** (`*.md`):
```yaml
---
title: "Venue"
draft: false
date: 2025-01-01T00:00:00-00:00
summary: "Conference venue information"
weight: 20
menu:
  main:
    identifier: "conference-venue"
    parent: "conference"
    name: "Venue"
    weight: 20 # This should be at least 2 to appear after the list page in the dropdown
---
```


## Markdown Basics

### Headings
```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
```

### Text Formatting
```markdown
**Bold text**
*Italic text*
`Inline code`
~~Strikethrough~~
```

### Lists
```markdown
Unordered list:
- Item 1
- Item 2
  - Sub-item
  - Sub-item

Ordered list:
1. First item
2. Second item
3. Third item
```

### Links 
```markdown
[Link text](https://example.com)
[Internal link](../about/clef-initiative.md)
```

### Tables
```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
```

### Code Blocks
````markdown
```python
def hello_world():
    print("Hello, World!")
```
````

### Blockquotes
```markdown
> This is a blockquote.
> It can span multiple lines.
```

## Available Shortcodes

Shortcodes are special Hugo components that add enhanced functionality to your content. They are written between `{{<` and `>}}` tags.

### 1. Alert Component

Creates styled notification boxes for important information.

**Syntax:**
```markdown
{{< alert type="info" title="Important Note" >}}
Your alert message goes here. You can use **markdown** formatting.
{{< /alert >}}
```

**Parameters:**
- `type`: `primary`, `info`, `warning`, `error`, `success` (default: `primary`)
- `title`: Optional title for the alert

**Examples:**
```markdown
{{< alert type="info" title="Registration Open" >}}
Early bird registration is now available until March 15, 2026.
{{< /alert >}}

{{< alert type="warning" >}}
The submission deadline has been extended to February 28, 2026.
{{< /alert >}}

{{< alert type="error" title="Important" >}}
Late submissions will not be accepted under any circumstances.
{{< /alert >}}
```

### 2. Button Component

Creates styled buttons and links.

**Syntax:**
```markdown
{{< button href="/registration" type="primary" size="md" >}}
Register Now
{{< /button >}}
```

**Parameters:**
- `href`: URL to link to (required; can be relative to page, relative to root URL, or external)
- `type`: `primary`, `secondary`, `outline`, `ghost`, `destructive`, `link` (default: `primary`)
- `size`: `sm`, `md`, `lg` (default: `md`)
- `class`: Additional [Tailwind](http://tailwindcss.com) CSS classes

**Examples:**
```markdown
{{< button href="openreview.net/..." type="primary" >}}
Submit Paper
{{< /button >}}

{{< button href="/registration/fees" type="secondary" size="lg" >}}
View Pricing
{{< /button >}}

{{< button href="#download" type="outline" size="sm" >}}
Download PDF
{{< /button >}}
```

### 3. Card Component

Creates structured content cards.

**Syntax:**
```markdown
{{< card title="Card Title" footer="Footer text" link="/more-info" >}}
Card content goes here. You can use **markdown** formatting.
{{< /card >}}
```

**Parameters:**
- `title`: Card header title
- `footer`: Optional footer text
- `class`: Additional [Tailwind](http://tailwindcss.com) CSS classes
- `width`: Card width, `sm`/`md`/`lg`/`xl`/`2xl`/`full`

**Examples:**
```markdown
{{< card title="Keynote Speaker" footer="September 10, 2026" >}}
**Dr. Anna Smith**  
*University of Edinburgh*

Leading expert in information retrieval and machine learning applications.
{{< /card >}}

{{< card title="Important Dates" link="/dates" >}}
- **Paper Submission**: February 28, 2026
- **Notification**: May 15, 2026
- **Camera Ready**: June 30, 2026
{{< /card >}}
```

### 4. Dates Component

Displays important dates from data files with status indicators.

**Syntax:**
```markdown
{{< dates key="conference" >}}
```

**Parameters:**
- `key`: References a top-level key in `data/dates.yaml`

**Data File Format** (`data/dates.yaml`):
```yaml
conference:
  timezone: "Central European Time (CET)" # Optional; will be shown at bottom of list
  dates:                                  # Dates appear in order as listed here
    - name: "Paper Submission Deadline"   # Name of the date
      date: "2026-02-28"                  # Date; needs to be formatted YYYY-MM-DD
    - name: "Notification of Acceptance"
      date: "2026-05-15"
    - name: "Camera-Ready Papers Due"
      date: "2026-06-30"
    - name: "Conference Dates"
      date: "2026-09-10"
```

**Examples:**
```markdown
## Important Conference Dates
{{< dates key="conference" >}}
```

### 5. Figure Component

Display images with captions and responsive sizing, and text floating.

**Syntax:**
```markdown
{{< figure src="img/venue.jpg" size="600x400" alt="Conference venue" caption="CLEF 2026 venue in Jena" width="lg" float="center" >}}
```

**Parameters:**
- `src`: Image URL or path (required)
- `size`: If given, automatically resizes the image to the specified dimensions
- `alt`: Alt text for accessibility
- `caption`: Optional image caption
- `width`: `sm`, `md`, `lg`, `xl`, `2xl`, `3xl`, `4xl`, `full` (default: `full`)
- `float`: `left`, `right`, `center` (default: `center`)
- `class`: Additional [Tailwind](http://tailwindcss.com) CSS classes

**Examples:**
```markdown
{{< figure 
    src="img/jena-university.jpg" 
    alt="University of Jena campus" 
    caption="The University of Jena campus where CLEF 2026 will be held"
    width="xl" 
>}}

{{< figure 
    src="img/keynote-speaker.jpg" 
    alt="Dr. Sarah Johnson" 
    caption="**Dr. Sarah Johnson**, Keynote Speaker"
    width="md" 
    float="right" 
>}}
```

### 6. Accordion Component

Creates collapsible accordion sections, for example for FAQs.

**Syntax:**
```markdown
{{< accordion >}}
  {{< accordion-item title="How do I submit a paper?" >}}
  Papers must be submitted through the conference management system by the deadline.
  {{< /accordion-item >}}
  
  {{< accordion-item title="What are the page limits?" >}}
  Long papers: 12 pages. Short papers: 6 pages. All pages include references.
  {{< /accordion-item >}}
{{< /accordion >}}
```

**Parameters:** (per item)
- `title`: Question or section title (required)
- `id`: Optional custom ID, for example to link to (auto-generated if not provided)

**Examples:**
```markdown
## Frequently Asked Questions

{{< accordion >}}
  {{< accordion-item title="When is the registration deadline?" >}}
  Registration remains open until August 15, 2026. However, we recommend early registration for discounted rates.
  {{< /accordion-item >}}
  
  {{< accordion-item title="Is financial support available?" >}}
  Limited travel grants are available for students and participants from developing countries. Apply through the registration system.
  {{< /accordion-item >}}
  
  {{< accordion-item title="What is the conference format?" >}}
  CLEF 2026 will be an in-person conference with some hybrid elements for remote participation.
  {{< /accordion-item >}}
{{< /accordion >}}
```

### 7. Call-to-Action Component

This component inserts a row with three buttons, linking to the call for papers, the lab page, and the conference information.
It is intended to be inserted on the home page markdown as a call to action for site visitors and to aid quick navigation.

**Syntax:**
```markdown
{{< cta >}}
```

## Tips for Content Editors

1. **Preview Your Changes**: Always preview your content by building locally before publishing (see [`README.md`](README.md))
2. **Check Links**: Verify that all internal and external links work
3. **Optimize Images**: Compress images for web use, aim for under 500KB
4. **Use Consistent Formatting**: Follow the established patterns and styles
5. **Test Responsive Design**: Check how your content looks on mobile devices
6. **Keep Data Files Updated**: Remember to update date files and other data sources
7. **Use Version Control**: Keep track of your changes with meaningful commit messages


## Getting Help

- Check existing pages for formatting examples
- Refer to the [Hugo documentation](http://gohugo.io) for advanced features
- Test shortcodes on a draft page before using them in production
