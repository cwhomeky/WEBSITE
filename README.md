<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pro Realtor Universal Ad Studio</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- html2canvas -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <!-- Google Font Backup (Great Vibes - Modern Script Fallback for Adeptly) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
    <style>
        /* Format Dimensions */
        .format-feed { width: 450px; min-height: 450px; }
        .format-story { width: 360px; min-height: 640px; }
        .format-flyer { width: 450px; min-height: 580px; }
        
        /* Dynamic Theme Styles */
        .theme-dark { background-color: #0f172a !important; color: #f8fafc !important; }
        .theme-dark .card-bg { background-color: #1e293b !important; color: #f8fafc !important; }
        .theme-dark .text-muted { color: #94a3b8 !important; }
        
        .theme-light { background-color: #1e3a8a !important; color: #ffffff !important; }
        .theme-light .card-bg { background-color: #ffffff !important; color: #1e293b !important; }
        .theme-light .text-muted { color: #475569 !important; }

        /* Global Ad Body Font (Century Modern Serif Fallback Chain) */
        .century-body {
            font-family: 'CenturyCustom', 'Century Schoolbook', 'Century', 'Georgia', 'Cambria', serif;
        }

        /* Headline Script Font (Adeptly Fallback Chain) */
        .script-headline {
            font-family: 'AdeptlyCustom', 'Great Vibes', cursive, sans-serif;
        }

        /* Headshot Edge Smoothing & Dynamic Transform CSS */
        .headshot-smooth {
            filter: contrast(1.03) brightness(1.02);
            object-fit: cover;
            border-radius: 9999px;
            border: 2px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
        }

        .draggable-element {
            cursor: move;
            transition: transform 0.05s ease-out;
            user-select: none;
        }
    </style>
</head>
<body class="bg-slate-100 p-4 md:p-8 font-sans">

    <div class="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-12 gap-8">
        
        <!-- LEFT COLUMN: Universal Controls & Input Form (5 cols) -->
        <div class="lg:col-span-5 bg-white p-6 rounded-xl shadow-md space-y-4 max-h-[90vh] overflow-y-auto">
            <h2 class="text-2xl font-bold text-slate-800 border-b pb-2">Universal Ad Control Panel</h2>
            
            <!-- 1. Canvas Aspect Ratio & Themes -->
            <div class="space-y-2">
                <label class="block text-xs font-bold uppercase text-slate-500">1. Aspect Ratio & Theme</label>
                <div class="grid grid-cols-3 gap-2">
                    <button onclick="setFormat('feed')" class="py-2 text-xs font-bold border rounded-lg hover:bg-slate-50 focus:bg-blue-900 focus:text-white">Feed (1:1)</button>
                    <button onclick="setFormat('story')" class="py-2 text-xs font-bold border rounded-lg hover:bg-slate-50 focus:bg-blue-900 focus:text-white">Story (9:16)</button>
                    <button onclick="setFormat('flyer')" class="py-2 text-xs font-bold border rounded-lg hover:bg-slate-50 focus:bg-blue-900 focus:text-white">Flyer (8.5x11)</button>
                </div>
                <div class="grid grid-cols-2 gap-2 pt-1">
                    <button onclick="setTheme('light')" class="py-2 text-xs font-bold border rounded-lg bg-blue-900 text-white">Classic Navy</button>
                    <button onclick="setTheme('dark')" class="py-2 text-xs font-bold border rounded-lg bg-slate-900 text-white">Modern Dark</button>
                </div>
            </div>

            <!-- 2. Custom Fonts Engine -->
            <div class="space-y-2 border-t pt-2">
                <label class="block text-xs font-bold uppercase text-slate-500">2. Font File Uploads</label>
                <div class="grid grid-cols-2 gap-2">
                    <div>
                        <label class="block text-[10px] font-semibold text-slate-600">Headline (Adeptly)</label>
                        <input type="file" id="font-upload" accept=".otf,.ttf,.woff,.woff2" class="w-full text-xs text-slate-500 file:mr-1 file:py-1 file:px-2 file:rounded-md file:border-0 file:text-[10px] file:bg-blue-50">
                    </div>
                    <div>
                        <label class="block text-[10px] font-semibold text-slate-600">Body (Century)</label>
                        <input type="file" id="body-font-upload" accept=".otf,.ttf,.woff,.woff2" class="w-full text-xs text-slate-500 file:mr-1 file:py-1 file:px-2 file:rounded-md file:border-0 file:text-[10px] file:bg-blue-50">
                    </div>
                </div>
            </div>

            <!-- 3. MLS Auto-Fill Box -->
            <hr>
            <div class="bg-blue-50 p-3 rounded-lg border border-blue-200 space-y-2">
                <label class="block text-xs font-bold uppercase text-blue-900">⚡ MLS Import / Auto-Fill Box</label>
                <textarea id="mls-raw-input" rows="2" placeholder="Paste MLS details here..." class="w-full p-2 border rounded-lg text-xs bg-white"></textarea>
                <button onclick="parseMLSData()" class="w-full bg-blue-900 text-white py-1.5 rounded-lg font-bold hover:bg-blue-800 transition text-xs shadow-sm">
                    Auto-Populate Ad Fields
                </button>
            </div>

            <!-- 4. Element-by-Element Granular Adjuster -->
            <hr>
            <h3 class="text-xs font-bold uppercase text-slate-700">4. Granular Element Controls</h3>

            <!-- Badge Adjuster -->
            <div class="bg-slate-50 p-2.5 rounded-lg border border-slate-200 space-y-2">
                <div class="flex justify-between items-center">
                    <span class="text-xs font-bold text-slate-700">Status Badge</span>
                    <input type="text" id="input-badge" value="NEW LISTING" class="p-1 border rounded text-xs w-1/2">
                </div>
                <div class="grid grid-cols-3 gap-2 text-[10px]">
                    <div><span>Scale:</span><input type="range" id="badge-scale" min="50" max="200" value="100" class="w-full accent-blue-900"></div>
                    <div><span>Shift X:</span><input type="range" id="badge-x" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                    <div><span>Shift Y:</span><input type="range" id="badge-y" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                </div>
            </div>

            <!-- Headline Adjuster -->
            <div class="bg-slate-50 p-2.5 rounded-lg border border-slate-200 space-y-2">
                <div class="flex justify-between items-center">
                    <span class="text-xs font-bold text-slate-700">Headline</span>
                    <input type="text" id="input-headline" value="Your Dream Build Lot in Scenic LaRue County!" class="p-1 border rounded text-xs w-2/3">
                </div>
                <div class="grid grid-cols-3 gap-2 text-[10px]">
                    <div><span>Font Size:</span><input type="range" id="headline-scale" min="12" max="48" value="24" class="w-full accent-blue-900"></div>
                    <div><span>Shift X:</span><input type="range" id="headline-x" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                    <div><span>Shift Y:</span><input type="range" id="headline-y" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                </div>
            </div>

            <!-- Address Banner Adjuster (Blank by Default) -->
            <div class="bg-slate-50 p-2.5 rounded-lg border border-slate-200 space-y-2">
                <div class="flex justify-between items-center">
                    <span class="text-xs font-bold text-slate-700">Address Banner</span>
                    <input type="text" id="input-address" value="" placeholder="Type property address here..." class="p-1 border rounded text-xs w-2/3">
                </div>
                <div class="grid grid-cols-3 gap-2 text-[10px]">
                    <div><span>Font Size:</span><input type="range" id="address-scale" min="8" max="24" value="12" class="w-full accent-blue-900"></div>
                    <div><span>Shift X:</span><input type="range" id="address-x" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                    <div><span>Shift Y:</span><input type="range" id="address-y" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                </div>
            </div>

            <!-- Price & Specs Adjuster -->
            <div class="bg-slate-50 p-2.5 rounded-lg border border-slate-200 space-y-2">
                <div class="grid grid-cols-2 gap-2">
                    <input type="text" id="input-price" value="$49,000" class="p-1 border rounded text-xs">
                    <input type="text" id="input-acres" value="0.68 AC" class="p-1 border rounded text-xs">
                </div>
                <div class="grid grid-cols-3 gap-2 text-[10px]">
                    <div><span>Scale:</span><input type="range" id="specs-scale" min="50" max="200" value="100" class="w-full accent-blue-900"></div>
                    <div><span>Shift X:</span><input type="range" id="specs-x" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                    <div><span>Shift Y:</span><input type="range" id="specs-y" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                </div>
            </div>

            <!-- Photos Container Adjuster -->
            <div class="bg-slate-50 p-2.5 rounded-lg border border-slate-200 space-y-2">
                <label class="block text-xs font-bold text-slate-700">Main Photo Canvas Container</label>
                <input type="file" id="image-upload" accept="image/*" multiple class="w-full text-xs text-slate-500 file:mr-2 file:py-1 file:px-2 file:rounded-md file:border-0 file:text-[10px] file:bg-blue-50">
                <div id="image-list" class="flex flex-wrap gap-2 pt-1"></div>
                <div class="grid grid-cols-3 gap-2 text-[10px]">
                    <div><span>Container Height:</span><input type="range" id="photo-height" min="100" max="400" value="240" class="w-full accent-blue-900"></div>
                    <div><span>Active Scale:</span><input type="range" id="input-scale" min="10" max="300" value="100" class="w-full accent-blue-900"></div>
                    <div><span>Active Shift X:</span><input type="range" id="input-pos-x" min="-200" max="200" value="0" class="w-full accent-blue-900"></div>
                </div>
            </div>

            <!-- Description & Features Adjuster -->
            <div class="bg-slate-50 p-2.5 rounded-lg border border-slate-200 space-y-2">
                <span class="text-xs font-bold text-slate-700">Description Box</span>
                <textarea id="input-description" rows="2" class="w-full p-1 border rounded text-xs">Discover your opportunity to build the home of your dreams on this newly developed lot in Magnolia Fields!</textarea>
                <div class="grid grid-cols-3 gap-2 text-[10px]">
                    <div><span>Font Size:</span><input type="range" id="desc-scale" min="6" max="18" value="10" class="w-full accent-blue-900"></div>
                    <div><span>Shift X:</span><input type="range" id="desc-x" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                    <div><span>Shift Y:</span><input type="range" id="desc-y" min="-150" max="150" value="0" class="w-full accent-blue-900"></div>
                </div>
            </div>

            <!-- Section 4 Controls (Headshot, Contact, QR, Logo) -->
            <div class="bg-amber-50 p-3 rounded-lg border border-amber-200 space-y-3">
                <label class="block text-xs font-bold uppercase text-amber-900">Footer / Section 4 Adjuster</label>

                <!-- Headshot -->
                <div>
                    <label class="block text-[11px] font-bold text-amber-900">Headshot Image</label>
                    <input type="file" id="headshot-upload" accept="image/*" class="w-full text-xs text-slate-500 file:mr-1 file:py-0.5 file:px-2 file:border-0 file:text-[10px] file:bg-white">
                    <div class="grid grid-cols-3 gap-2 text-[10px] pt-1">
                        <div><span>Scale:</span><input type="range" id="input-hs-scale" min="10" max="300" value="100" class="w-full accent-amber-700"></div>
                        <div><span>Shift X:</span><input type="range" id="input-hs-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                        <div><span>Shift Y:</span><input type="range" id="input-hs-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                    </div>
                </div>

                <!-- Contact Text -->
                <div>
                    <label class="block text-[11px] font-bold text-amber-900">Contact Text Block</label>
                    <input type="text" id="input-agent" value="Patrick Washington | (216) 336-5533" class="w-full p-1 border rounded text-xs bg-white mb-1">
                    <input type="email" id="input-email" value="CWHOMEKY@GMAIL.COM" class="w-full p-1 border rounded text-xs bg-white mb-1">
                    <div class="grid grid-cols-3 gap-2 text-[10px]">
                        <div><span>Font Size:</span><input type="range" id="input-txt-size" min="8" max="24" value="12" class="w-full accent-amber-700"></div>
                        <div><span>Shift X:</span><input type="range" id="input-txt-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                        <div><span>Shift Y:</span><input type="range" id="input-txt-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                    </div>
                </div>

                <!-- QR Code -->
                <div>
                    <label class="block text-[11px] font-bold text-amber-900">QR Code</label>
                    <input type="file" id="qr-upload" accept="image/*" class="w-full text-xs text-slate-500 file:mr-1 file:py-0.5 file:px-2 file:border-0 file:text-[10px] file:bg-white mb-1">
                    <input type="text" id="input-qr-url" value="https://claudewashington.realtor/" class="w-full p-1 border rounded text-xs bg-white mb-1">
                    <div class="grid grid-cols-3 gap-2 text-[10px]">
                        <div><span>Scale:</span><input type="range" id="input-qr-scale" min="10" max="300" value="100" class="w-full accent-amber-700"></div>
                        <div><span>Shift X:</span><input type="range" id="input-qr-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                        <div><span>Shift Y:</span><input type="range" id="input-qr-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                    </div>
                </div>

                <!-- Brokerage Logo -->
                <div>
                    <label class="block text-[11px] font-bold text-amber-900">Brokerage Logo (PENNBLACK.png)</label>
                    <input type="file" id="logo-upload" accept="image/*" class="w-full text-xs text-slate-500 file:mr-1 file:py-0.5 file:px-2 file:border-0 file:text-[10px] file:bg-white mb-1">
                    <div class="grid grid-cols-3 gap-2 text-[10px]">
                        <div><span>Scale:</span><input type="range" id="input-logo-scale" min="10" max="300" value="100" class="w-full accent-amber-700"></div>
                        <div><span>Shift X:</span><input type="range" id="input-logo-pos-x" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                        <div><span>Shift Y:</span><input type="range" id="input-logo-pos-y" min="-150" max="150" value="0" class="w-full accent-amber-700"></div>
                    </div>
                </div>
            </div>

            <button onclick="downloadAd()" class="w-full bg-emerald-600 text-white py-3 rounded-lg font-bold hover:bg-emerald-700 transition text-sm shadow-md">
                Download High-Res Graphic (100% Free)
            </button>
        </div>

        <!-- RIGHT COLUMN: Interactive Live Canvas Preview (7 cols) -->
        <div class="lg:col-span-7 flex flex-col items-center justify-start min-h-[600px] bg-slate-200 p-6 rounded-xl border border-dashed border-slate-400">
            <span class="text-xs font-bold text-slate-500 uppercase tracking-wider mb-4">Live Interactive Canvas</span>
            
            <div id="ad-template" class="format-feed theme-light p-4 rounded-lg shadow-2xl flex flex-col justify-between text-center transition-all relative century-body overflow-hidden">
                
                <!-- Status Badge Wrapper -->
                <div id="badge-wrapper" class="flex justify-center draggable-element">
                    <span id="display-badge" class="bg-amber-400 text-slate-900 font-extrabold text-[10px] uppercase px-3 py-0.5 rounded-full shadow tracking-wider">NEW LISTING</span>
                </div>

                <!-- Headline Wrapper -->
                <div id="headline-wrapper" class="py-1 text-2xl tracking-wide leading-tight script-headline draggable-element">
                    Your Dream Build Lot in Scenic LaRue County!
                </div>

                <!-- Address Banner Wrapper (Blank by default) -->
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

                <!-- Description & Features Wrapper -->
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
                        <img id="display-headshot" src="https://via.placeholder.com/150x150?text=Headshot" class="w-full h-full headshot-smooth pointer-events-none" alt="Patrick Washington">
                    </div>

                    <!-- Contact Details Wrapper -->
                    <div id="contact-text-wrapper" class="text-left draggable-element">
                        <p class="text-[9px] opacity-80">Listed & Brokered by: Pennington Properties</p>
                        <p class="text-xs font-bold pt-0.5" id="display-agent">Call Patrick Washington at (216) 336-5533</p>
                        <p class="text-[10px] font-semibold text-blue-200" id="display-email">✉ CWHOMEKY@GMAIL.COM</p>
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
                    <img id="display-logo" src="https://via.placeholder.com/250x40?text=Pennington+Properties+Logo" class="max-h-8 max-w-[80%] object-contain pointer-events-none">
                </div>

            </div>
        </div>

    </div>

    <!-- JavaScript Engine -->
    <script>
        // Sync Basic Inputs
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
                        document.getElementById('ad-template').style.fontFamily = "'CenturyCustom', 'Century Schoolbook', 'Georgia', serif";
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
                wrapper.className = `relative h-full flex-1 overflow-hidden flex items-center justify-center cursor-move border rounded ${index === activeIndex ? 'ring-2 ring-blue-600' : ''}`;
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
                thumb.className = `w-10 h-10 object-cover rounded border-2 cursor-pointer ${index === activeIndex ? 'border-blue-900 scale-105' : 'border-slate-300 opacity-60'}`;
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
