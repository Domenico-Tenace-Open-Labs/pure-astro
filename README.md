# Pure Astro

Welcome to the repository of **Pure Astro**, an open-source project for personal websites and blogs, fast, modern, and dedicated to a SEO-friendly experience.
Originally based on the [Milky-Way](https://github.com/ttomczak3/Milky-Way) template by [Astro](https://astro.build/), **Pure Astro** extends and customizes the structure to form the solid foundation of my web space ("digital garden"), designed for sharing technical articles, projects, and a complete portfolio.

## What is Pure Astro?

Pure Astro is the codebase ("engine") that provides the backbone of this website, based on the Astro framework. Focus primarily on creating content and less on complex maintenance.
Its advantages:

- **Zero JS by default:** Astro reduces page weight by shipping zero JavaScript (or the bare minimum) to the client, maximizing speed and keeping "Core Web Vitals" metrics top-notch.
- **Content Collections support:** The entire blog and various projects rely on Markdown files (`.md` or `.mdx`), complete with strict chronological sorting and dynamic pagination features.
- **Custom design:** The graphic interfaces are built on extensive customizations of the _Bulma CSS_ framework to make them elegant without sacrificing readability.

## How to run it in Dev

The project utilizes the performance of the `pnpm` manager (as it is natively supported), but works just as well with classic `npm` / `yarn`. To test and modify the site on your local machine, follow these quick steps:

1. **Clone the repository**:

   ```bash
   git clone https://github.com/DomeT99/pure-astro.git
   cd pure-astro
   ```

2. **Install dependencies**:

   ```bash
   pnpm install
   ```

3. **Start the development server with live-preview**:
   ```bash
   pnpm run dev
   ```
   This command will concurrently launch a local web server with the _Hot Module Replacement (HMR)_ feature.
   Now open your machine's browser and go to: **`http://localhost:4321`** (or whatever port is shown in the terminal!). On every save in your `.astro` files, the page will automatically reload the view.

## Support

If you like this project, you can support me with a very small donation.

I would be grateful 🥹
<br/>
<br/>
<a href="https://www.buymeacoffee.com/domenicotenace" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
