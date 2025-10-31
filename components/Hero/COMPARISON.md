# Hero Component Comparison

This document compares our updated Hero Banner component with the drupal_cms_olivero Hero component.

## File Structure

Both components follow the same Drupal Single Directory Component (SDC) structure:

```
hero/
├── hero.component.yml
├── hero.twig
├── hero.css
└── README.md (ours only)
```

---

## Component Metadata (hero.component.yml)

### Similarities
- Both use the modern v1 schema: `https://git.drupalcode.org/project/drupal/-/raw/HEAD/core/assets/schemas/v1/metadata.schema.json`
- Both require `title` and `link_url_1` as mandatory fields
- Both support primary and secondary links with custom text
- Both use experimental status
- Both include examples in the schema

### Differences

| Feature | Our Component | drupal_cms_olivero |
|---------|--------------|-------------------|
| **Name** | "Hero Banner" | "Hero" |
| **Description** | More detailed with subtitle mention | Simpler description |
| **Subtitle field** | ✅ Separate `subtitle` field | ❌ No subtitle field |
| **Summary/Description** | Has `summary` field | Has `summary` field |
| **Image definition** | Custom object with src, alt, width, height | References `json-schema-definitions://canvas.module/image` |
| **Image examples** | width: 2000, height: 1000 | width: 2000, height: 1500 |

**Key difference:** Our component includes a **dedicated `subtitle` field** that drupal_cms_olivero doesn't have, giving more hierarchical text structure.

---

## Template (hero.twig)

### Similarities
- Both use `<img>` tag for the hero image (not background-image CSS)
- Both use grid-based layouts with container classes
- Both include primary and secondary CTA buttons
- Both have conditional rendering for optional fields
- Both use the same button class structure

### Differences

| Feature | Our Component | drupal_cms_olivero |
|---------|--------------|-------------------|
| **Title tag** | `<h1>` | `<h2>` |
| **Subtitle** | `<h2>` tag | ❌ Not present |
| **Summary** | `<p>` tag | `<p>` tag |
| **Class prefix** | `hero-banner__*` | `hero__*` |
| **Image attributes** | Conditional width/height | Always present width/height |
| **Container class** | `.hero-banner__container` | `.hero__container` |
| **Documentation** | More detailed variable comments | Standard comments |

**Key differences:**
1. **Heading hierarchy:** Our component uses `<h1>` for title (vs their `<h2>`)
2. **Subtitle support:** Our component has a dedicated `<h2>` subtitle field
3. **Class naming:** We use `hero-banner__*` prefix vs their `hero__*`

---

## Styling (hero.css)

### Similarities
- Both use modern CSS Grid layout
- Both use **container queries** (`@container`) for responsive design
- Both position image absolutely on larger screens
- Both use 2:1 aspect ratio on desktop
- Both have white background data box overlaying the image
- Both use subgrid for nested grid layouts
- Both have responsive breakpoints

### Differences

| Feature | Our Component | drupal_cms_olivero |
|---------|--------------|-------------------|
| **Class prefix** | `.hero-banner__*` | `.hero__*` |
| **Grid columns** | 12 columns explicitly defined | Relies on parent grid |
| **Title styling** | Bold + custom sizing | Just margin control |
| **Summary styling** | Bold text | Bold text |
| **Subtitle styling** | ✅ Dedicated styles | ❌ Not present |
| **Button styles** | ✅ Included in component | ❌ Relies on theme |
| **Color scheme** | Blue (#0071b9) | Relies on CSS variables |
| **Hover states** | ✅ Defined | ❌ Not defined |
| **Text shadows** | ❌ Removed | ❌ Not present |
| **Container padding** | 20px explicit | Uses CSS variables |
| **Breakpoint** | 700px (matches theirs) | 700px |

**Key differences:**
1. **Self-contained styling:** Our component includes button styles; theirs relies on theme
2. **Color system:** We use explicit colors; they use CSS custom properties (more flexible)
3. **Subtitle styles:** We have dedicated subtitle styling
4. **Grid definition:** We explicitly define 12 columns; theirs expects parent grid

---

## Feature Comparison Summary

### Features We Added That They Don't Have
✅ **Subtitle field** - Dedicated subtitle support with proper hierarchy
✅ **Self-contained button styles** - Buttons work without theme dependencies
✅ **Explicit color scheme** - Works out of the box
✅ **Hover states** - Defined button interactions

### Features They Have That We Don't Have
❌ **Canvas module integration** - Their image field references centralized image definition
❌ **CSS variable system** - More flexible theming via custom properties
❌ **Theme integration** - Better integrated with Olivero theme system
❌ **Example image** - They include `images/example-hero.jpg`

### Shared Modern Features
✅ CSS Container Queries
✅ CSS Grid with Subgrid
✅ 2:1 Aspect Ratio
✅ Responsive Design
✅ Absolute Positioned Images
✅ White Content Overlay Box
✅ Primary & Secondary CTAs
✅ Left-aligned Content

---

## Usage Comparison

### Our Component Usage
```twig
{% include 'drupal-components:hero' with {
  image: {
    src: '/images/hero.jpg',
    alt: 'Hero background',
    width: 2000,
    height: 1000
  },
  title: 'Welcome to Our Site',
  subtitle: 'Your Trusted Partner',
  summary: 'This is our hero banner description',
  link_url_1: 'https://example.com',
  link_text_1: 'Get Started',
  link_url_2: 'https://example.com/about',
  link_text_2: 'Learn More'
} %}
```

### drupal_cms_olivero Usage
```twig
{% include 'drupal_cms_olivero:hero' with {
  image: {
    src: '/images/hero.jpg',
    alt: 'Hero background',
    width: 2000,
    height: 1500
  },
  title: 'Welcome to Our Site',
  summary: 'This is our hero banner description',
  link_url_1: 'https://example.com',
  link_text_1: 'Get Started',
  link_url_2: 'https://example.com/about',
  link_text_2: 'Learn More'
} %}
```

**Note:** The main usage difference is our **`subtitle`** field support.

---

## Recommendations

### When to Use Our Component
- When you need a **subtitle field** for additional hierarchy
- When you want **self-contained styling** without theme dependencies
- When you need explicit color schemes
- For standalone projects not using Drupal CMS

### When to Use drupal_cms_olivero Component
- When building on top of Drupal CMS
- When you want tight **theme integration**
- When you need **centralized image management** via Canvas module
- When you prefer **CSS variable flexibility** for theming

### Potential Improvements to Our Component
1. Add CSS custom properties for colors instead of hardcoded values
2. Create a separate `buttons.css` or rely on theme button styles
3. Consider using Canvas module image reference for better integration
4. Add an example image like drupal_cms_olivero has
5. Consider making grid system more flexible (not hardcoded 12 columns)

---

## Technical Advantages

### Our Component
- ✅ More semantic heading hierarchy (h1 → h2 for title → subtitle)
- ✅ Works standalone without theme dependencies
- ✅ Additional content field (subtitle) for richer content
- ✅ Explicit, readable code

### drupal_cms_olivero Component
- ✅ Better integration with Drupal ecosystem
- ✅ More flexible theming system via CSS variables
- ✅ Cleaner, more minimal code
- ✅ Production-tested in Drupal CMS

---

## Conclusion

Both components follow modern Drupal SDC best practices with CSS Grid and container queries. The main differentiators are:

1. **Our component** adds a subtitle field and self-contained styling
2. **drupal_cms_olivero** is more tightly integrated with Drupal CMS theme system

Choose based on your project needs:
- **Standalone/Custom projects** → Use ours
- **Drupal CMS integration** → Use theirs or adapt ours to use their patterns
