# Neural Link Landingpage

A polished, dark-themed landing page for a fictional brain-computer interface (BCI) startup — Neuralink-style branding with an interactive **WebGL 3D hero** (custom GLSL shaders over a depth-mapped image via `@react-three/fiber` + `three`), plus a full marketing site: features, technology deep-dive, applications timeline, safety, testimonials, FAQ, and CTA sections.

Originally generated with [v0.app](https://v0.app); hardened and documented here for open use.

## What it does

- Full-screen 3D hero (`hero-webgl.tsx`) rendering a depth-mapped image with custom vertex/fragment shaders — the visual subtly responds to mouse movement for a holographic parallax effect.
- Alternate 3D hero component (`hero-3d.tsx`) and a standard layout fallback in `app/page.tsx`.
- Complete marketing sections: navbar, hero, features, technology, applications timeline, safety, testimonials, FAQ, CTA, footer.
- Extra legal pages: `/privacy`, `/terms`, `/cookies`.
- Client-side only — no backend, no API routes, no forms processing.

## Features

- Interactive WebGL 3D hero with custom GLSL shaders (react-three-fiber)
- Holographic depth-map parallax effect on the hero visual
- Responsive marketing sections: features, technology, applications timeline, safety, testimonials, FAQ, CTA
- Privacy / Terms / Cookies pages included
- Dark synth-tech aesthetic with Tailwind CSS
- Static export ready (`output: 'export'`) — deployable to any static host
- shadcn/ui components throughout

## Tech stack

- Next.js 15 (App Router, static export)
- React 19
- TypeScript
- three.js + @react-three/fiber + @react-three/drei (3D hero)
- Tailwind CSS 4
- shadcn/ui (Radix primitives)
- lucide-react icons

## Quick start

```bash
# install dependencies (pnpm or npm)
pnpm install
# or: npm install --legacy-peer-deps

# run the dev server
pnpm dev
# open http://localhost:3000

# production build (static export → ./out)
pnpm build

# serve the exported site locally
npx serve out
```

## Project structure

```
├── app/
│   ├── page.tsx            # assembles the landing page sections
│   ├── layout.tsx          # root layout
│   ├── globals.css         # global styles
│   ├── privacy/page.tsx    # privacy policy page
│   ├── terms/page.tsx      # terms page
│   └── cookies/page.tsx    # cookie policy page
├── components/
│   ├── hero-webgl.tsx      # WebGL 3D hero (custom shaders, depth-mapped image)
│   ├── hero-3d.tsx         # alternate 3D hero component
│   ├── navbar.tsx          # navigation bar
│   ├── features-section.tsx
│   ├── technology-section.tsx
│   ├── applications-section.tsx / applications-timeline.tsx
│   ├── safety-section.tsx
│   ├── testimonials-section.tsx
│   ├── faq-section.tsx
│   ├── cta-section.tsx
│   ├── footer.tsx
│   └── ui/                 # shadcn/ui primitives
├── lib/                    # shared utilities
├── public/                 # static assets
└── next.config.mjs         # static export + basePath configuration
```

## Configuration

`next.config.mjs` sets:

- `output: 'export'` — builds a fully static site into `out/`
- `basePath: '/neural-link-landingpage'` — required when served from the `girishlade111.github.io/neural-link-landingpage` GitHub Pages subpath. **Remove `basePath` (or point it at `/`) if deploying to a domain root or Vercel.**
- `images.unoptimized: true` — required for static export

Note: the 3D hero loads its texture/depth images from `i.postimg.cc` (external hotlink). If those URLs break, self-host the images in `public/` and update `TEXTUREMAP` / `DEPTHMAP` in `components/hero-webgl.tsx`.

## Environment variables

None required. The app is 100% client-side and calls no APIs.

## Deployment

- **GitHub Pages:** `pnpm build` → publish `out/` to the `gh-pages` branch. Live at `https://girishlade111.github.io/neural-link-landingpage/`
- **Vercel / Netlify / Cloudflare Pages:** push the repo and deploy as a Next.js/static site (set output directory to `out`). If deploying to a root domain, remove the `basePath` setting from `next.config.mjs` first.

## Credits

Built by Girish Lade — https://ladestack.in
