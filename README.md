import React from 'react';

// Xmoney Landing Page
// Single-file React component (default export) using Tailwind CSS utility classes.
// To use:
// 1) Create a React app (Vite / CRA) with Tailwind installed.
// 2) Drop this file in src/App.jsx and ensure Tailwind is configured.
// 3) Start the dev server. This file is self-contained and uses no external images.

export default function App() {
  return (
    <div className="min-h-screen relative overflow-hidden font-sans">
      {/* Animated background: moving gradient + subtle diagonal lines */}
      <div aria-hidden className="fixed inset-0 -z-10 animate-bgSlow">
        <div className="absolute inset-0 bg-gradient-to-r from-indigo-900 via-slate-900 to-emerald-900 opacity-80" />
        <svg className="absolute inset-0 w-full h-full" preserveAspectRatio="none">
          <defs>
            <pattern id="p" width="40" height="40" patternUnits="userSpaceOnUse" patternTransform="rotate(20)">
              <line x1="0" y="0" x2="0" y2="40" strokeOpacity="0.02" strokeWidth="2" stroke="#ffffff" />
            </pattern>
          </defs>
          <rect width="100%" height="100%" fill="url(#p)" />
        </svg>
      </div>

      {/* Top nav / hero */}
      <header className="pt-12 pb-6 px-6 sm:px-12 lg:px-24">
        <nav className="flex items-center justify-between">
          <div className="flex items-center gap-4">
            {/* Big animated Xmoney logo text */}
            <h1 className="text-white text-5xl sm:text-6xl lg:text-7xl font-extrabold tracking-tight leading-none hero-logo" aria-label="Xmoney">
              X<span className="mx-1">MONEY</span>
            </h1>
            <p className="text-sm text-emerald-200 hidden md:block ml-4">Helping small businesses win</p>
          </div>

          <div className="flex items-center gap-4">
            <a href="#offers" className="text-white/90 hover:text-white transition">Offers</a>
            <a href="#contact" className="text-white/80 hover:text-white transition">Contact</a>
          </div>
        </nav>
      </header>

      {/* Intro blurb with thin entering animation */}
      <main className="px-6 sm:px-12 lg:px-24">
        <section className="max-w-4xl">
          <p className="mt-6 text-slate-200 text-lg sm:text-xl leading-relaxed intro-text">
            Xmoney helps small businesses grow with high-impact branding, practical business ideas, and professional video edits — all designed for measurable results.
            We combine design, strategy and conversion-focused delivery. Explore the offers below and buy instantly.
          </p>
        </section>

        {/* Cards / Pllakat */}
        <section id="offers" className="mt-12 grid gap-8 grid-cols-1 md:grid-cols-3">

          {/* Card 1 - 2 Logos + Buy button */}
          <article className="offer-card p-6 rounded-2xl backdrop-blur-md bg-white/6 border border-white/6 shadow-lg">
            <h2 className="text-xl font-semibold text-white">2 Logos for your business</h2>
            <p className="mt-2 text-sm text-slate-300">Two polished logo variants (vector + PNG). Ready for web, socials, and print.</p>

            <div className="mt-4 flex gap-4 items-center">
              {/* Placeholder logo 1 */}
              <div className="w-20 h-20 rounded-md bg-white/8 flex items-center justify-center">
                <svg width="60" height="60" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <rect x="10" y="10" width="80" height="80" rx="14" fill="white" fillOpacity="0.06" />
                  <text x="50" y="58" textAnchor="middle" fontFamily="sans-serif" fontSize="28" fill="#fff" fillOpacity="0.9">XM</text>
                </svg>
              </div>

              {/* Placeholder logo 2 */}
              <div className="w-20 h-20 rounded-md bg-white/8 flex items-center justify-center">
                <svg width="60" height="60" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <circle cx="50" cy="50" r="36" fill="white" fillOpacity="0.06" />
                  <text x="50" y="58" textAnchor="middle" fontFamily="sans-serif" fontSize="28" fill="#fff" fillOpacity="0.9">X</text>
                </svg>
              </div>

              <div className="ml-auto text-sm text-slate-300">Price: <span className="font-semibold text-white">$5</span></div>
            </div>

            <div className="mt-6 flex items-center gap-4">
              <a
                href="https://whop.com/xmoney-1/xmoney-1c/"
                target="_blank"
                rel="noopener noreferrer"
                className="buy-btn inline-block px-5 py-3 rounded-lg text-white font-medium shadow hover:scale-105 transition-transform"
                aria-label="Buy 2 logos for $5"
              >
                Buy now — $5
              </a>

              <a href="#details" className="text-sm text-emerald-200 hover:underline">More details</a>
            </div>
          </article>

          {/* Card 2 - 10 business ideas */}
          <article className="offer-card p-6 rounded-2xl backdrop-blur-md bg-white/6 border border-white/6 shadow-lg">
            <h2 className="text-xl font-semibold text-white">10 Business Ideas for You</h2>
            <p className="mt-2 text-sm text-slate-300">A curated list of ten realistic, high-potential micro-business ideas tailored for local markets.</p>

            <ul className="mt-4 grid gap-2 text-slate-300 text-sm">
              <li>• Local delivery micro-service</li>
              <li>• Niche product subscription</li>
              <li>• Social-media content package</li>
            </ul>

            <div className="mt-6 flex items-center gap-4">
              <a
                href="https://whop.com/xmoney-1/xmoney-7e/"
                target="_blank"
                rel="noopener noreferrer"
                className="buy-btn inline-block px-5 py-3 rounded-lg text-white font-medium shadow hover:scale-105 transition-transform"
                aria-label="Buy 10 business ideas for $10"
              >
                Buy now — $10
              </a>

              <a href="#why" className="text-sm text-emerald-200 hover:underline">Why these ideas?</a>
            </div>
          </article>

          {/* Card 3 - Video editing */}
          <article className="offer-card p-6 rounded-2xl backdrop-blur-md bg-white/6 border border-white/6 shadow-lg">
            <h2 className="text-xl font-semibold text-white">1 Video Edit — Pro Quality</h2>
            <p className="mt-2 text-sm text-slate-300">Professional video editing for your business: social cutdowns, captioning and conversion-first edits.</p>

            <div className="mt-4 flex items-center gap-4">
              <div className="w-20 h-12 rounded-md bg-white/8 flex items-center justify-center text-sm text-slate-200">1:00</div>
              <div className="ml-auto text-sm text-slate-300">Price: <span className="font-semibold text-white">$10</span></div>
            </div>

            <div className="mt-6 flex items-center gap-4">
              <a
                href="https://whop.com/xmoney-1/xmoney-b1/"
                target="_blank"
                rel="noopener noreferrer"
                className="buy-btn inline-block px-5 py-3 rounded-lg text-white font-medium shadow hover:scale-105 transition-transform"
                aria-label="Buy 1 professional video edit for $10"
              >
                Buy now — $10
              </a>

              <a href="#portfolio" className="text-sm text-emerald-200 hover:underline">See portfolio</a>
            </div>
          </article>

        </section>

        {/* Footer / contact */}
        <footer id="contact" className="mt-16 py-8 text-slate-300">
          <div className="max-w-4xl"> 
            <p>Need custom packages or brand strategy? Email <a href="mailto:hello@xmoney.example" className="text-emerald-200 underline">hello@xmoney.example</a></p>
            <p className="mt-3 text-sm">Budget set: <strong>$10,000</strong> — this sample landing page is built to be upgraded into a full marketing site, funnel, and analytics setup within that budget.</p>
          </div>
        </footer>

      </main>

      {/* Small helper: floating CTA */}
      <div className="fixed right-6 bottom-6">
        <a href="#offers" className="px-4 py-3 rounded-full bg-white/6 border border-white/8 text-white shadow-lg backdrop-blur hover:scale-105 transition">See offers</a>
      </div>

      {/* Styles local to this component - Tailwind + custom animations */}
      <style jsx>{`
        /* hero logo thin entry and letter animation */
        .hero-logo {
          font-family: Inter, ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
          -webkit-font-smoothing: antialiased;
          animation: logoEnter 1s ease forwards;
          letter-spacing: -0.02em;
          font-weight: 800;
        }

        .hero-logo span { font-weight: 700; }

        @keyframes logoEnter {
          0% { transform: translateY(-8px) scale(0.98); filter: blur(6px); opacity: 0; }
          100% { transform: translateY(0) scale(1); filter: blur(0); opacity: 1; }
        }

        /* Intro text thin-style */
        .intro-text { font-weight: 300; opacity: 0; transform: translateY(8px); animation: introUp 1s 0.25s ease forwards; }
        @keyframes introUp { to { opacity: 1; transform: translateY(0); } }

        /* Animated background slow pan */
        @keyframes bgSlow {
          0% { transform: translateX(-10%); }
          50% { transform: translateX(10%); }
          100% { transform: translateX(-10%); }
        }
        .animate-bgSlow { animation: bgSlow 30s linear infinite; }

        /* Card hover */
        .offer-card { transition: transform 220ms ease, box-shadow 220ms ease, background-color 220ms ease; }
        .offer-card:hover { transform: translateY(-8px) scale(1.01); box-shadow: 0 18px 40px rgba(2,6,23,0.6); }

        /* Buy button: red by default, green on hover */
        .buy-btn { background-color: #dc2626; /* red-600 */ }
        .buy-btn:hover { background-color: #16a34a; /* green-600 */ }

        /* Accessible focus state */
        .buy-btn:focus { outline: 3px solid rgba(99,102,241,0.18); outline-offset: 3px; }

      `}</style>
    </div>
  );
}
