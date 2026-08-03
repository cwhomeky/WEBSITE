<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CWHOMESKY | Patrick C. Washington - Modern Real Estate</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;700;800&family=Montserrat:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        body { 
            font-family: 'Montserrat', sans-serif; 
            background-color: #0f172a; 
            color: #f8fafc; 
        }
        .font-luxury { 
            font-family: 'Cinzel', serif; 
        }
        .glass-card { 
            background: rgba(30, 41, 59, 0.7); 
            backdrop-filter: blur(12px); 
            border: 1px solid rgba(255, 255, 255, 0.1); 
        }
        .headshot-smooth { 
            filter: contrast(1.03) brightness(1.02); 
            object-fit: cover; 
            border-radius: 9999px; 
            border: 2px solid rgba(212, 175, 55, 0.5); 
            box-shadow: 0 10px 25px -3px rgba(0, 0, 0, 0.5); 
            transition: transform 0.05s ease-out;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between">

    <!-- NAVIGATION HEADER -->
    <header class="sticky top-0 z-50 glass-card border-b border-slate-700/50 px-6 py-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <div class="flex items-center gap-3">
                <span class="font-luxury text-2xl font-bold tracking-widest text-amber-400">CWHOMESKY</span>
                <span class="text-xs text-slate-400 hidden sm:inline-block border-l border-slate-600 pl-3">Patrick C. Washington</span>
            </div>
            <nav class="flex items-center gap-6 text-sm font-semibold">
                <a href="#about" class="hover:text-amber-400 transition">About</a>
                <a href="#services" class="hover:text-amber-400 transition">Focus Areas</a>
                <a href="#contact" class="hover:text-amber-400 transition">Contact</a>
                <a href="tel:5022308636" class="bg-amber-500 text-slate-950 px-4 py-2 rounded-full font-bold hover:bg-amber-400 transition shadow-lg text-xs">
                    📞 (502) 230-8636
                </a>
            </nav>
        </div>
    </header>

    <!-- HERO SECTION -->
    <section class="relative py-20 px-6 text-center bg-gradient-to-b from-slate-900 to-slate-950 overflow-hidden">
        <div class="max-w-4xl mx-auto relative z-10">
            <span class="text-amber-400 text-xs font-bold tracking-widest uppercase mb-2 block">Dedicated • Trustworthy • Honest</span>
            <h1 class="font-luxury text-4xl md:text-6xl font-extrabold text-white leading-tight mb-6">
                Your Premier Real Estate & Property Partner
            </h1>
            <p class="text-slate-300 text-base md:text-lg mb-8 max-w-2xl mx-auto font-light">
                Delivering tailored real estate transactions, local valuation expertise, and full-service property solutions across Elizabethtown and surrounding Kentucky areas.
            </p>
            <div class="flex justify-center">
                <a href="#contact" class="bg-amber-500 text-slate-950 px-8 py-3 rounded-lg font-bold hover:bg-amber-400 transition shadow-xl text-sm">
                    Get In Touch Today
                </a>
            </div>
        </div>
    </section>

    <!-- ABOUT SECTION WITH PHOTO SHOWCASE & SLIDERS -->
    <section id="about" class="py-16 px-6 max-w-7xl mx-auto w-full">
        <div class="grid grid-cols-1 md:grid-cols-12 gap-12 items-center">
            
            <!-- Headshot Display + Positioning Controls -->
            <div class="md:col-span-5 flex flex-col items-center">
                <div class="relative w-64 h-64 flex items-center justify-center overflow-hidden mb-4">
                    <img id="main-agent-photo" src="https://via.placeholder.com/300x300?text=Upload+Headshot" class="w-full h-full headshot-smooth" alt="Patrick C. Washington">
                </div>
                
                <!-- Live Photo Scale & Position Controls -->
                <div class="glass-card p-4 rounded-xl w-full space-y-3 text-xs">
                    <div class="flex justify-between items-center border-b border-slate-700 pb-2">
                        <span class="font-bold text-amber-400 uppercase">Photo Scale & Alignment</span>
                        <input type="file" id="main-photo-upload" accept="image/*" class="text-[10px] text-slate-400 file:mr-2 file:py-1 file:px-2 file:rounded file:border-0 file:bg-amber-500 file:text-slate-950 font-semibold">
                    </div>
                    <div>
                        <div class="flex justify-between text-slate-300 mb-1">
                            <span>Zoom Scale:</span>
                            <span id="main-scale-val" class="text-amber-400 font-bold">100%</span>
                        </div>
                        <input type="range" id="main-photo-scale" min="10" max="300" value="100" class="w-full accent-amber-400">
                    </div>
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <span class="text-slate-300">Shift X (Left/Right):</span>
                            <input type="range" id="main-photo-x" min="-150" max="150" value="0" class="w-full accent-amber-400">
                        </div>
                        <div>
                            <span class="text-slate-300">Shift Y (Up/Down):</span>
                            <input type="range" id="main-photo-y" min="-150" max="150" value="0" class="w-full accent-amber-400">
                        </div>
                    </div>
                </div>
            </div>

            <!-- Bio Details -->
            <div class="md:col-span-7 space-y-6">
                <span class="text-amber-400 font-bold text-xs uppercase tracking-widest">About CWHOMESKY</span>
                <h2 class="font-luxury text-3xl md:text-4xl font-bold text-white">Patrick C. Washington</h2>
                <p class="text-slate-300 text-sm md:text-base leading-relaxed font-light">
                    Whether you are looking to purchase your primary residence, sell a property for maximum value, or manage ongoing real estate operations, CWHOMESKY provides dedicated end-to-end guidance backed by deep local community roots.
                </p>
                
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-2 text-xs">
                    <div class="glass-card p-4 rounded-lg">
                        <span class="text-slate-400 block mb-1">Direct Phone Lines</span>
                        <p class="font-bold text-white">(502) 230-8636</p>
                        <p class="font-bold text-slate-300">(216) 336-5533</p>
                    </div>
                    <div class="glass-card p-4 rounded-lg">
                        <span class="text-slate-400 block mb-1">Direct Email</span>
                        <p class="font-bold text-amber-400">cwhomeky@gmail.com</p>
                        <p class="text-slate-400 mt-0.5">Elizabethtown, KY</p>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- FOCUS AREAS / SERVICES SECTION -->
    <section id="services" class="py-16 px-6 bg-slate-950 border-t border-b border-slate-800/80">
        <div class="max-w-7xl mx-auto">
            <div class="text-center mb-12">
                <span class="text-amber-400 text-xs font-bold uppercase tracking-widest">Our Expertise</span>
                <h2 class="font-luxury text-3xl md:text-4xl font-bold text-white mt-1">Core Focus Areas</h2>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Residential Real Estate -->
                <div class="glass-card rounded-2xl overflow-hidden border border-slate-700/50 hover:border-amber-500/50 transition duration-300">
                    <img src="https://images.unsplash.com/photo-1570129477492-45c003edd2be?auto=format&fit=crop&w=600&q=80" alt="Residential Real Estate" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <h3 class="font-luxury text-xl font-bold text-white mb-1">Residential Real Estate</h3>
                        <span class="text-amber-400 text-xs font-semibold block mb-3">Buying & Selling</span>
                        <p class="text-slate-400 text-xs leading-relaxed">Guiding homeowners and buyers through seamless residential property transactions with personalized care.</p>
                    </div>
                </div>

                <!-- Property Management -->
                <div class="glass-card rounded-2xl overflow-hidden border border-slate-700/50 hover:border-amber-500/50 transition duration-300">
                    <img src="https://images.unsplash.com/photo-1560518883-ce09059eeffa?auto=format&fit=crop&w=600&q=80" alt="Property Management" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <h3 class="font-luxury text-xl font-bold text-white mb-1">Property Management</h3>
                        <span class="text-amber-400 text-xs font-semibold block mb-3">Full Service Solutions</span>
                        <p class="text-slate-400 text-xs leading-relaxed">Comprehensive management services ensuring long-term property value, maintenance, and operational ease.</p>
                    </div>
                </div>

                <!-- Local Market Expertise -->
                <div class="glass-card rounded-2xl overflow-hidden border border-slate-700/50 hover:border-amber-500/50 transition duration-300">
                    <img src="https://images.unsplash.com/photo-1582407947304-fd86f028f716?auto=format&fit=crop&w=600&q=80" alt="Local Market Expertise" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <h3 class="font-luxury text-xl font-bold text-white mb-1">Local Market Expertise</h3>
                        <span class="text-amber-400 text-xs font-semibold block mb-3">Elizabethtown & Beyond</span>
                        <p class="text-slate-400 text-xs leading-relaxed">In-depth knowledge of local neighborhood trends, accurate property valuations, and strategic market insights.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CONTACT FORM SECTION -->
    <section id="contact" class="py-16 px-6 max-w-4xl mx-auto w-full">
        <div class="text-center mb-10">
            <span class="text-amber-400 text-xs font-bold uppercase tracking-widest">Get In Touch</span>
            <h2 class="font-luxury text-3xl font-bold text-white mt-1">Connect With CWHOMESKY</h2>
            <p class="text-slate-400 text-xs md:text-sm mt-2">Send a direct message and we will get back to you promptly.</p>
        </div>

        <div class="glass-card p-8 rounded-2xl shadow-2xl border border-slate-700/50">
            <!-- REPLACE YOUR_FORMSPREE_ID WITH YOUR ACTUAL FORMSPREE FORM ID -->
            <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST" class="space-y-4 text-xs">
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-slate-300 font-semibold mb-1">Full Name</label>
                        <input type="text" name="name" required placeholder="John Doe" class="w-full p-3 bg-slate-900/80 border border-slate-700 rounded-lg text-white focus:outline-none focus:border-amber-400">
                    </div>
                    <div>
                        <label class="block text-slate-300 font-semibold mb-1">Email Address</label>
                        <input type="email" name="email" required placeholder="name@example.com" class="w-full p-3 bg-slate-900/80 border border-slate-700 rounded-lg text-white focus:outline-none focus:border-amber-400">
                    </div>
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">Phone Number</label>
                    <input type="tel" name="phone" placeholder="(502) 230-8636" class="w-full p-3 bg-slate-900/80 border border-slate-700 rounded-lg text-white focus:outline-none focus:border-amber-400">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">How Can We Help You?</label>
                    <textarea name="message" rows="4" required placeholder="Type your message here..." class="w-full p-3 bg-slate-900/80 border border-slate-700 rounded-lg text-white focus:outline-none focus:border-amber-400"></textarea>
                </div>
                <button type="submit" class="w-full bg-amber-500 text-slate-950 font-bold py-3 rounded-lg hover:bg-amber-400 transition text-sm shadow-xl">
                    Send Message Directly
                </button>
            </form>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="border-t border-slate-800 py-8 text-center text-xs text-slate-500 bg-slate-950">
        <p><strong class="text-slate-300">CWHOMESKY</strong> | Patrick C. Washington | Elizabethtown, KY</p>
        <p class="mt-1">Direct: (502) 230-8636 | (216) 336-5533 | cwhomeky@gmail.com</p>
        <p class="mt-4 text-[10px] text-slate-600">&copy; All Rights Reserved.</p>
    </footer>

    <!-- SCRIPT FOR PHOTO SCALE & POSITION CONTROL -->
    <script>
        const mainPhoto = document.getElementById('main-agent-photo');
        let mainScale = 100, mainX = 0, mainY = 0;

        function updateMainPhoto() {
            mainPhoto.style.transform = `translate(${mainX}px, ${mainY}px) scale(${mainScale / 100})`;
            document.getElementById('main-scale-val').innerText = mainScale + '%';
        }

        document.getElementById('main-photo-scale').addEventListener('input', (e) => { 
            mainScale = e.target.value; 
            updateMainPhoto(); 
        });
        document.getElementById('main-photo-x').addEventListener('input', (e) => { 
            mainX = e.target.value; 
            updateMainPhoto(); 
        });
        document.getElementById('main-photo-y').addEventListener('input', (e) => { 
            mainY = e.target.value; 
            updateMainPhoto(); 
        });

        document.getElementById('main-photo-upload').addEventListener('change', function(e) {
            if (e.target.files[0]) {
                const reader = new FileReader();
                reader.onload = (ev) => {
                    mainPhoto.src = ev.target.result;
                };
                reader.readAsDataURL(e.target.files[0]);
            }
        });
    </script>
</body>
</html>
