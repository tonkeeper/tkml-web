# TKML (TonKeeper Markup Language)

TKML isn't just a markup language; it's like your retro '90s game console for web apps! No need for CSS or JS—just plug in your components in XML format and play. We've sprinkled in some '90s vibes and a dash of HTTP/1.1 nostalgia to keep things fun and simple.

TKML is designed for building fast, mobile-friendly web applications with minimal configuration. Think of it as your trusty sidekick, providing a set of pre-styled components that follow modern design principles, so you can focus on creating awesome content without sweating the small stuff.

You can create the simplest TKML app by uploading an `index.tkml` page to your website. This page serves as the entry point for your application. Here's a basic example:

1. **Create an `index.tkml` file**: This file will contain your TKML markup. For instance:

   ```xml
   <title>Hello</title>
   <desc>
       Hello world! This is a minimal TKML website.
   </desc>
   ```

2. **Upload the file to your server**: Place the `index.tkml` file in the root directory of your website or any accessible path.

3. **Access your TKML app**: Go to http://tkml.app, and type `example.com/index.tkml` in input field.

This simple setup will render a page with a title and a description, demonstrating the basic structure of a TKML document.

## Features

- 🎨 Pre-styled components with dark/light mode support
- 📱 Mobile-first responsive design
- 🔄 Built-in navigation system with browser history support
- ⚡ Streaming XML parser for fast rendering
- 🎯 Zero CSS/JS configuration needed
- 🔌 Extensible component system

## Quick Start
This example demonstrates how to embed a TKML app within your own application
```html
<!DOCTYPE html>
<html>
<head>
    <title>TKML App</title>
    <link rel="stylesheet" href="./styles.min.css">
    <script src="./tkml.min.js"></script>
</head>
<body>
    <div id="container"></div>
    <script>
        const container = document.getElementById('container');
        const tkml = new TKML(container, { dark: true });
        tkml.load('index.tkml');
    </script>
</body>
</html>
```

## Components

### Title
Displays a heading.
```xml
<title>Regular Title</title>
<title center>Centered Title</title>
```
Attributes:
- `center` - Centers the title text

### Desc
Displays descriptive text in a muted color.
```xml
<desc>Description text</desc>
<desc center>Centered description</desc>
```
Attributes:
- `center` - Centers the description text

### Button
Creates a clickable button.
```xml
<button href="/action">Click Me</button>
```
Attributes:
- `href` - URL to navigate to when clicked
- `target` - Target window ('_blank' for new window)
- `preload` - Set to "true" to preload the href URL

### Input
Creates a text input field.
```xml
<input placeholder="Enter text" href="/submit" name="query" />
```
Attributes:
- `placeholder` - Placeholder text
- `value` - Initial value
- `type` - Input type (text, password, etc)
- `href` - URL to submit to on Enter
- `name` - Parameter name for the submitted value

### Section
Creates a clickable section with optional icon.
```xml
<section href="/details" icon="/icons/arrow.png">Section content</section>
```
Attributes:
- `href` - URL to navigate to when clicked
- `icon` - URL of the icon to display
- `target` - Target window
- `preload` - Set to "true" to preload the href URL

### List
Groups items in a list container.
```xml
<list>
    <section>Item 1</section>
    <section>Item 2</section>
</list>
```

### Info
Creates an info block with title, description, image and button.
```xml
<info>
    <img src="/image.jpg" height="200" />
    <title>Title</title>
    <desc>Description</desc>
    <button href="/action">Action</button>
</info>
```

### Checkbox
Creates a toggle switch.
```xml
<checkbox href="/toggle" checked>Toggle me</checkbox>
```
Attributes:
- `href` - URL to call when toggled
- `checked` - Initial checked state
- `target` - Target window
- `preload` - Set to "true" to preload the href URL

### Radio
Creates a radio button in a group.
```xml
<radio group="options" href="/select" checked>Option 1</radio>
<radio group="options" href="/select">Option 2</radio>
```
Attributes:
- `group` - Group name for related radio buttons
- `href` - URL to call when selected
- `checked` - Initial checked state
- `target` - Target window
- `preload` - Set to "true" to preload the href URL

### Code
Displays syntax-highlighted code.
```xml
<code lang="javascript">
const x = 42;
console.log(x);
</code>
```
Attributes:
- `lang` - Programming language for syntax highlighting

### Img
Displays an image.
```xml
<img src="/image.jpg" alt="Description" height="200" />
```
Attributes:
- `src` - Image URL
- `alt` - Alternative text
- `height` - Fixed height in pixels

### Loader
Creates a loading indicator that loads content when visible.
```xml
<loader href="/content" />
```
Attributes:
- `href` - URL of content to load when loader becomes visible

### Links
Creates a clickable link.
```xml
<a href="/page" preload="true">Click here</a>
```
Attributes:
- `href` - URL to navigate to
- `target` - Target window ('_blank' for new window)
- `preload` - Set to "true" to preload the href URL

### Text Formatting
Basic text formatting tags:
```xml
<b>Bold text</b>
<i>Italic text</i>
<u>Underlined text</u>
<s>Strikethrough text</s>
```

### Line Break
Adds vertical spacing:
```xml
<br/>
```

All components that support navigation (`button`, `section`, `a`, etc) have these common attributes:
- `href` - URL to navigate to
- `target` - Target window ('_blank' for new window)
- `preload` - Set to "true" to preload the URL

## Examples

Complete page example:
```xml
<title center>Welcome</title>
<desc center>Select an option below</desc>
<list>
    <section href="/option1" icon="/icons/1.png">First Option</section>
    <section href="/option2" icon="/icons/2.png">Second Option</section>
</list>
<info>
    <img src="/banner.jpg" height="200" />
    <title>Important Info</title>
    <desc>Additional details here</desc>
    <button href="/more">Learn More</button>
</info>
```

### Automatic Dark Mode

```javascript
// Automatically detects system preference
new TKML(container);

// Force dark mode
new TKML(container, { dark: true });
```

### Navigation with History

All navigation is handled automatically through `href` attributes. The library manages browser history and provides smooth transitions between pages.

## Development

1. Install dependencies:
```bash
npm install
```

2. Start development server with hot reload:
```bash
npm run dev
```

3. Build for production:
```bash
npm run pack
```

## Browser Support

TKML works in all modern browsers that support:
- XMLHttpRequest
- ES6+ JavaScript
- CSS Custom Properties
- Browser History API

## License

MIT
