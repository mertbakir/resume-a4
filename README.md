# Resume-A4

A modern, responsive, print-friendly Hugo theme for creating professional A4-sized resumes.  
Write your resume content in YAML, track changes with git, and generate a clean site you can deploy (e.g., GitHub Pages), print, or export as PDF.

## ✨ Features

- A4-sized resume pages ready for print, PDF, and static site deployment.
- Define your resume in YAML to easily manage content and track changes with git.
- Improved documentation and example site.
- Customizations options:
  - Freely customize section content, titles, order and placement.
  - Choose from multiple widgets and styles for user-defined sections.
  - Built-in citation formats for academic work.
  - Enable/disable two-column layout and page headers.
  - Add as many pages as you like, remember though you should keep it simple.
  - Explore many more options in `config.yaml`.

## 🚀 Quick Start

### Installation

```bash
# Create a Hugo site
hugo new site my-resume && cd my-resume

# Delete default hugo.toml
rm hugo.toml

# Add the theme (choose one)
git clone https://github.com/mertbakir/resume-a4.git themes/resume-a4
# OR as submodule
git submodule add https://github.com/mertbakir/resume-a4.git themes/resume-a4

# Copy example config and data
cp themes/resume-a4/exampleSite/config.yaml .
cp -r themes/resume-a4/exampleSite/data .

# Start server for preview
hugo server
```

### Usage

1. Edit `config.yaml` to configure sections and layout. 
2. Update YAML files in the `data/` folder with your resume content.
3. Optional: Copy `themes/resume-a4/exampleSite/assets/` for CSS customization.

## 🧱Details

The theme builds the **main column**, **side column**, **header**, and **additional pages** from *features* (sections).
- For historical reasons we used the term feature instead of section; in this document I use the two words interchangeably.
- Each page defines a list of `features`, and optionally a `header` and a `side` column for a two-column layout.
- The two-column layout is **optional**; you can disable the side column.
- The render order of features is the order listed in `config.yaml`.

**Core Features**: `about, experience, education, languages, publications`.  
**User Defined Features**: Other sections you define, e.g. `skills`, `certificates`, `projects`.

### Common Configuration Keys

- **`feature`**: Name of the feature.   
- **`title`**: String rendered as the header of the element.   
  Useful when you want to create resume in another language. Example: 'Experience' can be overwritten with 'Deneyim'.  
  Title can be disabled by using an empty string if you want to save space.
- **`collection`**: The base name of the YAML file containing the data. Defaults to 'features' when not specified.
- **`widget`**: Defines how section content will be rendered for user-defined-features. Core features have their own template/layout. One of: `details-list` (default), `word-list`.
- **`style`**: Rendering style for `word-list` widget. One of: `list`, `compact`, or `title-list`.


### Widget Types

#### 1. details-list

**Data Structure:** Expects data in this format (in YAML file):
```yaml
- title: "Senior Developer"           # The title string
  subtitle: "Tech Company Inc."       # String rendered under title (company, institution, etc.)
  date: "2020 - Present"              # Date string (when certificate was given, employment period, etc.)
  details: |                          # Text in markdown format
    - Led development of microservices architecture
    - Mentored junior developers  
    - Improved system performance by 40%
  link: "https://company.com"         # URL where the title will link to (optional)
  links:                              # List of links rendered as bullet list below details
    - prefix: "Company"               # String before the link
      title: "Website"                # String inside the link
      url: "https://company.com"      # Destination of the link
      icon: "fas fa-cloud"            # Icon string (Font Awesome) rendered after title
```

#### 2. word-list

Handy widget for skills, interests, languages, and other list-based content.

**Configuration:**
```yaml
- feature: skills
  title: Technical Skills
  widget: word-list
  style: compact  # Required: list, compact, or title-list
```

**Style Options:**
- **`list`**: Simple bulleted list
- **`compact`**: Comma-separated inline format  
- **`title-list`**: Grouped lists with titles

**Data Structure:** Expects data in this format (in YAML file):

**For `list` or `compact` styles:**
```yaml
skills:
  - "JavaScript"
  - "Python" 
  - "React"
  - "Node.js"
```

**For `title-list` style:**
```yaml
skill_groups:
  - groupName: "Frontend"      # Title of the group
    list:                      # List of strings rendered under the group
      - "React"
      - "Vue.js"
  - groupName: "Backend"
    list:
      - "Node.js"
      - "Python"
```

### Custom CSS

Copy the `assets/` folder from `exampleSite/` to your site root to customize styles:

```
your-site/
├── assets/
│   └── css/
│       └── custom.scss
├── config.yaml
└── data/
```

To show URLs when printing, add to your custom CSS:

```scss
@media print {
  a[href]:after {
    content: " (" attr(href) ")";
    font-size: 0.8em;
    color: #666;
  }
}
```

## ⁉️FAQ

- **How do I create a single-page resume?**  
Remove the second page from your `config.yaml` - just keep one page with `header: true`.

- **How do I add a profile picture?**  
Set `header.avatar: "your-photo.jpg"` in config and place the image in your `/static` folder.

- **Can I put contact info in the sidebar?**  
Yes, set `header.contactOnSide: true` (only works when `avatar: false`).

- **How do I change section order?**  
Rearrange the features list in your `pages` configuration - sections render in the order listed.

- **How do I hide sections I don't need?**  
Simply remove any feature you don't want from the `pages` configuration, in `config.yaml`.

- **How do I add custom sections?**  
Create a new YAML file in `/data` and reference it in your config with the same name, or just add a new section in `features.yaml`.  
Review the expected data structure in [Widget Types](#widget-types) above.

- **Can I use markdown in descriptions?**  
Yes, the `details` field in most widgets supports full markdown formatting.

- **How do I add external links?**  
Use the `links` array in your data files with `url` and `text` properties.

- **How do I customize colors and fonts?**  
Copy the `/assets` folder from `exampleSite` to your site root and modify the SCSS files.

- **Can I show URLs when printing?**  
Yes, uncomment `print_urls.scss` in your config's CSS section.

- **The theme isn't loading - what's wrong?**  
Check that `theme: "resume-a4"` is set in your config and the theme is in `/themes/resume-a4`.

- **How do I update to the latest version?**  
Run `git pull` in your theme directory, then delete your `/resources` folder and run `hugo server`.

- **My hugo project doesn't seem to recognize the theme.**  
Make sure the theme is in `themes/resume-a4` directory and in your config file theme is set correctly. `theme: resume-a4`.  
And make sure you have only one config file. Hugo generates `hugo.toml` by default when you call `hugo new site`.


- **There is a bug.**  
I would be happy if you submit a pull request with a fix.

---

- See the [Example Site](./exampleSite/) for working setups.  
- Open an [Issue](https://github.com/mertbakir/resume-a4/issues) for support.
