# Personal Portfolio Website

This is my personal portfolio website built with Hugo and the PaperMod theme.

## 🚀 Tech Stack

- [Hugo](https://gohugo.io/) - Static Site Generator
- [PaperMod](https://github.com/adityatelange/hugo-PaperMod) - Theme
- GitHub Pages - Hosting
- GitHub Actions - CI/CD

## ✨ Features

### Core Features

- 🎨 Modern and Clean Design
- 🌓 Automatic Dark/Light Mode
- 📱 Fully Responsive Layout
- 🔍 Full-text Search Functionality
- 🚀 Fast Loading (90+ PageSpeed Score)
- 📊 SEO Optimized
  - Open Graph Support
  - Twitter Cards Support
  - Custom Meta Tags

### Content Features

- 💼 Project Showcase
- 📈 Experience Timeline
- 🔗 Social Media Integration
- 📄 Resume/CV Link
- 📧 Contact Information
- 📝 Markdown Support

### Technical Features

- 🖼️ Image Optimization
  - WebP Format Support
  - Lazy Loading
  - Responsive Images
- 🔒 Cache Control Headers
- 📦 Asset Fingerprinting
- 🤖 RSS Feed Generation
- 🎯 Custom 404 Page

## 📁 Project Structure

```
├── assets/             # Website assets (images, etc.)
├── content/            # Website content
│   ├── projects/       # Project pages
│   └── experience/     # Experience pages
├── layouts/            # Custom layouts
├── static/            # Static files
├── themes/            # Hugo themes
│   └── PaperMod/     # PaperMod theme
├── config.yaml        # Hugo configuration
└── README.md         # This file
```

## 🚀 Deployment

The website is automatically deployed to GitHub Pages using GitHub Actions when changes are pushed to the main branch. The deployment workflow is defined in `.github/workflows/gh-pages.yml`.

### Deployment Features

- 🔄 Automatic builds on push
- 🔒 Secure deployment
- 📊 Build status checks
- 🚫 Failed build protection

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🔧 Troubleshooting

### Common Issues

1. **Hugo Version Mismatch**: Make sure you're using Hugo Extended version
2. **Submodule Issues**: If theme is missing, run `git submodule update --init --recursive`
3. **Build Errors**: Check Hugo version compatibility and YAML syntax
4. **Image Processing**: Ensure you have Hugo Extended for image processing features

### Development Tips

- Use `hugo server --navigateToChanged` for better development experience
- Enable draft mode with `-D` flag for testing draft content
- Use `hugo --minify` for production builds
