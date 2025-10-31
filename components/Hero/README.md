# Hero Banner Component

A modern Drupal Single Directory Component (SDC) for displaying a hero banner with a background image, title, subtitle, description, and call-to-action buttons.

## Features

- 🖼️ **Background image support** with proper accessibility (alt text, width, height)
- 📝 **Rich content structure**: Title (h1), Subtitle (h2), and Summary/Description
- 🎯 **Call-to-action buttons**: Primary and optional secondary CTA buttons
- 📱 **Modern responsive design** using CSS Container Queries
- 🎨 **CSS Grid layout** with 12-column system and subgrid
- ⚡ **Left-aligned content** with white overlay box on desktop
- 🎭 **2:1 aspect ratio** on larger screens for optimal visual presentation
- ♿ **Accessibility-friendly** semantic HTML structure

## Usage

### In Twig Templates

```twig
{% include 'drupal-components:hero' with {
  image: {
    src: '/path/to/image.jpg',
    alt: 'Hero banner background',
    width: 2000,
    height: 1000
  },
  title: 'Welcome to Our Site',
  subtitle: 'Your Trusted Partner',
  summary: 'This is a powerful hero banner that captures attention and provides key information to your visitors.',
  link_url_1: 'https://example.com/get-started',
  link_text_1: 'Get Started',
  link_url_2: 'https://example.com/learn-more',
  link_text_2: 'Learn More'
} %}
```

### Required Fields

- `title`: The main heading (h1)
- `link_url_1`: Primary button URL

### Optional Fields

- `image`: Object with `src`, `alt`, `width`, and `height` properties
- `subtitle`: Secondary heading (h2) for additional hierarchy
- `summary`: Description/summary text (bold styled)
- `link_text_1`: Primary button text (defaults to "Learn more")
- `link_url_2`: Secondary button URL
- `link_text_2`: Secondary button text

## Modern CSS Features

The component uses cutting-edge CSS features:

### Container Queries
Responsive design based on container width (not viewport), allowing the component to adapt to any layout context.

### CSS Grid & Subgrid
- 12-column grid system for flexible layouts
- Subgrid support for nested alignment
- Automatic responsive adjustments at 700px breakpoint

### Layout Behavior
- **Mobile (<700px)**: Image above content, full-width white box
- **Desktop (≥700px)**: Image positioned absolutely as background, content in white box overlay (9 columns wide)

## Styling

The component includes responsive breakpoints using container queries:
- Desktop: 2:1 aspect ratio, 12-column grid (1200px max-width)
- Tablet: Container query at 768px
- Mobile: Container query at 480px, stacked buttons

## Button Styles

Included primary and secondary button styles:
- **Primary**: Blue background (#0071b9) with white text
- **Secondary**: Transparent with blue border, fills on hover
- Fully responsive with hover states

## Customization

You can customize the component by:
1. **Colors**: Update button colors in `hero.css` (`.button--primary`, `.button--secondary`)
2. **Grid**: Adjust the 12-column grid or column spans in `.hero-banner__container`
3. **Aspect ratio**: Change the 2:1 ratio in `@container (min-width: 700px)`
4. **Content width**: Modify `grid-column: 1 / 10` to adjust white box width
5. **Typography**: Update font sizes in the CSS for title, subtitle, and summary
6. **Spacing**: Adjust padding and margins in `.hero-banner__data`

## Comparison with drupal_cms_olivero

See [COMPARISON.md](COMPARISON.md) for a detailed comparison with the official Drupal CMS Olivero hero component, including:
- Feature differences
- Technical approach comparison
- Usage recommendations
- When to use each component
