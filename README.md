import React, { Suspense, useRef, useEffect } from 'react';
import { Canvas, useFrame } from '@react-three/fiber';
import { Float, Html, OrbitControls, Text, PerspectiveCamera } from '@react-three/drei';
import { motion } from 'framer-motion';
import gsap from 'gsap';

// Single-file React component: Xmoney 3D Landing Page
// Requirements (install before use):
// npm install react react-dom @react-three/fiber @react-three/drei three framer-motion gsap
// Tailwind is optional — this file uses inline styles + small CSS block for simplicity.

// Notes: This file assumes you run it in a React app (Vite / CRA). It is intentionally self-contained
// and relies on simple THREE primitives (no external GLTF). The 3D scene is decorative and interactive,
// while the page contains real HTML CTAs linking to your Whop pages.

function FloatingCard({ x, y, z, title, price, link, desc }) {
  return (
    <Float floatIntensity={1.2} rotationIntensity={0.6} speed={2}>
      <mesh position={[x, y, z]}>
        <boxBufferGeometry args={[2.2, 1.3, 0.14]} />
        <meshStandardMaterial color={'#0f172a'} roughness={0.25} metalness={0.2} emissive={'#001f00'} emissiveIntensity={0.06} />
        <Html center distanceFactor={2.5} style={{ pointerEvents: 'auto' }}>
          <div style={{ width: 260, padding: 16, borderRadius: 12, background: 'linear-gradient(180deg, rgba(255,255,255,0.04), rgba(255,255,255,0.02))', border: '1px solid rgba(255,255,255,0.08)', color: '#e6eef2', fontFamily: 'Inter, Arial, sans-serif' }}>
            <h3 style={{ margin: 0, fontSize: 16, fontWeight: 700 }}>{title}</h3>
            <p style={{ margin: '8px 0', fontSize: 13, color: '#c9d6dd' }}>{desc}</p>
            <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
              <div style={{ fontWeight: 700 }}>${price}</div>
              <a href={link} target="_blank" rel="noreferrer" className="buy-link" style={{ textDecoration: 'none', padding: '8px 12px', borderRadius: 8, background: '#dc2626', color: 'white', fontWeight: 700 }}>
                BUY NOW
              </a>
            </div>
          </div>
        </Html>
      </mesh>
    </Float>
  );
}

function AnimatedLogo() {
  const ref = useRef();
  useFrame(({ clock }) => {
    const t = clock.getElapsedTime();
    if (ref.current) ref.current.rotation.y = Math.sin(t / 2) * 0.18;
  });
  return (
    <group ref={ref} position={[0, 1.8, -3]}>
      <mesh position={[-1.1, 0, 0]}>
        <sphereBufferGeometry args={[0.36, 36, 36]} />
        <meshStandardMaterial color={'#10b981'} metalness={0.6} roughness={0.15} emissive={'#063c2f'} emissiveIntensity={0.08} />
      </mesh>
      <Float floatIntensity={0.6} rotationIntensity={0.2}>
        <Text fontSize={0.6} maxWidth={3} lineHeight={0.9} letterSpacing={-0.02} anchorX="center" anchorY="middle">
          X
          <meshBasicMaterial attach="material" color="#06b6d4" />
        </Text>
      </Float>
    </group>
  );
}

function BackgroundSpheres() {
  // a few subtle spheres moving slowly
  const group = useRef();
  useFrame(({ clock }) => {
    if (!group.current) return;
    const t = clock.getElapsedTime();
    group.current.rotation.y = t / 20;
    for (let i = 0; i < group.current.children.length; i++) {
      const ch = group.current.children[i];
      ch.position.y = Math.sin(t / 2 + i) * 1.2;
    }
  });
  return (
    <group ref={group}>
      {[...Array(6)].map((_, i) => (
        <mesh key={i} position={[Math.cos(i) * (3 + i * 0.6), Math.sin(i) * (1 + i * 0.2), -5 - i * 0.6]}>
          <sphereBufferGeometry args={[0.9 - i * 0.08, 32, 32]} />
          <meshStandardMaterial color={i % 2 === 0 ? '#0ea5a4' : '#7c3aed'} roughness={0.6} metalness={0.2} emissive={'#00121a'} emissiveIntensity={0.02} />
        </mesh>
      ))}
    </group>
  );
}

function Scene() {
  return (
    <> 
      <ambientLight intensity={0.6} />
      <directionalLight intensity={0.6} position={[5, 10, 7]} />
      <Suspense fallback={null}>
        <BackgroundSpheres />
        <AnimatedLogo />

        {/* Three floating cards in 3D */}
        <FloatingCard x={-2.5} y={0.2} z={-2} title={'2 Logos for your business'} price={5} link={'https://whop.com/xmoney-1/xmoney-1c/'} desc={'Two polished logo variants (vector + PNG).'} />
        <FloatingCard x={0} y={-0.2} z={-1} title={'10 Business Ideas'} price={10} link={'https://whop.com/xmoney-1/xmoney-7e/'} desc={'Curated high-potential micro-business ideas.'} />
        <FloatingCard x={2.8} y={0.1} z={-2.2} title={'1 Video Edit — Pro'} price={10} link={'https://whop.com/xmoney-1/xmoney-b1/'} desc={'Social-ready pro video edit + captions.'} />

        <mesh rotation={[-Math.PI / 2, 0, 0]} position={[0, -2.5, -3]}> 
          <planeBufferGeometry args={[40, 40]} />
          <meshStandardMaterial color={'#001219'} roughness={1} metalness={0.05} />
        </mesh>
      </Suspense>
    </>
  );
}

