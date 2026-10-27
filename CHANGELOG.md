# Changelog

All notable changes to this project will be documented in this file.

## [0.2.0] - 2026-08-07

### Added

- `menuStyle` option: `"default"` keeps the top bar (nested pages render as
  dropdown panels), `"side"` fixes a nested, collapsible side menu to the left
- Folder syntax for `docPages`, nesting by path:
  - `"folder/"` - the folder README.md is its page; folders without a README
    render as group labels, or leave the menu when they have no children
  - `"folder/*.md"` - every markdown file in the folder
  - `"readme:folders"` - discover every folder in the repository with a README
- Folder validation and discovery use one GitHub tree API request; when the
  request fails, explicit folder entries still render unvalidated
- Legacy entries (`"Name"`, `"Label::path"`) work unchanged alongside the
  folder syntax

### Fixed

- On localhost, folder READMEs validate against the local server instead of
  the pushed GitHub tree, so folders not yet pushed still appear in the menu;
  a local run with no globs or discovery entries makes no network request

## [0.1.0] - 2026-08-07

### Added

- MDX tab rendering, matching the tab groups on modelcontextprotocol.io tutorials:
  - `<Tabs>` / `<Tab title="...">` blocks render as clickable content tabs
  - `<CodeGroup>` blocks render titled fences (info strings like `bash macOS/Linux`) as tabbed code blocks
  - Raw markdown on GitHub still renders cleanly - the tags pass through invisibly
- `Label::path` entries in `docPages` pair a menu label with a file path (e.g. `"Weather Servers::../develop/weather-servers/README"`)
- File resolution now tries the entry exactly as given first, so mixed-case nested paths like `../develop/README` resolve on case-sensitive hosts

## [0.0.0] - 2026-08-07

### Added

- Initial release of the **Marked Pages** interactive documentation template
- Single-file (`index.html`) zero-build documentation engine — no compilation or bundling required
- Markdown rendering with GitHub-flavored styling via `github-markdown-css`
- Automatic navigation menu generated from the `docPages` configuration array
- Smart file resolution supporting kebab-case, snake_case, camelCase, and uppercase/lowercase variants
  - Example: menu item `"Utility Types"` resolves to `utility-types.md`, `utility_types.md`, or `utilityTypes.md`
- GitHub-style anchor IDs auto-generated for all headings, enabling direct section links
- Support for files outside `docRoot` using relative path syntax (e.g., `"../QUICKSTART"`)
- Automatic `README.md` loading as the Home page
- GitHub Pages deployment support with auto-detected base URL from `defaultUserName` and `defaultRepoName`
- Configurable `docRoot` (default: `docs`) and `repoBranch` (default: `main`) variables
- Forced light mode for consistent rendering regardless of OS color scheme preference
- Responsive layout with a fixed navigation bar using a dark gradient design
- `QUICKSTART.md` with minimal setup instructions
- Sample `docs/` folder with starter documentation pages
