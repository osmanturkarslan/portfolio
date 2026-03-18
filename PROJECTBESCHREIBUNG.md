# Projektbeschreibung: Portfolio Webapp (Vue + Vite + Tailwind)

## 1. Projekttitel
**Portfolio Website**

## 2. Autor & Kontakt
- Name: Osman Türkarslan
- E-Mail: osmanturkarslan1620@gmail.com
- Telefon: 078 246 33 56
- LinkedIn: https://linkedin.com/in/osman-turkarslan
- GitHub: https://github.com/osman-turkarslan
- Website: https://osmanturkarslan.github.io/portfolio

## 3. Key Visual / Hero Image / Titelbild
- Aktuelles Hero-Segment als SpaceScene-3D-Background (`src/components/layout/SpaceScene.vue`)
- Titeltext in `Hero`-Komponente (`src/components/sections/Hero.vue`)
- Menüstruktur: `Hero`, `About`, `Education & Credentials`, `Contact` plus `ScrollIndicator`

## 4. Beschreibung
Diese Portfolio-Single-Page/Web-App wurde gebaut für einen Platform Developer mit Fokus auf moderne Frontend-Architektur.

Ziele:
- Präsenz als Developer zeigen
- Technologie-Stacks und Fähigkeiten visuell darstellen
- Kontaktdaten und Zeugnisse (Diplom, Certificate, Resume) als modales PDF-Zugriff anbieten
- Responsive, dunkles Cyber-/Space-Design, Animationen, 3D Interaktionen (via TresJS, Three.js)

## 5. Bilder
- Assets/Logo & Illustrations: `src/assets/uludag-üni-logo.png`, `src/assets/techpro-logo.png`, `src/assets/my-resume.jpg`, `src/assets/star.png` etc.
- Hintergrundbilder: `src/assets/nebula*.jpg`
- Hinweis: Grafiken sind in `src/assets` geführt, ein 3D-Style durch Backgrounds + SpaceScene.

## 6. Gebrauchte Tools / Tech-Stack (visuell)
- **Framework**: Vue 3
- **Build Tool**: Vite
- **CSS**: Tailwind CSS 4
- **3D & WebGL**: three.js, @tresjs/core
- **Animation**: GSAP
- **Post-Processing**: PostCSS, autoprefixer
- **Versionierung**: Git

## 7. Projektstruktur
```
index.html
package.json
src/
  App.vue
  main.js
  style.css
  components/
    layout/ScrollIndicator.vue
    layout/SpaceScene.vue
    sections/About.vue
    sections/Contact.vue
    sections/Education&Credentials.vue
    sections/Hero.vue
  assets/*
postcss.config.js
tailwind.config.js
vite.config.js
```

## 8. Installationsanleitung (Setup)

### 8.1 Voraussetzungen
- Node.js >= 18.x (oder 16.14+)
- NPM (zu Node passend) oder Yarn
- optional: VSCode

### 8.2 Klonen + Start
1. Repo klonen (öffentlich gestellt):
```bash
git clone https://github.com/osman-turkarslan/portfolio.git
cd portfolio
```
2. Abhängigkeiten installieren:
```bash
npm install
```
3. Dev-Server starten:
```bash
npm run dev
```
4. Browser öffnen:
`http://localhost:5173`

### 8.3 Build für Produktion
```bash
npm run build
npm run preview
```

### 8.4 Oder als Docker-Container (optional)
Hier wird ein einfacher Build-Befehl genutzt (keine Dockerfile vorhanden, kann ergänzt werden):

```bash
npm run build
# output in dist/
```

## 9. Status / Module
- **Tailwind**: durch `@import "tailwindcss"` in `src/style.css` geladen
- **PDF-Modal**: `Education&Credentials` verwendet `iframe`, PDF-Dateien aus `public` oder `src/assets` (einbinden in `public/resume.pdf` etc.)

## 10. Hinweise zu Versionsnummern / Programme
- Node.js: 18.x / 20.x empfohlen
- NPM: 10.x/12.x
- Vite: in `package.json` Version `^7.3.1`
- Vue: `^3.5.24`
- Tailwind: `^4.1.18`
- @tresjs/core: `^5.3.3`
- three: `^0.182.0`
- gsap: `^3.14.2`
- PostCSS: `^8.5.6`
- Autoprefixer: `^10.4.23`

## 11. Setup Schritt für Schritt
1. Projektdateien prüfen (Struktur, Komponenten, Assets)
2. Konfiguration prüfen: `tailwind.config.js`, `postcss.config.js`
3. Styling prüfen: `src/style.css` inkl. Typografie und Farben
4. Komponenten prüfen:
  - `Hero`: Titel, CTA
  - `About`: Textbeschreibung
  - `Education&Credentials`: Card-Abschnitte, PDF-Modal
  - `Contact`: Kontaktfelder, Social-Icons
5. 3D-Hintergrund (SpaceScene) starten
6. Script-Funktionalität testen: PDF Open, Contact Form, smooth-scrolling

## 12. Repository Link
- GitHub Public Repo: https://github.com/osman-turkarslan/portfolio

## 13. Deployment
- Hosting: GitHub Pages
- CI/CD: GitHub Actions
- Automatisches Deployment via .github/workflows/deploy.yml
- Live URL: https://osmanturkarslan.github.io/portfolio

---
