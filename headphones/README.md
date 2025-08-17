# Media Agency Landing Page (Responsive)

A clean, responsive landing page suitable for a creative/media/marketing agency. The layout adapts for **mobile**, **tablet**, and **desktop** and includes a hero section, “What we do” services, results/metrics, a contact form, and footer.

> The design reference shows three breakpoints with consistent typography, spacing, and color tokens. This README documents how to run, edit, and extend the project.

---

## ✨ Features

- **Responsive layout** across mobile, tablet, and desktop breakpoints
- **Accessible navigation** with keyboard focus states
- **Hero section** with headline, subtext, and call-to-action
- **Services grid** with iconography
- **Results/metrics** section using geometric badges
- **Contact form** with basic client-side validation (name, email, message)
- **Lightweight stack**: HTML5, modern CSS (Flexbox/Grid, custom properties), vanilla JS
- **Performance-first** with image optimization guidance

---

## 🧱 Project Structure

```text
.
├── index.html
├── css/
│   ├── base.css          # Reset + base typography + utilities
│   ├── variables.css     # Color & spacing tokens
│   └── styles.css        # Layout & components
├── js/
│   ├── main.js           # Navigation, smooth scroll, utilities
│   └── form.js           # Contact form validation
├── assets/
│   ├── images/           # Hero & section artwork
│   └── icons/            # SVG icons
└── README.md
```

> If you already created **`base.css`** and **`styles.css`** in a previous task, keep the same filenames and simply add `variables.css` (optional, for tokens).

---

## Design Tokens (suggested)

Define these in `css/variables.css` and import at the top of `styles.css`:

```css
:root {
  --color-bg: #0f1a24;
  --color-surface: #102030;
  --color-text: #e8eef4;
  --color-muted: #9fb2c3;
  --color-accent: #ff6a64;   /* CTA & icons */
  --radius-2xl: 1.25rem;
  --radius-xl: 0.875rem;

  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-12: 3rem;
  --content-max: 72rem;
}
```

> Adjust colors to match your brand; the sample design uses a dark navy background with a coral accent.

---

## 📱 Responsive Breakpoints (suggested)

```css
/* Mobile-first defaults */
@media (min-width: 48rem) {   /* ≥ 768px: tablet */
  /* tablet styles */
}
@media (min-width: 64rem) {   /* ≥ 1024px: small desktop */
  /* desktop styles */
}
@media (min-width: 80rem) {   /* ≥ 1280px: large desktop (optional) */
  /* wide layouts */
}
```

---

## 🚀 Getting Started

### 1) Open locally
No build step required.

```bash
# Option A: double-click index.html
# Option B: use a simple static server for live reload:
python3 -m http.server 5500
# then open http://localhost:5500
```

### 2) Link your styles
In `index.html`, within `<head>`:

```html
<link href="css/base.css" rel="stylesheet" />
<link href="css/variables.css" rel="stylesheet" />
<link href="css/styles.css" rel="stylesheet" />
```

### 3) Link your scripts (optional)
Place before the closing `</body>`:

```html
<script src="js/main.js" defer></script>
<script src="js/form.js" defer></script>
```

---

## 🧩 Key Sections (HTML Hints)

```html
<header class="site-header">
  <nav class="nav">
    <a class="logo" href="#">Brand</a>
    <button class="nav-toggle" aria-expanded="false" aria-controls="nav-menu">Menu</button>
    <ul id="nav-menu" class="nav-menu">
      <li><a href="#services">What we do</a></li>
      <li><a href="#results">Results</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>
</header>

<section class="hero" id="home">
  <div class="hero__content">
    <h1>Lorem ipsum dolor sit amet</h1>
    <p>Short value proposition that explains your service.</p>
    <a class="btn btn-accent" href="#contact">Get Started</a>
  </div>
  <figure class="hero__art">
    <!-- optimized hero image -->
  </figure>
</section>

<section class="services" id="services">
  <h2>What we do…</h2>
  <ul class="services__grid">
    <!-- 4–6 items with SVG icons + labels -->
  </ul>
</section>

<section class="results" id="results">
  <h2>Our results speak for themselves</h2>
  <ul class="results__grid">
    <!-- geometric badges with % metrics -->
  </ul>
</section>

<section class="contact" id="contact">
  <h2>Contact us</h2>
  <form novalidate>
    <label>Name <input type="text" name="name" required></label>
    <label>Email <input type="email" name="email" required></label>
    <label>Your message <textarea name="message" rows="5" required></textarea></label>
    <button class="btn btn-accent" type="submit">Send</button>
  </form>
</section>

<footer class="site-footer">© Your Brand</footer>
```

---

## ✅ Accessibility Checklist

- Semantic landmarks: `header`, `nav`, `main`, `section`, `footer`
- Sufficient color contrast (aim for WCAG AA)
- Focus states visible for links & buttons
- `aria-expanded` toggles on mobile nav button
- Form inputs have labels, errors announced to screen readers
- Images include descriptive `alt` text or `aria-hidden="true"` when decorative

---

## ⚡ Performance Tips

- Export hero/section images at multiple sizes and use `srcset` + `sizes`
- Prefer SVG for icons
- Minify/inline critical CSS if needed
- Defer non-critical scripts
- Run a Lighthouse audit and aim for 90+ scores

---

## 🧪 Form Validation (basic example)

In `js/form.js`:

```js
document.addEventListener("DOMContentLoaded", () => {
  const form = document.querySelector(".contact form");
  form?.addEventListener("submit", (e) => {
    const name = form.querySelector("input[name='name']");
    const email = form.querySelector("input[name='email']");
    const message = form.querySelector("textarea[name='message']");

    const errors = [];
    if (!name.value.trim()) errors.push("Please enter your name.");
    if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email.value)) errors.push("Enter a valid email.");
    if (!message.value.trim()) errors.push("Please write a short message.");

    if (errors.length) {
      e.preventDefault();
      alert(errors.join("\n"));
    }
  });
});
```

---

## 📦 Deployment

Any static hosting works:
- GitHub Pages
- Netlify (drag & drop the folder)
- Vercel (Static project)
- Cloudflare Pages

> Ensure your assets use relative paths so the site works from any base URL.

---

## 🤝 Contributing

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/section-name`
3. Commit changes: `git commit -m "Add xyz"`
4. Push and open a PR

---

## 📝 License

MIT — free to use, modify, and distribute. Keep the license in derived works.

---

## 🙌 Acknowledgements

- Stock imagery & icons: replace with properly licensed assets for production use
- ALX/learning tasks inspiration for `base.css` + `styles.css` split
