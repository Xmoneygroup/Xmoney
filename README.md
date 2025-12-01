[html code 1.txt](https://github.com/user-attachments/files/23858187/html.code.1.txt)
// File: app/dashboard/page.tsx – Modern Xmoney Dashboard with static galaxy background
export default function Dashboard() {
  return (
    <div className="relative min-h-screen bg-black text-white">
      {/* Static Galaxy Background */}
      <div
        className="absolute inset-0 -z-10 bg-cover bg-center"
        style={{ backgroundImage: "url('https://images.unsplash.com/photo-1610878180933-8d8398ffdd4f?auto=format&fit=crop&w=1470&q=80')" }}
      ></div>

      <div className="relative z-10 p-8 max-w-7xl mx-auto">
        <h1 className="text-5xl font-extrabold mb-6 text-center">Xmoney Dashboard</h1>
        <p className="text-xl text-center mb-12 max-w-2xl mx-auto">
          Welcome to the next level of business collaboration with <strong>Xmoney</strong>. Your membership unlocks exclusive tools and services designed to help your business grow.
        </p>

        {/* Options Grid */}
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
          {/* Option 1 – Logos */}
          <div className="bg-white bg-opacity-90 shadow-2xl rounded-3xl p-8 text-black hover:scale-105 transform transition duration-300">
            <h2 className="text-2xl font-bold mb-3">2 Professional Logos – $5</h2>
            <p className="mb-5">Get 2 custom logos to elevate your brand identity.</p>
            <a href="https://whop.com/checkout/plan_QOybDJlOSXgGn" target="_blank" rel="noopener noreferrer" className="inline-block bg-black text-white font-semibold px-6 py-3 rounded-xl w-full text-center hover:bg-gray-800 transition">
              Order Logos
            </a>
          </div>

          {/* Option 2 – Business Ideas */}
          <div className="bg-white bg-opacity-90 shadow-2xl rounded-3xl p-8 text-black hover:scale-105 transform transition duration-300">
            <h2 className="text-2xl font-bold mb-3">Business Ideas – $10</h2>
            <p className="mb-5">Receive unique business ideas and strategies to grow fast.</p>
            <a href="https://whop.com/checkout/plan_P7lCCHZ89ZLDj" target="_blank" rel="noopener noreferrer" className="inline-block bg-green-600 text-white font-semibold px-6 py-3 rounded-xl w-full text-center hover:bg-green-700 transition">
              Get Ideas
            </a>
          </div>

          {/* Option 3 – Premium Video */}
          <div className="bg-white bg-opacity-90 shadow-2xl rounded-3xl p-8 text-black hover:scale-105 transform transition duration-300">
            <h2 className="text-2xl font-bold mb-3">Premium Video Editing (20s) – $10</h2>
            <p className="mb-5">High-quality 20-second marketing video for your business.</p>
            <a href="https://whop.com/checkout/plan_KHyI8qQTLoyqk" target="_blank" rel="noopener noreferrer" className="inline-block bg-red-600 text-white font-semibold px-6 py-3 rounded-xl w-full text-center hover:bg-red-700 transition">
              Order Video
            </a>
          </div>
        </div>

        {/* Membership Section */}
        <div className="mt-16 bg-blue-900 bg-opacity-80 p-10 rounded-3xl text-center shadow-2xl hover:scale-105 transform transition duration-300">
          <h2 className="text-3xl font-bold mb-3">Xmoney Membership – $19.99 per business</h2>
          <p className="mb-5 text-lg">Unlock access to the full platform, including all tools, exclusive content, and priority support.</p>
          <a href="https://whop.com/checkout/plan_fenfmpRiZGQCn" target="_blank" rel="noopener noreferrer" className="inline-block bg-blue-600 text-white font-semibold px-8 py-4 rounded-xl text-lg hover:bg-blue-700 transition">
            Join Membership
          </a>
        </div>
      </div>
    </div>
  );
}
