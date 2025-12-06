[Xmoney html.txt](https://github.com/user-attachments/files/23990246/Xmoney.html.txt)
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

      {/* Galaxy animation styles */}
      <style jsx>{`
        .animated-galaxy {
          background: radial-gradient(circle at 20% 30%, #ff9ff3, transparent 25%),
                      radial-gradient(circle at 80% 70%, #feca57, transparent 25%),
                      radial-gradient(circle at 50% 50%, #48dbfb, transparent 25%);
          background-size: 400% 400%;
          animation: galaxyMove 20s linear infinite;
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