export default function App() {
  const heroRef = useRef();

  useEffect(() => {
    // Entrance animations using GSAP
    gsap.from('.brandTitle', { y: -30, opacity: 0, duration: 0.9, ease: 'power3.out' });
    gsap.from('.subtitle', { y: 10, opacity: 0, delay: 0.2, duration: 0.9 });
    gsap.from('.card-html', { y: 30, opacity: 0, stagger: 0.12, delay: 0.35, duration: 0.9, ease: 'power2.out' });
  }, []);

  return (
    <div style={{ minHeight: '100vh', fontFamily: 'Inter, Arial, sans-serif', background: 'linear-gradient(180deg, #030712 0%, #071126 60%)', color: '#e6f0f2' }}>

      {/* 3D Canvas header */}
      <div style={{ position: 'relative', height: '72vh', width: '100%', overflow: 'hidden' }}>
        <Canvas style={{ background: 'transparent' }} camera={{ position: [0, 1.2, 6], fov: 50 }}>
          <PerspectiveCamera makeDefault position={[0, 1.2, 6]} />
          <OrbitControls enableZoom={false} enablePan={false} enableRotate={false} />
          <Scene />
        </Canvas>

        {/* Overlay HTML header */}
        <div style={{ position: 'absolute', top: 24, left: 32, right: 32, display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
          <div>
            <div className="brandTitle" style={{ fontSize: 44, fontWeight: 800, letterSpacing: '6px' }}>XMONEY</div>
            <div className="subtitle" style={{ marginTop: 4, color: '#9bd5d4' }}>Helping small businesses win</div>
          </div>

          <nav style={{ display: 'flex', gap: 18, alignItems: 'center' }}>
            <a href="#offers" style={{ color: '#cfeff0', textDecoration: 'none' }}>Offers</a>
            <a href="#about" style={{ color: '#cfeff0', textDecoration: 'none' }}>About</a>
            <a href="#contact" style={{ color: '#cfeff0', textDecoration: 'none' }}>Contact</a>
          </nav>
        </div>

        {/* CTA Buttons center */}
        <div style={{ position: 'absolute', left: '50%', transform: 'translateX(-50%)', bottom: 36, display: 'flex', gap: 12 }}>
          <motion.a whileHover={{ scale: 1.03 }} whileTap={{ scale: 0.98 }} href="#offers" style={{ background: '#06b6d4', padding: '12px 18px', borderRadius: 10, color: '#002d2f', fontWeight: 800, textDecoration: 'none' }}>See Offers</motion.a>
          <motion.a whileHover={{ scale: 1.03 }} whileTap={{ scale: 0.98 }} href="#contact" style={{ background: '#0ea5a4', padding: '12px 18px', borderRadius: 10, color: '#002d2f', fontWeight: 700, textDecoration: 'none' }}>Get Custom Package</motion.a>
        </div>
      </div>

      {/* OFFERS — HTML version of the 3 cards for accessibility */}
      <section id="offers" style={{ padding: '48px 24px', maxWidth: 1200, margin: '0 auto' }}>
        <h2 style={{ fontSize: 28, marginBottom: 8 }}>Our Offers</h2>
        <p style={{ color: '#bcd', marginBottom: 22 }}>Instant purchase — secure checkout via Whop. Prices shown are final.</p>

        <div style={{ display: 'flex', gap: 18, flexWrap: 'wrap' }}>

          <div className="card-html" style={{ flex: '1 1 320px', background: 'linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01))', padding: 18, borderRadius: 12, border: '1px solid rgba(255,255,255,0.06)' }}>
            <h3 style={{ marginTop: 0 }}>2 Logos for your Business</h3>
            <p style={{ color: '#cfe' }}>Two polished logo variants: vector + PNG. Delivery: 3–5 days.</p>
            <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginTop: 12 }}>
              <strong>$5</strong>
              <a className="buy-html" href="https://whop.com/xmoney-1/xmoney-1c/" target="_blank" rel="noreferrer" style={{ background: '#dc2626', padding: '10px 14px', color: 'white', borderRadius: 8, fontWeight: 800, textDecoration: 'none' }}>BUY NOW</a>
            </div>
          </div>

          <div className="card-html" style={{ flex: '1 1 320px', background: 'linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01))', padding: 18, borderRadius: 12, border: '1px solid rgba(255,255,255,0.06)' }}>
            <h3 style={{ marginTop: 0 }}>10 Business Ideas</h3>
            <p style={{ color: '#cfe' }}>A targeted list of ten business ideas with quick start steps and revenue model notes.</p>
            <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginTop: 12 }}>
              <strong>$10</strong>
              <a className="buy-html" href="https://whop.com/xmoney-1/xmoney-7e/" target="_blank" rel="noreferrer" style={{ background: '#dc2626', padding: '10px 14px', color: 'white', borderRadius: 8, fontWeight: 800, textDecoration: 'none' }}>BUY NOW</a>
            </div>
          </div>

          <div className="card-html" style={{ flex: '1 1 320px', background: 'linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01))', padding: 18, borderRadius: 12, border: '1px solid rgba(255,255,255,0.06)' }}>
            <h3 style={{ marginTop: 0 }}>1 Pro Video Edit</h3>
            <p style={{ color: '#cfe' }}>Professional edit designed for social conversions — captions, music, 1 revision included.</p>
            <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginTop: 12 }}>
              <strong>$10</strong>
              <a className="buy-html" href="https://whop.com/xmoney-1/xmoney-b1/" target="_blank" rel="noreferrer" style={{ background: '#dc2626', padding: '10px 14px', color: 'white', borderRadius: 8, fontWeight: 800, textDecoration: 'none' }}>BUY NOW</a>
            </div>
          </div>

        </div>
      </section>

      {/* ABOUT / SERVICES */}
      <section id="about" style={{ padding: '28px 24px', background: 'linear-gradient(180deg, rgba(3,6,23,0.2), transparent)' }}>
        <div style={{ maxWidth: 1000, margin: '0 auto' }}>
          <h2>About Xmoney</h2>
          <p style={{ color: '#cfe' }}>Xmoney helps small businesses grow with practical strategy, strong brand identity, and conversion-focused media. We blend design, marketing, and execution to get you customers fast.</p>

          <h3 style={{ marginTop: 18 }}>Services</h3>
          <ul style={{ color: '#cfe' }}>
            <li>Brand identity & logo suites</li>
            <li>Business idea validation & microservices</li>
            <li>Professional video edits for ads & social</li>
            <li>Landing pages & funnels (upgradeable)</li>
          </ul>
        </div>
      </section>

      {/* TESTIMONIALS */}
      <section style={{ padding: '28px 24px' }}>
        <div style={{ maxWidth: 900, margin: '0 auto' }}>
          <h2>Testimonials</h2>
          <div style={{ display: 'grid', gap: 12, gridTemplateColumns: '1fr 1fr', marginTop: 12 }}>
            <blockquote style={{ margin: 0, background: 'rgba(255,255,255,0.02)', padding: 12, borderRadius: 8 }}>
              "Xmoney redesigned our logo and sales doubled in 2 months." — Sara, bakery owner
            </blockquote>
            <blockquote style={{ margin: 0, background: 'rgba(255,255,255,0.02)', padding: 12, borderRadius: 8 }}>
              "The video edit converted better than our previous ads." — Mark, gym owner
            </blockquote>
          </div>
        </div>
      </section>

      {/* CONTACT */}
      <section id="contact" style={{ padding: '28px 24px', background: 'linear-gradient(180deg, transparent, rgba(3,6,23,0.18))' }}>
        <div style={{ maxWidth: 900, margin: '0 auto', display: 'flex', gap: 22, flexWrap: 'wrap' }}>
          <div style={{ flex: '1 1 360px' }}>
            <h3>Contact</h3>
            <p style={{ color: '#cfe' }}>Email us at <a href="mailto:hello@xmoney.example" style={{ color: '#9be' }}>hello@xmoney.example</a> for custom packages or collaborations.</p>
          </div>

          <form onSubmit={(e) => { e.preventDefault(); window.location.href = 'mailto:hello@xmoney.example?subject=Website%20Lead'; }} style={{ flex: '1 1 360px', display: 'flex', flexDirection: 'column', gap: 8 }}>
            <input required placeholder="Your name" style={{ padding: 10, borderRadius: 8, border: '1px solid rgba(255,255,255,0.06)', background: 'transparent', color: '#e6f0f2' }} />
            <input required type="email" placeholder="Email" style={{ padding: 10, borderRadius: 8, border: '1px solid rgba(255,255,255,0.06)', background: 'transparent', color: '#e6f0f2' }} />
            <textarea placeholder="Message" rows={4} style={{ padding: 10, borderRadius: 8, border: '1px solid rgba(255,255,255,0.06)', background: 'transparent', color: '#e6f0f2' }} />
            <button type="submit" style={{ padding: '10px 14px', background: '#06b6d4', color: '#022', fontWeight: 800, borderRadius: 8, border: 'none' }}>Send</button>
          </form>
        </div>
      </section>

      <footer style={{ padding: 20, textAlign: 'center', color: '#9bb' }}>© 2025 XMONEY — Built to help local businesses grow. Budget ready: $10,000 planning & implementation.</footer>

      {/* Small style block for hover color change for buy links */}
      <style>{`
        .buy-link:hover { background: #16a34a !important; }
        .buy-html:hover { background: #16a34a !important; }
        @media (max-width: 720px) { .brandTitle { font-size: 28px !important; } }
      `}</style>
    </div>
  );
}
