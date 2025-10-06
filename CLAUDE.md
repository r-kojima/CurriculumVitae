# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a Japanese curriculum vitae (職務経歴書) repository that converts Markdown to PDF using GitHub Actions. The main CV document is written in Markdown and automatically converted to PDF with Japanese font support.

## Build and Deployment

### Generate PDF from Markdown

The repository uses GitHub Actions to automatically convert Markdown to PDF:

```bash
# Trigger the workflow manually
gh workflow run convert_markdown_to_pdf.yml

# Or push changes to master branch with changes in markdown/ directory
git add markdown/CurriculumVitae.md
git commit -m "Update CV"
git push origin master
```

The workflow:
- Installs Japanese fonts (Noto CJK)
- Converts [markdown/CurriculumVitae.md](markdown/CurriculumVitae.md) to PDF
- Applies custom styling from [styles/style.css](styles/style.css)
- Uploads the PDF as an artifact named "職務経歴書"

### Local Testing

There's no local build command. To test changes, you need to either:
1. Push to master and check the GitHub Actions workflow output
2. Use the workflow_dispatch trigger to manually run the conversion

## Architecture

- **[markdown/](markdown/)**: Contains the source CV in Markdown format
  - [CurriculumVitae.md](markdown/CurriculumVitae.md) - Main CV document in Japanese
- **[styles/](styles/)**: CSS styling for PDF output
  - [style.css](styles/style.css) - Defines Japanese font families for the PDF
- **[.github/workflows/](/.github/workflows/)**: GitHub Actions workflows
  - [convert_markdown_to_pdf.yml](.github/workflows/convert_markdown_to_pdf.yml) - Automated PDF generation

## Important Notes

- All content is in Japanese
- The PDF generation requires Japanese fonts (Noto Sans JP, Noto Sans Mono CJK JP)
- Changes to the CV should be made in [markdown/CurriculumVitae.md](markdown/CurriculumVitae.md)
- The workflow only triggers on changes to files in the `markdown/` directory or manual dispatch
