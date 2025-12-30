# Agent Guidelines for Tool Collection

This document provides comprehensive information for AI agents and developers working on this tool collection project.

## Project Overview

**Tool Collection** is a repository of lightweight, self-contained HTML tools designed for rapid development and deployment. Each tool is a standalone file that requires no build process or external dependencies (except for Pico CSS from CDN).

### Core Philosophy
- **Simplicity First**: No frameworks, no build tools, no node_modules
- **Self-Contained**: Each tool is independent and can run standalone
- **Fast Development**: Vanilla JavaScript with immediate results
- **Semantic Web**: Standards-based HTML for accessibility and maintainability

## Project Structure & Constraints

### Folder Organization
```
tool-collection/
├── README.md              # User-facing documentation
├── AGENT.md              # This file - AI agent guidelines
├── TOOL_TEMPLATE.html    # Starting template for new tools
├── .gitignore            # Git configuration
├── .gitattributes        # Line ending standards
└── tools/
    ├── index.html        # Central hub/landing page
    └── [tool-name].html  # Individual tool files
```

### Immutable Constraints

These constraints **MUST** be enforced for every tool:

1. **Location**: All tools must be in the `tools/` folder
2. **Format**: Each tool is a single `.html` file
3. **No React/Frameworks**: Use vanilla JavaScript only
4. **Styling**: Must use [Pico CSS](https://picocss.com) from CDN
5. **HTML**: Must be semantic and well-formed
6. **Dependencies**: Load from CDN only, no npm packages
7. **Self-Contained**: Single file, no external JS/CSS files except Pico
8. **Naming**: Use kebab-case for file names (e.g., `data-converter.html`)

## Tool Development Workflow

### Step 1: Planning
- Define the tool's purpose clearly
- Identify what external resources are needed (if any)
- Plan the UI/UX layout

### Step 2: Create the File
```bash
# Copy template
cp TOOL_TEMPLATE.html tools/your-tool-name.html

# Edit the file
# Customize metadata, content, and JavaScript
```

### Step 3: Update Registry
Edit `tools/index.html` and add an entry to the `tools` array:

```javascript
{
    name: "Your Tool Name",
    file: "your-tool-name.html",
    description: "What this tool does and why it's useful."
}
```

### Step 4: Test
- Open `tools/index.html` in a browser
- Verify the tool appears in the hub
- Test the tool functionality
- Verify responsive design works

### Step 5: Commit
```bash
git add tools/your-tool-name.html tools/index.html
git commit -m "Add: Your Tool Name - brief description"
```

## Tool Template Explained

The `TOOL_TEMPLATE.html` provides a standardized structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Standard metadata for SEO and mobile -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="...">
    <title>Tool Name</title>
    
    <!-- Pico CSS from CDN -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.min.css">
    
    <!-- Optional: Inline CSS only -->
    <style>
        /* Custom styles */
    </style>
</head>
<body>
    <main class="container">
        <!-- Content here -->
    </main>
    
    <footer class="container">
        <!-- Back link -->
    </footer>

    <script>
        // Vanilla JavaScript only
    </script>
</body>
</html>
```

### Key Elements to Always Include

1. **Semantic Structure**
   - `<main>` for primary content
   - `<header>` for introductions
   - `<section>` for content blocks
   - `<footer>` with back link to index

2. **Pico CSS Integration**
   - Use `.container` for centered layout
   - Use Pico form elements: `<input>`, `<textarea>`, `<button>`, `<select>`
   - Use `<article>` for card-like containers
   - Use semantic elements like `<table>`, `<code>`, `<pre>`

3. **Navigation**
   - Always include a back link: `<a href="index.html">← Back to Tools</a>`
   - This maintains ease of navigation

## External Resources (CDN)

When a tool needs external libraries, load them from CDN:

### Pico CSS (Always Required)
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.min.css">
```

### Common External Resources (Load from CDN only)
- **Charts**: Chart.js from jsdelivr
- **Date Handling**: date-fns from jsdelivr
- **Utilities**: lodash from jsdelivr
- **Markdown**: marked.js from jsdelivr
- **JSON Validation**: ajv from jsdelivr

### CDN Pattern
```html
<!-- Always use these CDNs -->
https://cdn.jsdelivr.net/npm/package@version/dist/file.min.js
https://unpkg.com/package@version/dist/file.min.js
```

### When to Consider External Resources
- ✅ Small utility libraries (< 50KB minified)
- ✅ Popular, well-maintained projects
- ✅ When vanilla JS is impractical
- ❌ Don't add for minor functionality
- ❌ Don't add if vanilla JS works well enough

## Semantic HTML Standards

All tools must follow semantic HTML5 standards:

### Structure
```html
<html>
  <head>
  <body>
    <header> <!-- Page header -->
    <nav>    <!-- Navigation -->
    <main>   <!-- Main content -->
      <section> <!-- Thematic grouping -->
      <article> <!-- Self-contained content -->
    <aside>  <!-- Supplementary content -->
    <footer> <!-- Footer -->
```

### Form Elements
```html
<!-- Always use semantic form elements -->
<form>
  <fieldset>
    <legend>Group Label</legend>
    <label for="input-id">Label Text</label>
    <input id="input-id" type="text">
  </fieldset>
  <button type="submit">Submit</button>
</form>
```

### Text Content
```html
<!-- Use semantic elements for meaning -->
<strong>Important</strong>  <!-- Not <b> -->
<em>Emphasis</em>          <!-- Not <i> -->
<code>var x = 1;</code>     <!-- For code -->
<kbd>Ctrl+C</kbd>          <!-- For keyboard input
<samp>Output</samp>        <!-- For sample output
<mark>Highlighted</mark>   <!-- For marked text
```

## Common Patterns

### Pattern: Data Display
```html
<article>
    <h2>Results</h2>
    <table>
        <thead>
            <tr><th>Column 1</th><th>Column 2</th></tr>
        </thead>
        <tbody id="results">
            <!-- Results inserted here -->
        </tbody>
    </table>
</article>
```

### Pattern: Input Form
```html
<form id="tool-form">
    <fieldset>
        <legend>Configuration</legend>
        <label for="input-text">
            Text Input
            <input id="input-text" type="text" placeholder="Enter text">
        </label>
    </fieldset>
    <button type="submit">Process</button>
</form>
```

### Pattern: Responsive Grid
```html
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1rem;">
    <article>Item 1</article>
    <article>Item 2</article>
    <article>Item 3</article>
</div>
```

## JavaScript Best Practices

### Module Pattern (Vanilla JS)
```javascript
const MyTool = (() => {
    // Private variables
    const state = {};

    // Private functions
    const init = () => {
        // Initialize
    };

    const handleEvent = (e) => {
        // Handle events
    };

    // Public API
    return {
        init: init
    };
})();

// Initialize on load
document.addEventListener('DOMContentLoaded', MyTool.init);
```

### Event Handling
```javascript
// Prefer addEventListener
document.getElementById('button').addEventListener('click', (e) => {
    e.preventDefault();
    // Handle click
});

// Query selectors
const elements = document.querySelectorAll('.item');
elements.forEach(el => {
    // Process element
});
```

### DOM Manipulation
```javascript
// Create elements
const div = document.createElement('div');
div.className = 'my-class';
div.textContent = 'Hello';

// Append
document.getElementById('container').appendChild(div);

// Remove
div.remove();
```

## Git Workflow

### Commit Messages
Use clear, conventional commit messages:

```
feat: Add data converter tool
fix: Correct calculation in formula parser
docs: Update README with new tool info
style: Improve CSS spacing
refactor: Simplify event handling
```

### File Changes
- Only modify files in the `tools/` folder for new tools
- Update `tools/index.html` to register new tools
- Update root `README.md` if adding notable features

## Testing Checklist

Before committing a new tool:

- [ ] Tool loads without errors (check browser console)
- [ ] All functionality works as intended
- [ ] Responsive design works (test on mobile viewport)
- [ ] Pico CSS styling is applied correctly
- [ ] Semantic HTML validates (use W3C validator)
- [ ] No external JS/CSS files (except Pico from CDN)
- [ ] Back link to `index.html` works
- [ ] Tool appears in the hub page
- [ ] All form inputs are properly labeled
- [ ] Error handling is graceful

## Performance Guidelines

### Target Metrics
- Page load time: < 2 seconds
- Initial tool load: < 500ms
- Smooth interactions at 60 FPS

### Optimization Tips
1. Minify CSS inline styles when useful
2. Defer non-critical rendering
3. Use efficient DOM queries
4. Debounce event handlers if needed
5. Lazy-load large external resources

## Accessibility Standards

### WCAG 2.1 AA Compliance
- [ ] Color contrast ratio ≥ 4.5:1 for text
- [ ] All form inputs have labels
- [ ] Keyboard navigation works
- [ ] Images have alt text
- [ ] Semantic HTML structure
- [ ] Error messages are clear

### Keyboard Navigation
```javascript
// Ensure all interactive elements are keyboard accessible
document.addEventListener('keydown', (e) => {
    if (e.key === 'Enter' && e.target.matches('.my-button')) {
        // Handle action
    }
});
```

## Documentation Template

Add comments to complex JavaScript:

```javascript
/**
 * Processes user input and generates output
 * @param {string} input - The user's input string
 * @returns {string} The processed output
 */
function processInput(input) {
    // Implementation
    return output;
}
```

## Common Issues & Solutions

### Issue: External resource won't load
- Check CDN URL is correct
- Verify network connection
- Use HTTPS links only
- Check browser console for CORS errors

### Issue: Pico CSS not applying
- Ensure `<link>` tag is in `<head>`
- Verify CDN URL is correct
- Check for CSS conflicts
- Use browser dev tools to inspect

### Issue: JavaScript errors
- Check browser console for stack traces
- Verify DOM elements exist before querying
- Use error handling: try/catch for risky operations
- Test in multiple browsers

## Future Enhancements

Potential additions to this collection:
- Tool categories/tags system
- Search functionality in hub
- Dark mode support
- Local storage for tool settings
- Tool versioning system
- Analytics/usage tracking

## Questions & Support

When working on this project:
1. Refer to the constraints list above
2. Check existing tools for patterns
3. Follow the semantic HTML standards
4. Test thoroughly before committing
5. Keep tools focused and single-purpose

---

**Last Updated**: 2025-12-30
**Version**: 1.0
