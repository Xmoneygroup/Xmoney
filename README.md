// File: app/dashboard/page.tsx – Member Dashboard with moving galaxy background
export default function Dashboard() {
  return (
    <div className="relative min-h-screen overflow-hidden bg-black">
      {/* Galaxy Background */}
      <div className="absolute inset-0 -z-10">
        <div className="stars"></div>
        <div className="stars2"></div>
        <div className="stars3"></div>
      </div>

      <div className="p-6 relative z-10 text-white">
        <h1 className="text-4xl font-bold mb-6">Dashboard - Xmoney</h1>
        <p className="text-xl mb-6">
          Welcome to the next level of business collaboration with <strong>Xmoney</strong>. Your membership unlocks exclusive tools and services.
        </p>

        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div className="bg-white shadow-xl rounded-2xl p-6 text-black">
            <h2 className="text-2xl font-bold mb-2">2 Professional Logos – $5</h2>
            <p>Get 2 custom logos for your business.</p>
            <a href="https://whop.com/checkout/plan_QOybDJlOSXgGn" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-black text-white px-4 py-2 rounded-xl w-full text-center">Order Logos</a>
          </div>

          <div className="bg-white shadow-xl rounded-2xl p-6 text-black">
            <h2 className="text-2xl font-bold mb-2">Business Ideas – $10</h2>
            <p>Receive unique ideas to grow your business.</p>
            <a href="https://whop.com/checkout/plan_P7lCCHZ89ZLDj" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-green-600 text-white px-4 py-2 rounded-xl w-full text-center">Get Ideas</a>
          </div>

          <div className="bg-white shadow-xl rounded-2xl p-6 text-black">
            <h2 className="text-2xl font-bold mb-2">Premium Video Editing (20s) – $10</h2>
            <p>High-quality 20-second marketing video for your business.</p>
            <a href="https://whop.com/checkout/plan_KHyI8qQTLoyqk" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-red-600 text-white px-4 py-2 rounded-xl w-full text-center">Order Video</a>
          </div>
        </div>

        <div className="mt-10 p-6 bg-yellow-100 rounded-xl text-center text-black">
          <h2 className="text-2xl font-bold mb-2">Xmoney Membership – $19.99 per business</h2>
          <p>Unlock access to the full platform, including all tools and priority support.</p>
          <a href="https://whop.com/checkout/plan_fenfmpRiZGQCn" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-blue-600 text-white px-6 py-3 rounded-xl text-lg">Join Membership</a>
        </div>
      </div>

      {/* Galaxy Animation CSS */}
      <style jsx>{`
        .stars, .stars2, .stars3 {
          position: absolute;
          top: 0;
          left: 0;
          width: 200%;
          height: 200%;
          background-repeat: repeat;
          background-size: contain;
          animation: moveStars 100s linear infinite;
        }

        .stars {
          background-image: radial-gradient(white 1px, transparent 1px);
          animation-duration: 100s;
        }
        .stars2 {
          background-image: radial-gradient(white 2px, transparent 2px);
          animation-duration: 150s;
        }
        .stars3 {
          background-image: radial-gradient(white 3px, transparent 3px);
          animation-duration: 200s;
        }

        @keyframes moveStars {
          0% { transform: translate(0, 0); }
          100% { transform: translate(-50%, -50%); }
        }
      `}</style>
    </div>
  );
}
// File: app/dashboard/page.tsx – Member Dashboard with static galaxy background
export default function Dashboard() {
  return (
    <div className="relative min-h-screen bg-black">
      {/* Static Galaxy Background */}
      <div
        className="absolute inset-0 -z-10 bg-cover bg-center"
        style={{ backgroundImage: "url('https://images.unsplash.com/photo-1610878180933-8d8398ffdd4f?auto=format&fit=crop&w=1470&q=80')" }}
      ></div>

      <div className="p-6 relative z-10 text-white">
        <h1 className="text-4xl font-bold mb-6">Dashboard - Xmoney</h1>
        <p className="text-xl mb-6">
          Welcome to the next level of business collaboration with <strong>Xmoney</strong>. Your membership unlocks exclusive tools and services.
        </p>

        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div className="bg-white shadow-xl rounded-2xl p-6 text-black">
            <h2 className="text-2xl font-bold mb-2">2 Professional Logos – $5</h2>
            <p>Get 2 custom logos for your business.</p>
            <a href="https://whop.com/checkout/plan_QOybDJlOSXgGn" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-black text-white px-4 py-2 rounded-xl w-full text-center">Order Logos</a>
          </div>

          <div className="bg-white shadow-xl rounded-2xl p-6 text-black">
            <h2 className="text-2xl font-bold mb-2">Business Ideas – $10</h2>
            <p>Receive unique ideas to grow your business.</p>
            <a href="https://whop.com/checkout/plan_P7lCCHZ89ZLDj" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-green-600 text-white px-4 py-2 rounded-xl w-full text-center">Get Ideas</a>
          </div>

          <div className="bg-white shadow-xl rounded-2xl p-6 text-black">
            <h2 className="text-2xl font-bold mb-2">Premium Video Editing (20s) – $10</h2>
            <p>High-quality 20-second marketing video for your business.</p>
            <a href="https://whop.com/checkout/plan_KHyI8qQTLoyqk" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-red-600 text-white px-4 py-2 rounded-xl w-full text-center">Order Video</a>
          </div>
        </div>

        <div className="mt-10 p-6 bg-yellow-100 rounded-xl text-center text-black">
          <h2 className="text-2xl font-bold mb-2">Xmoney Membership – $19.99 per business</h2>
          <p>Unlock access to the full platform, including all tools and priority support.</p>
          <a href="https://whop.com/checkout/plan_fenfmpRiZGQCn" target="_blank" rel="noopener noreferrer" className="mt-4 inline-block bg-blue-600 text-white px-6 py-3 rounded-xl text-lg">Join Membership</a>
        </div>
      </div>
    </div>
  );
}
