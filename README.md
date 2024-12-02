# Serhan Ekici's Website

## Overview

This ~300-line POSIX-compliant shell script is a flexible static site generator designed to transform content into a fully functional and transparent website. The generator's core philosophy is file-based modularity, where each piece of content in a directory is generated into a single file. It combines dynamic content generation with version control metadata to create a Git-driven static website.

## Features

- **D.R.Y. - Do Not Repeat Yourself**

  - **Configuration Management**: The script uses a global conf file to define global settings, such as (`BUILD_DIR`, `CSS_FILE`, `PICS_DIR`, `site_lang`, `default_footer`, `site_description`...), and other globally defined custom variables. Individual files can also include their own `conf` file to override global variables or file-specific Git metadata.
  - **Dynamic Placeholder Replacement**: Placeholders like `${author_name}`, `${date_created}`, `${date_modified}`, and `${title}` are dynamically replaced with:
    - **Git Metadata**: For values like creation and modification timestamps, and author names.
    - **Custom Variables**: Defined in either the global `conf` file or file-specific `conf` files.

- **Version Control**:

  - Git metadata is integrated into every page, including:
    - **Creation and Modification Timestamps**: Automatically extracted from Git commit history.
    - **Page-Specific Commit History**: A chronological list of all commits affecting a page, complete with commit messages, author names, and direct links to the GitHub repository.

- **Markdown Injection**:

  - Converts Markdown files to HTML using `pandoc` and injects the output into specified placeholders within HTML templates.
  - Enables the combination of simple Markdown content with HTML.

- **Support for Modular Files**:

  - Modular content can be split into multiple files (e.g., `0.md`, `0.html`) and processed sequentially.
  - Markdown files are converted to HTML using `pandoc`, and prebuilt HTML files are appended directly, allowing for highly customizable page structures.

- **Automatic Index and RSS Generation**:
  - Automatically links generated pages in an `index.html` file.
  - Optionally adds pages to an RSS feed, complete with titles, timestamps, and descriptions.

## Dependencies

- **POSIX Utilities**:
  - `sed`, `realpath`, `printf`, `tr`, `cut`, `grep` `tail` `head`, `rm`: Text processing and file path resolution etc.
- **[pandoc](https://pandoc.org/)**: Converts Markdown files into HTML.
- **[git](https://git-scm.com/)**: Version control system for extracting commit metadata.
- **[shfmt](https://github.com/mvdan/sh#shfmt)**: Formats shell scripts for consistent code style.
- **[shellcheck](https://github.com/koalaman/shellcheck)**: Lints shell scripts to detect errors and enforce best practices.
- **[pre-commit](https://pre-commit.com/)**: Manages and runs hooks in Git repositories, ensuring code quality.
- **[prettier](https://prettier.io/)**: Formats HTML files for consistent and readable output.
- **[stylelint](https://stylelint.io/)**: Lints CSS and enforces consistent styling in stylesheets.

## Build Instructions

1. Ensure all dependencies are installed and accessible in your system's `PATH`.
2. Make the script executable:

```
chmod +x ./gen
```

3. Run the script

```
./gen
```
