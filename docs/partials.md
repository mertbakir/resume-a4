# Partial Templates Reference

This document explains each partial template's purpose and functionality for developers working on the Resume A4 theme.

## Core Layout Partials

### `header.html`
Renders the resume header with name, tagline, and contact links.
- Displays name from `about.name` data, fallback to "Resume"
- Shows tagline if enabled and available
- Renders contact links (conditionally based on avatar/contact settings)
- Handles avatar image display

### `footer.html`
Renders the resume footer with credits and additional links.
- Shows theme credits if enabled
- Displays custom footnote text
- Renders additional contact/social links
- Handles FontAwesome icons for links

### `section.html`
**Router partial** - determines which widget to use for each section.
- Handles section title display
- Routes to appropriate section widget based on `feature` and `widget` config
- Special handling for experience sections (grouped vs non-grouped)
- Fallback to `section-details-list.html` for unknown widgets
- Error handling for missing sections/data

## Widget Partials

### `section-details-list.html`
**Default widget** for structured data (experience, projects, education, etc.).
- Renders items with title, subtitle, date, and details
- Handles both linked and non-linked titles
- Supports FontAwesome link icons
- Renders markdown details and additional links
- Error handling for missing titles and invalid links

### `section-word-list.html`
Widget for lists of skills, interests, technologies, etc.
- **Style "list"**: Simple bullet list
- **Style "compact"**: Grouped items with description lists
- **Style "title-list"**: Groups with headings and sub-lists
- Handles both flat arrays and grouped data structures

### `section-about.html`
Simple widget that renders markdown content from `about.details`.
- Uses `markdown` partial for content rendering

### `section-experience.html`
**Grouped experience** widget for company-based experience layout.
- Groups roles by company
- Shows company name as section header
- Displays role title, date, and details for each position
- Optional tools/technologies display
- Page-based filtering support

### `section-experience-nogroup.html`
**Flat experience** widget for chronological experience layout.
- Each role as separate item
- No company grouping
- Page-based filtering support

### `section-education.html`
Specialized widget for education entries.
- Handles school name, degree, date, location
- Configurable field display (location, details, name priority)
- FontAwesome and external link icon controls
- Supports both linked and non-linked institutions

### `section-publications.html`
Complex widget supporting multiple academic citation styles.
- **IEEE style**: Author list, title, journal, volume, pages, date
- **APA style**: Author (date), title, journal formatting
- **TitleFirst**: Custom format with title-first layout
- **Default**: Basic author, date, title format
- DOI link support
- Author name formatting (first/middle initial + last name)

### `section-languages.html`
Specialized widget for language proficiency display.
- Language name with proficiency level
- Compact formatting optimized for sidebar use

### `section-json.html`
Development/debug widget that outputs raw JSON data.
- Useful for inspecting data structure during development

## Utility Partials

### `markdown.html`
Renders markdown content with proper escaping.
- Converts markdown to HTML
- Used by other partials for content rendering

### `_header_links.html`
Renders contact links with customizable separators.
- Used by header for contact information
- Supports different separators ("|", "<br>", etc.)
- FontAwesome icon support

## Data Flow

1. `home.html` calls `section.html` for each configured feature
2. `section.html` routes to appropriate widget based on configuration
3. Widget partials access data from `Data[collection][feature]`
4. Most widgets support page-based filtering and styling options
5. Error handling provides fallbacks for missing data

## Adding New Widgets

To create a new widget:

1. Create `section-{widget-name}.html` in `layouts/partials/`
2. Access data via `{{- $collection := index .Data (.Feature.collection | default "features") -}}`
3. Get feature data: `{{ range (index $collection .Feature.feature) }}`
4. Follow existing patterns for styling options and error handling
5. Document any new data structure requirements

## Common Patterns

- **Data access**: `index .Data (.Feature.collection | default "features")`
- **FontAwesome toggles**: `$.Params.{section}.useFontAwesome | default $.Params.useFontAwesome`
- **External link icons**: `$.Params.{section}.externalLinkIcon | default $.Params.externalLinkIcon`
- **Page filtering**: `{{ $page := .page | default 1 }}` with `{{- if eq $.Page $page -}}`
- **Error handling**: Always check for data existence and provide fallbacks