<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CWHOMESKY | Real Estate & Marketing Studio</title>
  
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- html2canvas for instant ad rendering -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  
  <!-- Typography Backup -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Playfair+Display:ital,wght@0,600;0,800;1,400&family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">

  <style>
    body { font-family: 'Plus Jakarta Sans', sans-serif; }
    .serif-title { font-family: 'CenturyCustom', 'Playfair Display', 'Georgia', serif; }
    .script-headline { font-family: 'AdeptlyCustom', 'Great Vibes', cursive; }
    
    /* Format Presets */
    .format-feed { width: 420px; min-height: 420px; }
    .format-story { width: 340px; min-height: 600px; }
    .format-flyer { width: 420px; min-height: 540px; }

    /* Dynamic Theme Enengines */
    .theme-light { background-color: #0f172a !important; color: #ffffff !important; }
    .theme-light .card-bg { background-color: #ffffff !important; color: #0f172a !important; }
    
    .theme-dark { background-color: #020617 !important; color: #f8fafc !important; }
    .theme-dark .card-bg { background-color: #0f172a !important; color: #f8fafc !important; }

    .headshot-smooth {
      filter: contrast(1.03) brightness(1.02);
      object-fit: cover;
      border-radius: 9999px;
      border: 2px solid rgba(255, 255, 255, 0.4);
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
    }

    .draggable-element {
      cursor: move;
      user-select: none;
    }
  </style>
</head>
<body class="bg-slate-950 text-slate-100 antialiased selection:bg-amber-400 selection:text-slate-950">

  <!-- TOP NAVIGATION HEADER -->
  <header class="sticky top-0 z-50 backdrop-blur-md bg-slate-950/80 border-b border-slate-800/80">
    <div class="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <span class="text-2xl font-black tracking-tight text-white">CW<span class="text-amber-400">HOMESKY</span></span>
      </div>
      
      <nav class="hidden md:flex items-center gap-8 text-sm font-semibold text-slate-300">
        <a href="#about" class="hover:text-amber-400 transition">About</a>
        <a href="#featured" class="hover:text-amber-400 transition">Focus Areas</a>
        <a href="#studio" class="text-amber-400 font-bold hover:text-amber-300 transition flex items-center gap-1">
          <span>⚡ Ad Generator Studio</span>
        </a>
        <a href="#contact" class="hover:text-amber-400 transition">Contact</a>
      </nav>

      <div class="flex items-center gap-4">
        <a href="tel:5022308636" class="hidden sm:inline-block px-4 py-2 text-xs font-extrabold uppercase tracking-wider bg-amber-400 text-slate-950 rounded-full hover:bg-amber-300 transition shadow-lg shadow-amber-400/10">
          📞 (502) 230-8636
        </a>
      </div>
    </div>
  </header>

  <!-- HERO SECTION -->
  <section class="relative py-24 md:py-32 overflow-hidden bg-gradient-to-b from-slate-950 via-slate-900 to-slate-950">
    <div class="max-w-5xl mx-auto px-6 text-center relative z-10 space-y-6">
      <span class="px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-widest bg-amber-400/10 text-amber-400 border border-amber-400/20 inline-block">
        Elizabethtown & Regional Real Estate
      </span>
      <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight text-white leading-tight">
        Your Dedicated, Honest & Trustworthy <br class="hidden sm:inline"><span class="text-transparent bg-clip-text bg-gradient-to-r from-amber-200 via-amber-400 to-amber-500">Real Estate Partner</span>
      </h1>
      <p class="max-w-2xl mx-auto text-slate-400 text-base md:text-lg leading-relaxed">
        Providing tailored residential buying, selling, and full-service property management across Elizabethtown, Radcliff, and surrounding areas.
      </p>
      <div class="flex flex-wrap justify-center gap-4 pt-4">
        <a href="#contact" class="px-8 py-4 bg-amber-400 text-slate-950 font-bold rounded-xl hover:bg-amber-300 transition shadow-xl shadow-amber-400/20 text-sm">
          Get In Touch Today
        </a>
        <a href="#studio" class="px-8 py-4 bg-slate-800/80 hover:bg-slate-800 text-white font-bold rounded-xl border border-slate-700 transition text-sm">
          Open Marketing Studio
        </a>
      </div>
    </div>
  </section>

  <!-- MAIN CONTENT CONTAINER -->
  <main class="max-w-7xl mx-auto px-6 py-16 space-y-24">

    <!-- ABOUT SECTION -->
    <section id="about" class="grid grid-cols-1 md:grid-cols-12 gap-12 items-center">
      <div class="md:col-span-5 flex flex-col items-center">
        <div class="relative w-64 h-64 md:w-72 md:h-72 rounded-3xl overflow-hidden border-2 border-amber-400/30 shadow-2xl shadow-amber-500/10">
          <img id="agent-profile-photo" src="https://via.placeholder.com/400x400?text=Patrick+C.+Washington" alt="Patrick C. Washington" class="w-full h-full object-cover">
        </div>
        <label for="agent-photo-input" class="mt-4 px-4 py-2 bg-slate-900 border border-slate-800 hover:border-amber-400/50 rounded-lg text-xs font-bold text-slate-300 cursor-pointer transition">
          📷 Upload / Update Photo
        </label>
        <input type="file" id="agent-photo-input" accept="image/*" class="hidden" onchange="loadAgentPhoto(event)">
      </div>

      <div class="md:col-span-7 space-y-6">
        <h2 class="text-3xl font-extrabold text-white">Welcome to CWHOMESKY</h2>
        <p class="text-slate-400 leading-relaxed text-base">
          Whether you are looking to purchase your dream home, sell a property, or maximize the return on your investments through dedicated property management, we deliver personal, honest, and expert guidance at every single step.
        </p>
        <div class="grid grid-cols-2 gap-4 pt-2 text-sm font-semibold">
          <div class="p-4 rounded-xl bg-slate-900/60 border border-slate-800/80">
            <span class="block text-2xl font-bold text-amber-400 mb-1">Local</span>
            <span class="text-slate-400">Elizabethtown & Regional Knowledge</span>
          </div>
          <div class="p-4 rounded-xl bg-slate-900/60 border border-slate-800/80">
            <span class="block text-2xl font-bold text-amber-400 mb-1">Full-Service</span>
            <span class="text-slate-400">Buying, Selling & Management</span>
          </div>
        </div>
      </div>
    </section>

    <!-- FOCUS AREAS / SERVICES -->
    <section id="featured" class="space-y-12">
      <div class="text-center space-y-3">
        <h2 class="text-3xl font-extrabold text-white">Our Core Focus Areas</h2>
        <p class="text-slate-400 max-w-xl mx-auto text-sm">Comprehensive real estate solutions structured to protect your investments and streamline your transactions.</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div class="bg-slate-900/50 border border-slate-800 rounded-2xl p-6 space-y-4 hover:border-amber-400/30 transition">
          <div class="w-12 h-12 bg-amber-400/10 rounded-xl flex items-center justify-center text-amber-400 text-xl font-bold">🏡</div>
          <h3 class="text-xl font-bold text-white">Residential Real Estate</h3>
          <p class="text-slate-400 text-sm leading-relaxed">Guiding homeowners and buyers through smooth, transparent buying and selling processes.</p>
        </div>

        <div class="bg-slate-900/50 border border-slate-800 rounded-2xl p-6 space-y-4 hover:border-amber-400/30 transition">
          <div class="w-12 h-12 bg-amber-400/10 rounded-xl flex items-center justify-center text-amber-400 text-xl font-bold">🔑</div>
          <h3 class="text-xl font-bold text-white">Property Management</h3>
          <p class="text-slate-400 text-sm leading-relaxed">End-to-end unit maintenance, tenant coordination, and property turnaround solutions.</p>
        </div>

        <div class="bg-slate-900/50 border border-slate-800 rounded-2xl p-6 space-y-4 hover:border-amber-400/30 transition">
          <div class="w-12 h-12 bg-amber-400/10 rounded-xl flex items-center justify-center text-amber-400 text-xl font-bold">📈</div>
          <h3 class="text-xl font-bold text-white">Local Market Expertise</h3>
          <p class="text-slate-400 text-sm leading-relaxed">Data-backed valuation, strategic neighborhood insights, and market placement.</p>
        </div>
      </div>
    </section>

    <!-- INTERACTIVE AD GENERATOR STUDIO (FULL ENGINE INTEGRATED) -->
    <section id="studio" class="bg-slate-900/80 border border-amber-400/20 rounded-3xl p-6 md:p-10 space-y-8 backdrop-blur-xl shadow-2xl">
      <div class="border-b border-slate-800 pb-6 flex flex-wrap justify-between items-center gap-4">
        <div>
          <span class="text-xs font-extrabold uppercase tracking-widest text-amber-400">Pro Feature</span>
          <h2 class="text-2xl md:text-3xl font-black text-white">Real Estate Ad & Graphic Studio</h2>
        </div>
        <p class="text-slate-400 text-xs max-w-md">Instantly design, scale, auto-fill, and download crisp social media ad graphics directly in your browser.</p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
        
        <!-- LEFT: Control Controls (5 cols) -->
        <div class="lg:col-span-5 space-y-6 max-h-[85vh] overflow-y-auto pr-2 text-slate-200">
          
          <!-- 1. Canvas Aspect Ratio & Theme -->
          <div class="space-y-2">
            <label class="block text-xs font-bold uppercase text-amber-400">1. Select Aspect Ratio & Theme</label>
            <div class="grid grid-cols-3 gap-2">
              <button onclick="setFormat('feed')" class="py-2 text-xs font-bold border border-slate-700 bg-slate-950 rounded-lg hover:border-amber-400 focus:bg-amber-400 focus:text-slate-950">Feed (1:1)</button>
              <button onclick="setFormat('story')" class="py-2 text-xs font-bold border border-slate-700 bg-slate-950 rounded-lg hover:border-amber-400 focus:bg-amber-400 focus:text-slate-950">Story (9:16)</button>
              <button onclick="setFormat('flyer')" class="py-2 text-xs font-bold border border-slate-700 bg-slate-950 rounded-lg hover:border-amber-400 focus:bg-amber-400 focus:text-slate-950">Flyer (8.5x11)</button>
            </div>
            <div class="grid grid-cols-2 gap-2 pt-1">
              <button onclick="setTheme('light')" class="py-2 text-xs font-bold border border-slate-700 bg-slate-900 rounded-lg text-white hover:border-amber-400">Classic Navy</button>
              <button onclick="setTheme('dark')" class="py-2 text-xs font-bold border border-slate-700 bg-slate-950 rounded-lg text-slate-300 hover:border-amber-400">Modern Dark</button>
            </div>
          </div>

          <!-- 2. Font Upload Engines -->
          <div class="space-y-2 border-t border-slate-800 pt-3">
            <label class="block text-xs font-bold uppercase text-amber-400">2. Custom Fonts Upload</label>
            <div class="grid grid-cols-2 gap-2">
              <div>
                <label class="block text-[10px] font-semibold text-slate-400">Headline Font (Adeptly)</label>
                <input type="file" id="font-upload" accept=".otf,.ttf,.woff,.woff2" class="w-full text-xs text-slate-400 file:mr-1 file:py-1 file:px-2 file:rounded-md file:border-0 file:text-[10px] file:bg-slate-800 file:text-slate-200">
              </div>
              <div>
                <label class="block text-[10px] font-semibold text-slate-400">Body Font (Century)</label>
                <input type="file" id="body-font-upload" accept=".otf,.ttf,.woff,.woff2" class="w-full text-xs text-slate-400 file:mr-1 file:py-1 file:px-2 file:rounded-md file:border-0 file:text-[10px] file:bg-slate-800 file:text-slate-200">
              </div>
            </div>
          </div>

          <!-- 3. MLS Auto-Fill Box -->
          <div class="bg-slate-950/80 p-3.5 rounded-xl border border-amber-400/20 space-y-2">
            <label class="block text-xs font-bold uppercase text-amber-400">⚡ MLS Import / Auto-Fill Box</label>
            <textarea id="mls-raw-input" rows="2" placeholder="Paste raw MLS details here (e.g. Lot 12, Hodgenville, KY 42748. Price: $49,000, 0.68 Acres...)" class="w-full p-2 border border-slate-800 rounded-lg text-xs bg-slate-900 text-white"></textarea>
            <button onclick="parseMLSData()" class="w-full bg-amber-400 text-slate-950 py-2 rounded-lg font-bold hover:bg-amber-300 transition text-xs shadow-md">
              Auto-Populate Ad Fields
            </button>
          </div>

          <!-- 4. Granular Element Adjusters -->
          <div class="space-y-3 border-t border-slate-800 pt-3">
            <label class="block text-xs font-bold uppercase text-amber-400">3. Granular Element Controls</label>

            <!-- Badge -->
            <div class="bg-slate-950/60 p-2.5 rounded-lg border border-slate-800 space-y-1.5">
              <div class="flex justify-between items-center">
                <span class="text-xs font-bold">Status Badge</span>
                <input type="text" id="input-badge" value="NEW LISTING" class="p-1 border border-slate-800 rounded bg-slate-900 text-xs w-1/2">
              </div>
              <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                <div><span>Scale:</span><input type="range" id="badge-scale" min="50" max="200" value="100" class="w-full accent-amber-400"></div>
                <div><span>Shift X:</span><input type="range" id="badge-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                <div><span>Shift Y:</span><input type="range" id="badge-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
              </div>
            </div>

            <!-- Headline -->
            <div class="bg-slate-950/60 p-2.5 rounded-lg border border-slate-800 space-y-1.5">
              <div class="flex justify-between items-center">
                <span class="text-xs font-bold">Headline</span>
                <input type="text" id="input-headline" value="Your Dream Build Lot in Scenic LaRue County!" class="p-1 border border-slate-800 rounded bg-slate-900 text-xs w-2/3">
              </div>
              <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                <div><span>Font Size:</span><input type="range" id="headline-scale" min="12" max="48" value="24" class="w-full accent-amber-400"></div>
                <div><span>Shift X:</span><input type="range" id="headline-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                <div><span>Shift Y:</span><input type="range" id="headline-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
              </div>
            </div>

            <!-- Address Banner -->
            <div class="bg-slate-950/60 p-2.5 rounded-lg border border-slate-800 space-y-1.5">
              <div class="flex justify-between items-center">
                <span class="text-xs font-bold">Address Banner</span>
                <input type="text" id="input-address" value="" placeholder="Type property address here..." class="p-1 border border-slate-800 rounded bg-slate-900 text-xs w-2/3">
              </div>
              <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                <div><span>Font Size:</span><input type="range" id="address-scale" min="8" max="24" value="12" class="w-full accent-amber-400"></div>
                <div><span>Shift X:</span><input type="range" id="address-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                <div><span>Shift Y:</span><input type="range" id="address-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
              </div>
            </div>

            <!-- Price & Specs -->
            <div class="bg-slate-950/60 p-2.5 rounded-lg border border-slate-800 space-y-1.5">
              <div class="grid grid-cols-2 gap-2">
                <input type="text" id="input-price" value="$49,000" class="p-1 border border-slate-800 rounded bg-slate-900 text-xs">
                <input type="text" id="input-acres" value="0.68 AC" class="p-1 border border-slate-800 rounded bg-slate-900 text-xs">
              </div>
              <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                <div><span>Scale:</span><input type="range" id="specs-scale" min="50" max="200" value="100" class="w-full accent-amber-400"></div>
                <div><span>Shift X:</span><input type="range" id="specs-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                <div><span>Shift Y:</span><input type="range" id="specs-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
              </div>
            </div>

            <!-- Main Photos -->
            <div class="bg-slate-950/60 p-2.5 rounded-lg border border-slate-800 space-y-1.5">
              <label class="block text-xs font-bold">Main Photo Canvas Container</label>
              <input type="file" id="image-upload" accept="image/*" multiple class="w-full text-xs text-slate-400 file:mr-2 file:py-1 file:px-2 file:rounded-md file:border-0 file:text-[10px] file:bg-slate-800 file:text-slate-200">
              <div id="image-list" class="flex flex-wrap gap-2 pt-1"></div>
              <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                <div><span>Height:</span><input type="range" id="photo-height" min="100" max="400" value="240" class="w-full accent-amber-400"></div>
                <div><span>Active Scale:</span><input type="range" id="input-scale" min="10" max="300" value="100" class="w-full accent-amber-400"></div>
                <div><span>Shift X:</span><input type="range" id="input-pos-x" min="-200" max="200" value="0" class="w-full accent-amber-400"></div>
              </div>
            </div>

            <!-- Description -->
            <div class="bg-slate-950/60 p-2.5 rounded-lg border border-slate-800 space-y-1.5">
              <span class="text-xs font-bold">Description Box</span>
              <textarea id="input-description" rows="2" class="w-full p-1 border border-slate-800 rounded bg-slate-900 text-xs">Discover your opportunity to build the home of your dreams on this newly developed lot in Magnolia Fields!</textarea>
              <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                <div><span>Font Size:</span><input type="range" id="desc-scale" min="6" max="18" value="10" class="w-full accent-amber-400"></div>
                <div><span>Shift X:</span><input type="range" id="desc-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                <div><span>Shift Y:</span><input type="range" id="desc-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
              </div>
            </div>

            <!-- Footer / Section 4 Adjuster -->
            <div class="bg-slate-950/80 p-3 rounded-lg border border-amber-400/20 space-y-3">
              <label class="block text-xs font-bold uppercase text-amber-400">Footer / Section 4 Adjuster</label>

              <!-- Headshot -->
              <div>
                <label class="block text-[11px] font-bold text-slate-300">Headshot Image</label>
                <input type="file" id="headshot-upload" accept="image/*" class="w-full text-xs text-slate-400 file:mr-1 file:py-0.5 file:px-2 file:border-0 file:text-[10px] file:bg-slate-800">
                <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400 pt-1">
                  <div><span>Scale:</span><input type="range" id="input-hs-scale" min="10" max="300" value="100" class="w-full accent-amber-400"></div>
                  <div><span>Shift X:</span><input type="range" id="input-hs-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                  <div><span>Shift Y:</span><input type="range" id="input-hs-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                </div>
              </div>

              <!-- Contact Text -->
              <div>
                <label class="block text-[11px] font-bold text-slate-300">Contact Text Block</label>
                <input type="text" id="input-agent" value="Patrick C. Washington | (502) 230-8636" class="w-full p-1 border border-slate-800 rounded bg-slate-900 text-xs mb-1">
                <input type="email" id="input-email" value="cwhomeky@gmail.com" class="w-full p-1 border border-slate-800 rounded bg-slate-900 text-xs mb-1">
                <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                  <div><span>Font Size:</span><input type="range" id="input-txt-size" min="8" max="24" value="12" class="w-full accent-amber-400"></div>
                  <div><span>Shift X:</span><input type="range" id="input-txt-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                  <div><span>Shift Y:</span><input type="range" id="input-txt-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                </div>
              </div>

              <!-- QR Code -->
              <div>
                <label class="block text-[11px] font-bold text-slate-300">QR Code</label>
                <input type="file" id="qr-upload" accept="image/*" class="w-full text-xs text-slate-400 file:mr-1 file:py-0.5 file:px-2 file:border-0 file:text-[10px] file:bg-slate-800 mb-1">
                <input type="text" id="input-qr-url" value="https://claudewashington.realtor/" class="w-full p-1 border border-slate-800 rounded bg-slate-900 text-xs mb-1">
                <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                  <div><span>Scale:</span><input type="range" id="input-qr-scale" min="10" max="300" value="100" class="w-full accent-amber-400"></div>
                  <div><span>Shift X:</span><input type="range" id="input-qr-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                  <div><span>Shift Y:</span><input type="range" id="input-qr-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                </div>
              </div>

              <!-- Brokerage Logo -->
              <div>
                <label class="block text-[11px] font-bold text-slate-300">Brokerage Logo (PENNBLACK.png)</label>
                <input type="file" id="logo-upload" accept="image/*" class="w-full text-xs text-slate-400 file:mr-1 file:py-0.5 file:px-2 file:border-0 file:text-[10px] file:bg-slate-800 mb-1">
                <div class="grid grid-cols-3 gap-2 text-[10px] text-slate-400">
                  <div><span>Scale:</span><input type="range" id="input-logo-scale" min="10" max="300" value="100" class="w-full accent-amber-400"></div>
                  <div><span>Shift X:</span><input type="range" id="input-logo-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                  <div><span>Shift Y:</span><input type="range" id="input-logo-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-400"></div>
                </div>
              </div>
            </div>

          </div>

          <button onclick="downloadAd()" class="w-full bg-emerald-500 text-slate-950 py-3 rounded-xl font-bold hover:bg-emerald-400 transition text-sm shadow-xl shadow-emerald-500/10">
            Download High-Res Graphic (100% Free)
          </button>
        </div>

        <!-- RIGHT: Interactive Live Canvas Preview (7 cols) -->
        <div class="lg:col-span-7 flex flex-col items-center justify-start min-h-[550px] bg-slate-950/60 p-6 rounded-2xl border border-dashed border-slate-800">
          <span class="text-xs font-bold text-slate-500 uppercase tracking-widest mb-4">Live Interactive Canvas</span>
          
          <div id="ad-template" class="format-feed theme-light p-4 rounded-xl shadow-2xl flex flex-col justify-between text-center transition-all relative century-body overflow-hidden">
            
            <!-- Status Badge Wrapper -->
            <div id="badge-wrapper" class="flex justify-center draggable-element">
              <span id="display-badge" class="bg-amber-400 text-slate-950 font-extrabold text-[10px] uppercase px-3 py-0.5 rounded-full shadow tracking-wider">NEW LISTING</span>
            </div>

            <!-- Headline Wrapper -->
            <div id="headline-wrapper" class="py-1 text-2xl tracking-wide leading-tight script-headline draggable-element">
              Your Dream Build Lot in Scenic LaRue County!
            </div>

            <!-- Address Banner Wrapper -->
            <div id="address-wrapper" class="card-bg mx-2 py-1.5 px-3 rounded-md font-bold text-xs shadow-md tracking-wide draggable-element">
              <span id="display-address"></span>
            </div>

            <!-- Specs Wrapper -->
            <div id="specs-wrapper" class="flex justify-around my-2 text-[11px] font-bold draggable-element">
              <span class="bg-black/20 px-2.5 py-1 rounded shadow" id="display-price">💲 Price: $49,000</span>
              <span class="bg-black/20 px-2.5 py-1 rounded shadow" id="display-acres">📐 Size: 0.68 AC</span>
            </div>

            <!-- Main Photo Container -->
            <div id="image-container" class="w-full h-[240px] my-1 rounded-lg shadow-md overflow-hidden relative border-2 border-white/20 bg-white flex items-center justify-center gap-1 p-1">
              <span id="placeholder-text" class="text-xs font-semibold text-slate-400">Upload Photos Above</span>
            </div>

            <!-- Description Wrapper -->
            <div id="desc-wrapper" class="card-bg mx-1 my-2 p-2.5 rounded text-left text-[10px] leading-relaxed space-y-1.5 shadow draggable-element">
              <p id="display-description" class="text-slate-800">Discover your opportunity to build the home of your dreams on this newly developed lot in Magnolia Fields!</p>
              <div class="grid grid-cols-2 gap-1 font-semibold text-[10px] border-t border-slate-200/50 pt-1.5">
                <div>✔ Build-Ready Site</div>
                <div>✔ <span id="display-school">LaRue County Schools</span></div>
                <div>✔ Scenic Location</div>
                <div>✔ <span id="display-mls">MLS #1234567</span></div>
              </div>
            </div>

            <!-- Footer Section (Headshot, Contact, QR) -->
            <div class="flex items-center justify-between border-t border-white/10 pt-2 pb-2 px-1 gap-2 relative">
              <!-- Headshot Wrapper -->
              <div class="w-16 h-16 flex-shrink-0 flex items-center justify-center draggable-element" id="headshot-wrapper">
                <img id="display-headshot" src="https://via.placeholder.com/150x150?text=Headshot" class="w-full h-full headshot-smooth pointer-events-none" alt="Patrick C. Washington">
              </div>

              <!-- Contact Details Wrapper -->
              <div id="contact-text-wrapper" class="text-left draggable-element">
                <p class="text-[9px] opacity-80">CWHOMESKY Real Estate</p>
                <p class="text-xs font-bold pt-0.5" id="display-agent">Call Patrick C. Washington at (502) 230-8636</p>
                <p class="text-[10px] font-semibold text-blue-200" id="display-email">✉ cwhomeky@gmail.com</p>
              </div>

              <!-- QR Code Wrapper -->
              <div id="qr-wrapper" class="bg-white p-1 rounded-md shadow-md flex-shrink-0 ml-1 draggable-element">
                <a id="display-qr-link" href="https://claudewashington.realtor/" target="_blank" title="Click to Visit Website">
                  <img id="display-qr" src="https://api.qrserver.com/v1/create-qr-code/?size=300x300&data=https://claudewashington.realtor/" class="w-11 h-11 object-contain pointer-events-none" alt="Claude Washington Realtor QR Code">
                </a>
              </div>
            </div>

            <!-- Brokerage Logo Wrapper -->
            <div id="logo-wrapper" class="w-full flex justify-center items-center pb-1 pt-1 border-t border-white/10 mt-auto draggable-element">
              <img id="display-logo" src="https://via.placeholder.com/250x40?text=CWHOMESKY+Brokerage+Logo" class="max-h-8 max-w-[80%] object-contain pointer-events-none">
            </div>

          </div>
        </div>

      </div>
    </section>

    <!-- FORMSPREE CONTACT SECTION -->
    <section id="contact" class="max-w-2xl mx-auto bg-slate-900 border border-slate-800 p-8 md:p-10 rounded-3xl space-y-6 shadow-2xl">
      <div class="text-center space-y-2">
        <h2 class="text-3xl font-extrabold text-white">Contact Us Directly</h2>
        <p class="text-slate-400 text-sm">Send a direct message and we will respond promptly.</p>
      </div>

      <!-- FORMSPREE FORM -->
      <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST" class="space-y-4">
        <div>
          <label for="full-name" class="block text-xs font-bold uppercase text-slate-400 mb-1">Full Name</label>
          <input type="text" id="full-name" name="name" placeholder="John Doe" required class="w-full p-3 bg-slate-950 border border-slate-800 rounded-xl text-sm text-white focus:outline-none focus:border-amber-400">
        </div>

        <div>
          <label for="email-address" class="block text-xs font-bold uppercase text-slate-400 mb-1">Email Address</label>
          <input type="email" id="email-address" name="email" placeholder="name@example.com" required class="w-full p-3 bg-slate-950 border border-slate-800 rounded-xl text-sm text-white focus:outline-none focus:border-amber-400">
        </div>

        <div>
          <label for="phone-number" class="block text-xs font-bold uppercase text-slate-400 mb-1">Phone Number</label>
          <input type="tel" id="phone-number" name="phone" placeholder="(502) 230-8636" class="w-full p-3 bg-slate-950 border border-slate-800 rounded-xl text-sm text-white focus:outline-none focus:border-amber-400">
        </div>

        <div>
          <label for="message" class="block text-xs font-bold uppercase text-slate-400 mb-1">Message</label>
          <textarea id="message" name="message" rows="4" placeholder="How can we help you today?" required class="w-full p-3 bg-slate-950 border border-slate-800 rounded-xl text-sm text-white focus:outline-none focus:border-amber-400"></textarea>
        </div>

        <button type="submit" class="w-full py-4 bg-amber-400 text-slate-950 font-bold rounded-xl hover:bg-amber-300 transition text-sm shadow-xl shadow-amber-400/10">
          Send Direct Message
        </button>
      </form>
    </section>

  </main>

  <!-- FOOTER -->
  <footer class="border-t border-slate-900 bg-slate-950/90 py-12 text-center text-slate-400 text-sm space-y-3">
    <p class="font-extrabold text-white text-base">CWHOMESKY | Patrick C. Washington | Elizabethtown, KY</p>
    <p>
      Direct: <a href="tel:5022308636" class="text-amber-400 font-semibold hover:underline">502-230-8636</a> | <a href="tel:2163365533" class="text-amber-400 font-semibold hover:underline">(216) 336-5533</a>
    </p>
    <p>
      Email: <a href="mailto:cwhomeky@gmail.com" class="text-amber-400 font-semibold hover:underline">cwhomeky@gmail.com</a>
    </p>
    <p class="text-xs text-slate-600 pt-4">&copy; All Rights Reserved.</p>
  </footer>

  <!-- JAVASCRIPT ENGINE -->
  <script>
    // Agent Photo Loader
    function loadAgentPhoto(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = function(e) {
          document.getElementById('agent-profile-photo').src = e.target.result;
          document.getElementById('display-headshot').src = e.target.result;
        };
        reader.readAsDataURL(file);
      }
    }

    // Sync Basic Inputs to Ad Canvas
    const syncField = (inputId, displayId, prefix = '') => {
      const input = document.getElementById(inputId);
      if (input) {
        input.addEventListener('input', (e) => {
          document.getElementById(displayId).innerText = prefix + e.target.value;
        });
      }
    };

    syncField('input-badge', 'display-badge');
    syncField('input-headline', 'headline-wrapper');
    syncField('input-address', 'display-address');
    syncField('input-price', 'display-price', '💲 Price: ');
    syncField('input-acres', 'display-acres', '📐 Size: ');
    syncField('input-description', 'display-description');
    syncField('input-agent', 'display-agent', 'Call ');
    syncField('input-email', 'display-email', '✉ ');

    // MLS Auto-Fill Logic
    function parseMLSData() {
      const rawText = document.getElementById('mls-raw-input').value;
      if (!rawText.trim()) return;

      const lotMatch = rawText.match(/lot\s*#?\s*(\d+[A-Za-z]?)/i);
      const lotNum = lotMatch ? `Lot ${lotMatch[1]}` : 'Lot --';

      const cszMatch = rawText.match(/([A-Za-z\s]+),\s*([A-Z]{2})\s*(\d{5})/);
      let addressFormatted = lotNum;

      if (cszMatch) {
        addressFormatted = `${lotNum}, ${cszMatch[1].trim()}, ${cszMatch[2].trim()} ${cszMatch[3].trim()}`;
      }

      document.getElementById('input-address').value = addressFormatted;
      document.getElementById('display-address').innerText = addressFormatted;

      const priceMatch = rawText.match(/\$\s*[\d,]+/);
      if (priceMatch) {
        document.getElementById('input-price').value = priceMatch[0];
        document.getElementById('display-price').innerText = '💲 Price: ' + priceMatch[0];
      }

      const acresMatch = rawText.match(/(\d+(\.\d+)?)\s*(acres?|ac|sqft|sq\.?\s*ft)/i);
      if (acresMatch) {
        document.getElementById('input-acres').value = acresMatch[0].toUpperCase();
        document.getElementById('display-acres').innerText = '📐 Size: ' + acresMatch[0].toUpperCase();
      }

      if (rawText.length > 50) {
        document.getElementById('input-description').value = rawText.trim();
        document.getElementById('display-description').innerText = rawText.trim();
      }
    }

    // Generic Element Transform Engine
    function attachTransform(sliderScaleId, sliderXId, sliderYId, targetElementId, isFontSize = false) {
      let scale = isFontSize ? 12 : 100, x = 0, y = 0;
      const target = document.getElementById(targetElementId);

      const apply = () => {
        if (isFontSize) {
          target.style.fontSize = `${scale}px`;
          target.style.transform = `translate(${x}px, ${y}px)`;
        } else {
          target.style.transform = `translate(${x}px, ${y}px) scale(${scale / 100})`;
        }
      };

      document.getElementById(sliderScaleId).addEventListener('input', (e) => { scale = e.target.value; apply(); });
      document.getElementById(sliderXId).addEventListener('input', (e) => { x = e.target.value; apply(); });
      document.getElementById(sliderYId).addEventListener('input', (e) => { y = e.target.value; apply(); });

      // Mouse Drag Support
      let isDragging = false, startX, startY;
      target.addEventListener('mousedown', (e) => {
        isDragging = true;
        startX = e.clientX - x;
        startY = e.clientY - y;
        const onMouseMove = (moveEvent) => {
          if (!isDragging) return;
          x = moveEvent.clientX - startX;
          y = moveEvent.clientY - startY;
          document.getElementById(sliderXId).value = x;
          document.getElementById(sliderYId).value = y;
          apply();
        };
        const onMouseUp = () => {
          isDragging = false;
          window.removeEventListener('mousemove', onMouseMove);
          window.removeEventListener('mouseup', onMouseUp);
        };
        window.addEventListener('mousemove', onMouseMove);
        window.addEventListener('mouseup', onMouseUp);
      });
    }

    // Bind Controls to Template Elements
    attachTransform('badge-scale', 'badge-x', 'badge-y', 'badge-wrapper');
    attachTransform('headline-scale', 'headline-x', 'headline-y', 'headline-wrapper', true);
    attachTransform('address-scale', 'address-x', 'address-y', 'address-wrapper', true);
    attachTransform('specs-scale', 'specs-x', 'specs-y', 'specs-wrapper');
    attachTransform('desc-scale', 'desc-x', 'desc-y', 'desc-wrapper', true);
    attachTransform('input-hs-scale', 'input-hs-pos-x', 'input-hs-pos-y', 'headshot-wrapper');
    attachTransform('input-txt-size', 'input-txt-pos-x', 'input-txt-pos-y', 'contact-text-wrapper', true);
    attachTransform('input-qr-scale', 'input-qr-pos-x', 'input-qr-pos-y', 'qr-wrapper');
    attachTransform('input-logo-scale', 'input-logo-pos-x', 'input-logo-pos-y', 'logo-wrapper');

    // Photo Container Height Control
    document.getElementById('photo-height').addEventListener('input', (e) => {
      document.getElementById('image-container').style.height = `${e.target.value}px`;
    });

    // Font Upload Engines
    document.getElementById('font-upload').addEventListener('change', function(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = function(e) {
          const newFont = new FontFace('AdeptlyCustom', `url(${e.target.result})`);
          newFont.load().then(function(loadedFont) {
            document.fonts.add(loadedFont);
            document.getElementById('headline-wrapper').style.fontFamily = "'AdeptlyCustom', 'Great Vibes', cursive";
          });
        };
        reader.readAsDataURL(file);
      }
    });

    document.getElementById('body-font-upload').addEventListener('change', function(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = function(e) {
          const newFont = new FontFace('CenturyCustom', `url(${e.target.result})`);
          newFont.load().then(function(loadedFont) {
            document.fonts.add(loadedFont);
            document.getElementById('ad-template').style.fontFamily = "'CenturyCustom', 'Playfair Display', serif";
          });
        };
        reader.readAsDataURL(file);
      }
    });

    // Image Uploads (Headshot, QR, Logo)
    document.getElementById('headshot-upload').addEventListener('change', function(e) {
      if (e.target.files[0]) {
        const r = new FileReader(); r.onload = (ev) => { document.getElementById('display-headshot').src = ev.target.result; }; r.readAsDataURL(e.target.files[0]);
      }
    });
    document.getElementById('qr-upload').addEventListener('change', function(e) {
      if (e.target.files[0]) {
        const r = new FileReader(); r.onload = (ev) => { document.getElementById('display-qr').src = ev.target.result; }; r.readAsDataURL(e.target.files[0]);
      }
    });
    document.getElementById('logo-upload').addEventListener('change', function(e) {
      if (e.target.files[0]) {
        const r = new FileReader(); r.onload = (ev) => { document.getElementById('display-logo').src = ev.target.result; }; r.readAsDataURL(e.target.files[0]);
      }
    });

    // Multi-Image Gallery Manager
    let imagesData = [];
    let activeIndex = -1;
    const imageContainer = document.getElementById('image-container');
    const imageList = document.getElementById('image-list');

    document.getElementById('image-upload').addEventListener('change', function(event) {
      const files = Array.from(event.target.files);
      files.forEach(file => {
        const reader = new FileReader();
        reader.onload = function(e) {
          imagesData.push({ id: Date.now() + Math.random(), src: e.target.result, scale: 100, x: 0, y: 0 });
          activeIndex = imagesData.length - 1;
          renderCanvasImages();
          renderThumbnails();
        };
        reader.readAsDataURL(file);
      });
    });

    function renderCanvasImages() {
      imageContainer.innerHTML = '';
      if (imagesData.length === 0) {
        imageContainer.innerHTML = '<span class="text-xs font-semibold text-slate-400">Upload Photos Above</span>';
        return;
      }
      imagesData.forEach((data, index) => {
        const wrapper = document.createElement('div');
        wrapper.className = `relative h-full flex-1 overflow-hidden flex items-center justify-center cursor-move border rounded ${index === activeIndex ? 'ring-2 ring-amber-400' : ''}`;
        const imgEl = document.createElement('img');
        imgEl.src = data.src;
        imgEl.className = 'max-w-full max-h-full object-contain pointer-events-none';
        imgEl.style.transform = `translate(${data.x}px, ${data.y}px) scale(${data.scale / 100})`;
        wrapper.appendChild(imgEl);
        imageContainer.appendChild(wrapper);
      });
    }

    function renderThumbnails() {
      imageList.innerHTML = '';
      imagesData.forEach((data, index) => {
        const thumb = document.createElement('img');
        thumb.src = data.src;
        thumb.className = `w-10 h-10 object-cover rounded border-2 cursor-pointer ${index === activeIndex ? 'border-amber-400 scale-105' : 'border-slate-800 opacity-60'}`;
        thumb.onclick = () => { activeIndex = index; renderCanvasImages(); renderThumbnails(); };
        imageList.appendChild(thumb);
      });
    }

    // Format & Theme Switching
    function setFormat(format) {
      const template = document.getElementById('ad-template');
      template.classList.remove('format-feed', 'format-story', 'format-flyer');
      template.classList.add(`format-${format}`);
    }

    function setTheme(theme) {
      const template = document.getElementById('ad-template');
      template.classList.remove('theme-light', 'theme-dark');
      template.classList.add(`theme-${theme}`);
    }

    // High-Res PNG Download
    function downloadAd() {
      const element = document.getElementById('ad-template');
      html2canvas(element, { scale: 3 }).then(canvas => {
        const link = document.createElement('a');
        link.download = 'real-estate-ad.png';
        link.href = canvas.toDataURL('image/png');
        link.click();
      });
    }
  </script>
</body>
</html>
