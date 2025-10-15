# Digital Wealth & Tech - Shopify Landing Page Template

A professional, high-converting landing page template for Digital Wealth & Tech, designed for Shopify stores selling digital products, SaaS tools, and automation templates.

## 🚀 Features

- **Modern Design**: Clean, professional layout inspired by Shopify 2.0 themes (Dawn/Sense)
- **Fully Responsive**: Mobile-first design that works on all devices
- **High Converting**: Optimized for sales with strategic CTAs and social proof
- **Shopify Compatible**: Built with Liquid templating and Shopify best practices
- **SEO Optimized**: Proper meta tags, structured data, and semantic HTML
- **Accessibility**: ARIA labels, alt tags, and keyboard navigation support
- **Performance**: Optimized CSS and minimal JavaScript

## 📁 File Structure

```
├── index.liquid                 # Main homepage template
├── sections/
│   ├── hero.liquid             # Hero section with headline and CTAs
│   ├── featured-products.liquid # Featured products grid
│   ├── testimonials.liquid     # Customer testimonials carousel
│   ├── about.liquid            # About us section
│   └── newsletter.liquid       # Newsletter signup form
└── assets/
    └── style.css               # Custom CSS with Tailwind integration
```

## 🛠 Installation

### Method 1: Upload to Existing Shopify Theme

1. **Access Theme Files**:
   - Go to your Shopify Admin → Online Store → Themes
   - Click "Actions" → "Edit code" on your current theme

2. **Upload Files**:
   - Replace `index.liquid` in the `templates/` folder
   - Create a `sections/` folder and upload all section files
   - Upload `style.css` to the `assets/` folder

3. **Update Theme Settings**:
   - Go to Theme Settings → Homepage
   - Set "index" as your homepage template

### Method 2: Create New Theme

1. **Download Theme Files**:
   - Download all files from this repository
   - Create a new folder for your theme

2. **Upload to Shopify**:
   - Zip the theme folder
   - Go to Themes → "Upload theme"
   - Upload the zip file

3. **Activate Theme**:
   - Click "Actions" → "Publish" to make it live

## 🎨 Customization Guide

### 1. Branding & Colors

**Update Brand Colors** in `assets/style.css`:
```css
:root {
    --brand-blue: #2563eb;      /* Primary blue */
    --brand-purple: #7c3aed;    /* Secondary purple */
    --brand-green: #059669;     /* Success green */
    --brand-orange: #ea580c;    /* Accent orange */
}
```

**Update Logo** in `index.liquid`:
```liquid
<!-- Replace this section in the header -->
<div class="flex-shrink-0">
    <a href="{{ routes.root_url }}" class="text-2xl font-bold text-gray-900">
        <span class="text-brand-blue">Your</span> <span class="text-brand-purple">Brand</span> <span class="text-brand-green">Name</span>
    </a>
</div>
```

### 2. Product Data

**Connect Real Products** in `sections/featured-products.liquid`:

Replace the static product cards with:
```liquid
{% for product in collections.featured.products limit: 4 %}
<div class="bg-white rounded-xl shadow-lg hover:shadow-xl transition-shadow duration-300 group overflow-hidden">
    <div class="relative">
        <img src="{{ product.featured_image | img_url: '400x300' }}" alt="{{ product.title }}" class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-300">
        {% if product.tags contains 'bestseller' %}
        <div class="absolute top-4 right-4 bg-brand-orange text-white px-3 py-1 rounded-full text-sm font-semibold">
            Best Seller
        </div>
        {% endif %}
    </div>
    <div class="p-6">
        <h3 class="text-xl font-semibold text-gray-900 mb-2">{{ product.title }}</h3>
        <p class="text-gray-600 mb-4">{{ product.description | truncate: 120 }}</p>
        <div class="flex items-center justify-between mb-4">
            <span class="text-2xl font-bold text-brand-blue">{{ product.price | money }}</span>
            <div class="flex items-center text-yellow-400">
                <!-- Add rating stars here -->
            </div>
        </div>
        <form action="/cart/add" method="post" enctype="multipart/form-data">
            <input type="hidden" name="id" value="{{ product.selected_or_first_available_variant.id }}">
            <button type="submit" class="w-full bg-gradient-to-r from-brand-blue to-brand-purple text-white py-3 rounded-lg font-semibold hover:from-blue-700 hover:to-purple-700 transition-all duration-300 transform hover:scale-105">
                <i class="fas fa-shopping-cart mr-2"></i>
                Add to Cart
            </button>
        </form>
    </div>
</div>
{% endfor %}
```

