# ASCII Banner Component

A custom web component that renders text as ASCII art using FIGlet fonts. Perfect for creating retro terminal-style banners and headers.

<img width="1231" height="138" alt="image" src="https://github.com/user-attachments/assets/15600cb2-5a6c-4b23-a5db-cd27d9f74eb2" />


## Overview

The `ascii-banner` component converts plain text into stylized ASCII art using FIGlet font files (.flf format). It features automatic scaling, responsive sizing, and support for multiple font families and size presets.

## Installation

Include the component script in your HTML:

```html
<script type="text/javascript" src="path/to/ascii-banner.js"></script>
```

The component will automatically register itself as `<ascii-banner>`.

## Usage

### Basic Example

```html
<ascii-banner
    text="Hello World"
    font-url="/fonts/Ogre.flf"
    size="standard">
</ascii-banner>
```

### With All Options

```html
<ascii-banner
    text="Welcome"
    font-url="/fonts/Cyberlarge.flf"
    size="statement"
    font-family="terminal-mono"
    color="var(--foreground)"
    fit="auto"
    aria-label="Welcome banner">
</ascii-banner>
```

## Attributes

### Required Attributes

| Attribute | Type | Description |
|-----------|------|-------------|
| `text` | string | The text to render as ASCII art |
| `font-url` | string | URL path to the FIGlet font file (.flf) |

### Optional Attributes

| Attribute | Type | Default | Description |
|-----------|------|---------|-------------|
| `size` | string | `"standard"` | Size preset (see Size Presets below) |
| `font-family` | string | `"terminal-mono"` | Font family for rendering (see Font Families below) |
| `color` | string | `"inherit"` | Text color (CSS color value) |
| `fit` | string | `"auto"` | Auto-fit mode (see Fit Modes below) |
| `aria-label` | string | - | Accessibility label (recommended) |

## Size Presets

The `size` attribute accepts the following presets with responsive font sizing:

- `badge` - Small badge size: `clamp(1rem, 0.35vw + 0.85rem, 1.6rem)`
- `mini` - Mini size: `clamp(1.2rem, 0.4vw + 1rem, 2rem)`
- `compact` - Compact size: `clamp(1.4rem, 0.45vw + 1.2rem, 2.6rem)`
- `standard` - Standard size: `clamp(2.2rem, 0.9vw + 1.8rem, 4.4rem)` (default)
- `statement` - Large statement: `clamp(3.4rem, 1.6vw + 2.8rem, 6.4rem)`
- `heroic` - Extra large: `clamp(4.6rem, 2.2vw + 3.8rem, 8.6rem)`

## Font Families

The `font-family` attribute controls the monospace font stack used for rendering:

- `terminal-mono` - Terminal-style fonts: Inconsolata, Fira Code, Source Code Pro, monospace (default)
- `system-mono` - System monospace: SFMono-Regular, Menlo, Consolas, Liberation Mono, monospace
- `retro-pixel` - Retro pixel fonts: Courier New, Lucida Console, Monaco, monospace

## Fit Modes

The `fit` attribute controls automatic scaling behavior:

- `auto` - Auto-fit by width only (default)
- `both` - Constrain by both width and height
- `width` - Constrain by width only
- `height` - Constrain by height only
- `none` - No auto-fitting, use natural size

When auto-fit is enabled, the component uses `ResizeObserver` to automatically scale the banner to fit its container while maintaining aspect ratio.

## FIGlet Fonts

The component requires FIGlet font files (.flf format). Popular fonts include:

- **Ogre** - Bold block letters
- **Cyberlarge** - Futuristic tech style
- **Colossal** - Very large characters
- **ANSI Shadow** - 3D shadow effect
- **Standard** - Classic FIGlet default
- **Slant** - Italic/slanted style
- **Banner** - Wide horizontal banners
- **Block** - Solid block characters
- **Doom** - Gaming style
- **Epic** - Dramatic large text
- **Graffiti** - Street art style
- **Larry 3D** - 3D perspective effect
- **Star Wars** - Sci-fi opening crawl style
- **Ghost** - Spooky style
- **Speed** - Racing style
- **Bloody** - Horror dripping style

You can find more FIGlet fonts at:
- [FIGlet Fonts Archive](http://www.figlet.org/fontdb.cgi)
- [patorjk.com](http://patorjk.com/software/taag/)

## Examples

### Logo in Navigation

```html
<a class="logo" href="/">
    <ascii-banner
        text="MySite"
        font-url="/fonts/Ogre.flf"
        size="badge"
        font-family="terminal-mono"
        color="var(--foreground)"
        fit="none">
    </ascii-banner>
</a>
```

### Page Header

```html
<header>
    <ascii-banner
        text="Welcome"
        font-url="/fonts/Cyberlarge.flf"
        size="statement"
        font-family="terminal-mono"
        color="var(--foreground)">
    </ascii-banner>
</header>
```

### Article Title

```html
<article>
    <ascii-banner
        text="{{title}}"
        font-url="/fonts/ANSI Shadow.flf"
        size="standard"
        font-family="terminal-mono"
        color="var(--foreground)">
    </ascii-banner>
</article>
```

## Dynamic Updates

The component supports dynamic attribute updates. Changing any attribute will automatically re-render the banner:

```javascript
const banner = document.querySelector('ascii-banner');
banner.setAttribute('text', 'New Text');
banner.setAttribute('size', 'heroic');
```

## Browser Support

- Modern browsers with Web Components support
- Shadow DOM API
- ResizeObserver API (for auto-fit feature)
- Fetch API (for loading font files)

## Performance

- Font files are cached after first load
- Resize operations are debounced (16ms) for smooth performance
- Auto-fit calculations reset scale before measuring for accurate dimensions

## Accessibility

Always include an `aria-label` attribute for screen readers:

```html
<ascii-banner
    text="Hello"
    font-url="/fonts/Ogre.flf"
    aria-label="Hello">
</ascii-banner>
```

## Styling

The component uses Shadow DOM, so external CSS won't affect it directly. Use the `color` attribute to control text color, and ensure the container has appropriate width constraints.

## Technical Details

- Built with Web Components (Custom Elements API)
- Uses Shadow DOM for style encapsulation
- Includes embedded FIGlet.js library for font parsing and rendering
- Supports all FIGlet font features including smushing rules

## License

This component includes the FIGlet.js library, which is licensed under MIT. See the component source code for full license information.

## Credits

- FIGlet.js by [patorjk](https://github.com/patorjk/figlet.js)
- FIGlet font format specification

