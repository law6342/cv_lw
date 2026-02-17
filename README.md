# Lauren Wilson - Personal Website

[![Deploy Quarto](https://github.com/law6342/cv_lw/actions/workflows/publish.yml/badge.svg)](https://github.com/law6342/cv_lw/actions/workflows/publish.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A professional personal website built with [Quarto](https://quarto.org/), featuring an academic CV and a blog for sharing research insights and technical writing.

🌐 **Live Site:** [https://law6342.github.io/cv_lw/](https://law6342.github.io/cv_lw/)

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Local Development](#local-development)
  - [Creating Blog Posts](#creating-blog-posts)
  - [Updating Your CV](#updating-your-cv)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Deployment](#deployment)
- [Customization](#customization)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Professional CV Homepage**: Front page displays a comprehensive academic and professional CV
- **Integrated Blog**: Blog section with automatic post listing and RSS feed support
- **Responsive Design**: Mobile-friendly layout using the Cosmo theme
- **Automatic Deployment**: GitHub Actions workflow for seamless deployment to GitHub Pages
- **Easy Content Management**: Write content in Markdown with Quarto's extended features
- **Category Support**: Organize blog posts with tags and categories
- **SEO-Friendly**: Proper meta tags and semantic HTML structure

## Prerequisites

To work with this project locally, you'll need:

- [Quarto](https://quarto.org/docs/get-started/) (version 1.3 or higher)
- A text editor (VS Code, RStudio, or any markdown editor)
- Git for version control
- (Optional) [GitHub CLI](https://cli.github.com/) for easier repository management

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/law6342/cv_lw.git
cd cv_lw
```

### 2. Install Quarto

Download and install Quarto from the [official website](https://quarto.org/docs/get-started/):

**macOS:**
```bash
brew install quarto
```

**Windows:**
Download the installer from [quarto.org](https://quarto.org/docs/get-started/)

**Linux:**
```bash
# Download and install the latest release
wget https://github.com/quarto-dev/quarto-cli/releases/download/v1.4.551/quarto-1.4.551-linux-amd64.deb
sudo dpkg -i quarto-1.4.551-linux-amd64.deb
```

### 3. Verify Installation

```bash
quarto check
```

## Usage

### Local Development

#### Preview the Site

Start a local development server with live reload:

```bash
quarto preview
```

This will open your browser to `http://localhost:4200` and automatically refresh when you make changes.

#### Render the Site

Build the static site files:

```bash
quarto render
```

The rendered site will be in the `_site/` directory.

### Creating Blog Posts

#### Method 1: Manual Creation

1. Create a new directory under `posts/`:
   ```bash
   mkdir -p posts/my-new-post
   ```

2. Create an `index.qmd` file in that directory:
   ```bash
   touch posts/my-new-post/index.qmd
   ```

3. Add front matter and content:
   ```yaml
   ---
   title: "My New Post Title"
   author: "Lauren Wilson"
   date: "2026-02-17"
   categories: [research, microbiology, tutorial]
   description: "A brief description of the post"
   ---

   ## Introduction

   Your content here...
   ```

#### Method 2: Using Quarto CLI

```bash
quarto create post posts/my-new-post
```

#### Adding Images

Place images in the post directory and reference them:

```markdown
![Image caption](image.png)
```

#### Code Blocks

Quarto supports syntax highlighting for many languages:

````markdown
```python
def hello_world():
    print("Hello, World!")
```
````

### Updating Your CV

Edit the `index.qmd` file to update your CV. The structure follows standard markdown with YAML front matter:

```yaml
---
title: "Lauren Wilson"
subtitle: "Graduate Student in Microbiology | Penn State"
page-layout: full
toc: false
---
```

## Project Structure

```
cv_lw/
├── .github/
│   └── workflows/
│       └── publish.yml       # GitHub Actions workflow
├── posts/                    # Blog posts directory
│   └── creating-this-website/
│       └── index.qmd         # Example blog post
├── _quarto.yml               # Main Quarto configuration
├── index.qmd                 # CV homepage
├── blog.qmd                  # Blog listing page
├── styles.css                # Custom CSS styles
├── .gitignore                # Git ignore file
└── README.md                 # This file
```

## Configuration

### Site-Wide Settings (_quarto.yml)

The main configuration file controls the entire site:

```yaml
project:
  type: website
  output-dir: _site

website:
  title: "Lauren Wilson"
  navbar:
    left:
      - text: "Home"
        href: index.qmd
      - text: "Blog"
        href: blog.qmd
  page-footer:
    center: "Copyright 2026, Lauren Wilson"

format:
  html:
    theme: cosmo
    css: styles.css
    toc: false
```

### Customization Options

- **Theme**: Change `theme: cosmo` to any [Bootswatch theme](https://quarto.org/docs/output-formats/html-themes.html)
- **Navigation**: Add more pages in the `navbar` section
- **Footer**: Customize the `page-footer` content
- **CSS**: Modify `styles.css` for custom styling

### Blog Configuration (blog.qmd)

Control how blog posts are displayed:

```yaml
---
title: "Blog"
listing:
  contents: posts
  sort: "date desc"
  type: default      # Options: default, grid, table
  categories: true
  feed: true
---
```

## Deployment

### Automatic Deployment (GitHub Actions)

The site automatically deploys to GitHub Pages when you push to the `main` branch.

#### Workflow File (.github/workflows/publish.yml)

The workflow:
1. Checks out the repository
2. Sets up Quarto
3. Renders the site
4. Deploys to GitHub Pages

#### Manual Deployment Trigger

You can also trigger deployment manually:

```bash
gh workflow run publish.yml
```

Or from the GitHub web interface: Actions → Publish Quarto Website → Run workflow

### GitHub Pages Settings

Ensure GitHub Pages is configured correctly:

1. Go to **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. The site will be available at `https://law6342.github.io/cv_lw/`

### Custom Domain (Optional)

To use a custom domain:

1. Add a `CNAME` file with your domain:
   ```bash
   echo "yourdomain.com" > CNAME
   ```

2. Configure DNS settings with your domain provider
3. Enable HTTPS in GitHub Pages settings

## Customization

### Changing the Theme

Edit `_quarto.yml`:

```yaml
format:
  html:
    theme: flatly  # Try: cosmo, flatly, darkly, journal, etc.
```

### Adding New Pages

1. Create a new `.qmd` file (e.g., `publications.qmd`)
2. Add it to the navbar in `_quarto.yml`:

```yaml
navbar:
  left:
    - text: "Publications"
      href: publications.qmd
```

### Custom CSS

Add your styles to `styles.css`:

```css
/* Custom color scheme */
:root {
  --primary-color: #2c3e50;
  --secondary-color: #3498db;
}

h1, h2, h3 {
  color: var(--primary-color);
}
```

### Adding Analytics

Add Google Analytics or other tracking to `_quarto.yml`:

```yaml
website:
  google-analytics: "G-XXXXXXXXXX"
```

### Social Media Links

Add social icons to the navbar:

```yaml
navbar:
  right:
    - icon: github
      href: https://github.com/law6342
    - icon: twitter
      href: https://twitter.com/yourusername
    - icon: linkedin
      href: https://linkedin.com/in/yourprofile
```

## Troubleshooting

### Site Not Updating After Push

1. Check the Actions tab for workflow errors
2. Ensure GitHub Pages source is set to "GitHub Actions"
3. Wait 1-2 minutes for DNS propagation
4. Clear your browser cache

### Quarto Preview Not Working

```bash
# Check Quarto installation
quarto check

# Try rendering first
quarto render

# Then preview
quarto preview
```

### Build Errors

Check for:
- YAML syntax errors in front matter
- Missing closing quotes or brackets
- Invalid date formats (use YYYY-MM-DD)
- Broken image links

### Local vs Production Differences

If the site looks different locally vs on GitHub Pages:
- Ensure you're using the same Quarto version
- Check for absolute vs relative paths
- Verify all assets are committed to Git

## Contributing

This is a personal website, but if you find bugs or have suggestions:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -m 'Add some improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see below for details:

```
MIT License

Copyright (c) 2026 Lauren Wilson

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Contact

**Lauren Wilson**
- Email: law6342@psu.edu
- Location: State College, PA
- Institution: Penn State University
- GitHub: [@law6342](https://github.com/law6342)

## Acknowledgments

- Built with [Quarto](https://quarto.org/) by Posit
- Hosted on [GitHub Pages](https://pages.github.com/)
- Theme based on [Bootswatch Cosmo](https://bootswatch.com/cosmo/)
- Inspired by the academic community's need for simple, effective personal websites

---

**Note**: This website showcases my academic work, research experience, and professional journey. Feel free to use this repository as a template for your own personal website!
