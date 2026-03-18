# Portfolio Project (Vue + Vite + Tailwind)

## Overview
This is a personal portfolio website built with Vue 3 and Vite, styled with Tailwind CSS. It features a dark, space-inspired UI with interactive sections and 3D background visuals.

## Features
- Responsive one-page portfolio layout
- Hero, About, Education & Credentials, Contact sections
- `SpaceScene` 3D background using Three.js + @tresjs/core
- Diploma / Certificate / Resume viewer using modal `iframe`
- Contact form with EmailJS integration
- Custom glass-style button and modern typography

## Tech Stack
- Vue 3
- Vite
- Tailwind CSS
- three.js, @tresjs/core
- GSAP
- PostCSS, autoprefixer

## Project Structure
```
index.html
package.json
postcss.config.js
tailwind.config.js
vite.config.js
PROJECTBESCHREIBUNG.md
src/
  App.vue
  main.js
  style.css
  assets/
  components/
    layout/
      ScrollIndicator.vue
      SpaceScene.vue
    sections/
      About.vue
      Contact.vue
      Education&Credentials.vue
      Hero.vue
```

## Installation
1. Clone repository:
   ```bash
   git clone https://github.com/osman-turkarslan/portfolio.git
   cd portfolio
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start dev server:
   ```bash
   npm run dev
   ```
4. Open browser:
   `http://localhost:5173`

## Build & Preview
```bash
npm run build
npm run preview
```

## Deployment
- Production output is in `dist/` after `npm run build`.
- Deploy anywhere static hosts allow (Netlify, Vercel, GitHub Pages).

## Contact Details
- Email: osmanturkarslan1620@gmail.com
- LinkedIn: https://linkedin.com/in/osman-turkarslan
- GitHub: https://github.com/osman-turkarslan
- Live URL: https://osmanturkarslan.github.io/portfolio

## Documentation
For full project documentation, requirements, setup and structure details, visit [PROJECTBESCHREIBUNG.md](./PROJECTBESCHREIBUNG.md).
