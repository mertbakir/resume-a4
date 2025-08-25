# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo theme called "Resume A4" - a simple, print-friendly resume generator that outputs A4-sized resumes. Users write their resume content in YAML files, and Hugo generates a clean, professional resume website that can be printed or saved as PDF.

## Development Commands

This is a Hugo theme, so development happens in the context of a Hugo site:

```bash
# Start Hugo development server (run from main project, not theme folder)
hugo server

# Build the site
hugo

# Clean resources (recommended workflow step)
rm -rf resources/
```

## Architecture

### Core Structure
- **layouts/**: Hugo templates that render the resume sections
- **assets/css/**: SCSS stylesheets for styling and print optimization
- **exampleSite/**: Complete working example with config and data files
- **static/**: Static assets like avatar images

### Key Files
- `exampleSite/config.yaml`: Main configuration defining page layout, sections, and styling options
- `exampleSite/data/`: YAML data files containing actual resume content (education.yaml, experience.yaml, etc.)
- `layouts/home.html`: Main template that orchestrates the entire resume layout
- `layouts/partials/`: Reusable components for different resume sections

### Section System
The theme uses a flexible widget system where each resume section can use different rendering widgets:
- `details-list`: Default widget for experience, education, projects, etc.
- `word-list`: For skills, interests (supports list, compact, title-list styles)  
- Custom section templates in `layouts/partials/section-*.html`

### Configuration Architecture
The `config.yaml` uses a feature-based system where:
- `pages[]`: Define multiple resume pages
- `features[]`: List of resume sections per page
- Each feature specifies: widget type, data source, title, and rendering options

### Workflow
1. Users copy `config.yaml` and `data/` folder to their Hugo project root
2. Theme generates resume from YAML data using the configured layout
3. For theme development: make changes, delete `resources/` folder, build with `hugo server`, copy `resources/` back to theme

## Data Structure

Resume content is stored in `data/*.yaml` files with consistent structure:
- Each entry typically has: title, subtitle, date, details (markdown), links
- Publications support APA/IEEE citation styles
- Skills/interests use simple string arrays or grouped lists