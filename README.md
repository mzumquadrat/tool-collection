# Tool Collection

A collection of lightweight, self-contained HTML tools built with vanilla JavaScript and CSS, styled with [Pico CSS](https://picocss.com).

## Project Structure

```
tool-collection/
├── README.md              # This file
├── .gitignore            # Git ignore rules
├── tools/
│   ├── index.html        # Hub page with links to all tools
│   └── [tool-name].html  # Individual tool files
```

## Design Principles

- **No Frameworks**: All tools use vanilla JavaScript, HTML, and CSS
- **Self-Contained**: Each tool is a standalone HTML file
- **Minimal Dependencies**: External dependencies are loaded from CDN when necessary
- **Semantic HTML**: All markup follows semantic HTML standards
- **Consistent Styling**: All tools use [Pico CSS](https://picocss.com) for styling
- **Git-Ready**: Includes standard Git configuration files

## Creating a New Tool

1. Create a new `.html` file in the `tools/` folder
2. Use the template below as a starting point:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Brief description of your tool">
    <title>Tool Name</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.min.css">
    <style>
        /* Optional: Add custom styles here */
    </style>
</head>
<body>
    <main class="container">
        <section>
            <h1>Tool Name</h1>
            <p>Tool description goes here.</p>
        </section>
    </main>
    <script>
        // Your vanilla JavaScript code here
    </script>
</body>
</html>
```

3. Add an entry to the `index.html` file with a link and description

## Features

- 🎨 Beautiful UI with Pico CSS
- 📦 Zero npm dependencies (external resources loaded from CDN)
- 🚀 Fast and lightweight
- 📱 Responsive design
- ♿ Semantic HTML for accessibility

## Available Tools

See `tools/index.html` for a complete list of available tools.

## Development

Simply edit the HTML files directly. No build process required.

## License

[Add your license here]
