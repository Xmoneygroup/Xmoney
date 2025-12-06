[Xmoney html.txt](https://github.com/user-attachments/files/23989992/Xmoney.html.txt)
// File: app/dashboard/page.tsx – Member Dashboard with animated galaxy background
export default function Dashboard() {
  return (
    <div className="relative min-h-screen overflow-hidden">
      {/* Animated Galaxy Background */}
      <div className="absolute inset-0 -z-10">
        <div className="animated-galaxy w-full h-full"></div>
      </div>

      <div className="p-6 relative z-10">
        <h1 className="text-4xl font-bold mb-6 text-white">Dashboard - Xmoney</h1>
        <p className="text-xl mb-6 text-white">
          Welcome to the next level of business collaboration with <strong>Xmoney</strong>. Your membership unlocks exclusive tools and services.
        </p>

        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          {/* TABLE 1 – 2 Logo Designs */}
          <div className="bg-white shadow-xl rounded-2xl p-6">
            <h2 className="text-2xl font-bold mb-2">2 Professional Logos – $5</h2>
            <p>Get 2 custom logos for your business.</p>
            <a href="https://whop.com/checkout/plan_QOybDJlOSXgGn" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-black text-white px-4 py-2 rounded-xl w-full text-center">Order Logos</a>
          </div>

          {/* TABLE 2 – Business Ideas */}
          <div className="bg-white shadow-xl rounded-2xl p-6">
            <h2 className="text-2xl font-bold mb-2">Business Ideas – $10</h2>
            <p>Receive unique ideas to grow your business.</p>
            <a href="https://whop.com/checkout/plan_P7lCCHZ89ZLDj" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-green-600 text-white px-4 py-2 rounded-xl w-full text-center">Get Ideas</a>
          </div>

          {/* TABLE 3 – Premium Video Editing */}
          <div className="bg-white shadow-xl rounded-2xl p-6">
            <h2 className="text-2xl font-bold mb-2">Premium Video Editing (20s) – $10</h2>
            <p>High-quality 20-second marketing video for your business.</p>
            <a href="https://whop.com/checkout/plan_KHyI8qQTLoyqk" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-red-600 text-white px-4 py-2 rounded-xl w-full text-center">Order Video</a>
          </div>
        </div>

        {/* Membership section */}
        <div className="mt-10 p-6 bg-yellow-100 rounded-xl text-center">
          <h2 className="text-2xl font-bold mb-2">Xmoney Membership – $19.99 per business</h2>
          <p>Unlock access to the full platform, including all tools and priority support.</p>
          <a href="https://whop.com/checkout/plan_fenfmpRiZGQCn" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-blue-600 text-white px-6 py-3 rounded-xl text-lg">Join Membership</a>
        </div>
      </div>

      <style jsx>{`
  .animated-galaxy {
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at 50% 50%, #ff0080, #7928ca, #2d2dff);
    background-size: 200% 200%;
    filter: blur(2px);
    animation: neonSmoke 8s ease-in-out infinite alternate;
  }

  @keyframes neonSmoke {
    0% { background-position: 30% 30%; }
    50% { background-position: 70% 60%; }
    100% { background-position: 30% 70%; }
  }
`}</style>

        }

        @keyframes galaxyMove {
          0% { background-position: 0% 0%, 100% 100%, 50% 50%; }
          50% { background-position: 100% 50%, 0% 100%, 50% 0%; }
          100% { background-position: 0% 0%, 100% 100%, 50% 50%; }
        }
      `}</style>
    </div>
  );
}