### 3. Content Updates

**Hero Section** (`sections/hero.liquid`):
- Update headline and subheadline
- Change CTA button text and links
- Replace hero image with your product mockup

**About Section** (`sections/about.liquid`):
- Update company mission and story
- Replace team photo
- Update contact information

**Testimonials** (`sections/testimonials.liquid`):
- Replace with real customer testimonials
- Update customer photos and names
- Add real review content

### 4. Images & Media

**Replace Placeholder Images**:
- Hero image: Update the product mockup in `sections/hero.liquid`
- Product images: Use real product photos
- About image: Add your team/office photo
- Testimonial avatars: Use real customer photos

**Image Optimization**:
- Use WebP format for better performance
- Compress images before uploading
- Use Shopify's image transformation: `{{ image | img_url: '400x300' }}`

### 5. SEO Optimization

**Update Meta Tags** in `index.liquid`:
```liquid
<title>{{ page_title | default: 'Your Custom Title' }}</title>
<meta name="description" content="Your custom meta description">
<meta property="og:title" content="Your Custom OG Title">
<meta property="og:description" content="Your custom OG description">
```

**Add Structured Data**:
```liquid
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Digital Wealth & Tech",
  "url": "{{ shop.url }}",
  "logo": "{{ 'logo.png' | asset_url }}"
}
</script>
```

## 🔧 Advanced Customization

### 1. Add New Sections

Create new section files in the `sections/` folder:
```liquid
<!-- sections/your-new-section.liquid -->
<section class="py-16 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Your content here -->
    </div>
</section>
```

Include in `index.liquid`:
```liquid
{% section 'your-new-section' %}
```

### 2. Custom JavaScript

Add custom functionality in `index.liquid`:
```javascript
<script>
// Your custom JavaScript here
document.addEventListener('DOMContentLoaded', function() {
    // Initialize your features
});
</script>
```

### 3. Analytics Integration

Add Google Analytics or other tracking:
```liquid
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## 📱 Mobile Optimization

The template is fully responsive with:
- Mobile-first CSS approach
- Touch-friendly buttons and links
- Optimized typography for small screens
- Collapsible mobile navigation
- Fast loading on mobile networks

## ⚡ Performance Tips

1. **Optimize Images**: Use appropriate sizes and formats
2. **Minimize CSS**: Remove unused Tailwind classes
3. **Lazy Loading**: Add `loading="lazy"` to images
4. **CDN**: Use Shopify's CDN for assets
5. **Caching**: Enable browser caching for static assets

## 🐛 Troubleshooting

### Common Issues:

1. **Sections Not Loading**:
   - Check file paths in `index.liquid`
   - Ensure section files are in the `sections/` folder

2. **Styles Not Applying**:
   - Verify `style.css` is uploaded to `assets/`
   - Check for CSS conflicts with theme styles

3. **Products Not Showing**:
   - Create a "featured" collection in Shopify
   - Add products to the collection
   - Check collection handle matches the code

4. **Mobile Menu Not Working**:
   - Ensure JavaScript is enabled
   - Check for console errors

## 📞 Support

For technical support or customization help:
- Email: support@digitalwealthtech.com
- Documentation: [Your documentation site]
- GitHub Issues: [Your repository issues]

## 📄 License

This template is provided as-is for Digital Wealth & Tech. Please respect the intellectual property and use responsibly.

---

**Built with ❤️ for Digital Wealth & Tech**

*Last updated: January 2025*

