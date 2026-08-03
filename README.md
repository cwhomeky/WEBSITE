<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pennington Properties | Real Estate Solutions</title>
  
  <!-- =========================================================
       CUSTOM STYLES (CSS)
       Edit the variables in :root to change colors across the whole site!
       ========================================================= -->
  <style>
    :root {
      --primary-color: #0f172a;    /* Dark Navy Header/Footer */
      --secondary-color: #1e293b;  /* Dark Slate Accents */
      --accent-color: #2563eb;     /* Button & Link Blue */
      --text-dark: #334155;        /* Body Text */
      --bg-light: #f8fafc;         /* Site Background */
      --card-bg: #ffffff;          /* Card Background */
    }

    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
    body { background-color: var(--bg-light); color: var(--text-dark); line-height: 1.6; }

    /* --- Navigation Bar --- */
    header {
      background-color: var(--primary-color);
      color: white;
      padding: 1rem 2rem;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    .brand-title { font-size: 1.5rem; font-weight: bold; letter-spacing: 0.5px; }
    nav a { color: #e2e8f0; text-decoration: none; margin-left: 1.5rem; font-weight: 500; transition: color 0.2s; }
    nav a:hover { color: var(--accent-color); }
    .nav-phone { background: var(--accent-color); padding: 0.5rem 1rem; border-radius: 4px; color: white !important; }

    /* --- Hero Banner --- */
    .hero {
      background: linear-gradient(rgba(15, 23, 42, 0.75), rgba(15, 23, 42, 0.75)), 
                  url('https://images.unsplash.com/photo-1564013799919-ab600027ffc6?auto=format&fit=crop&w=1600&q=80') center/cover no-repeat;
      color: white;
      text-align: center;
      padding: 6rem 1.5rem;
    }
    .hero h1 { font-size: 2.75rem; margin-bottom: 1rem; }
    .hero p { font-size: 1.25rem; max-width: 650px; margin: 0 auto 2rem; color: #cbd5e1; }
    .cta-btn {
      display: inline-block;
      background-color: var(--accent-color);
      color: white;
      padding: 0.85rem 2rem;
      text-decoration: none;
      font-weight: 600;
      border-radius: 5px;
      transition: background 0.2s;
    }
    .cta-btn:hover { background-color: #1d4ed8; }

    /* --- Main Container --- */
    .container { max-width: 1100px; margin: 3rem auto; padding: 0 1.5rem; }
    .section-title { font-size: 2rem; color: var(--primary-color); margin-bottom: 1.5rem; text-align: center; }

    /* --- Grid & Cards --- */
    .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem; }
    .card {
      background: var(--card-bg);
      border-radius: 8px;
      overflow: hidden;
      border: 1px solid #e2e8f0;
      box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
      transition: transform 0.2s;
    }
    .card:hover { transform: translateY(-4px); }
    .card img { width: 100%; height: 220px; object-fit: cover; }
    .card-content { padding: 1.5rem; }
    .card-title { font-size: 1.25rem; font-weight: bold; color: var(--primary-color); margin-bottom: 0.5rem; }
    .card-subtitle { color: var(--accent-color); font-size: 0.95rem; font-weight: 600; margin-bottom: 1rem; }

    /* --- Contact Form Section --- */
    .contact-wrapper {
      background: var(--card-bg);
      border: 1px solid #e2e8f0;
      border-radius: 8px;
      padding: 2.5rem;
      max-width: 700px;
      margin: 4rem auto 0;
      box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
    }
    .form-group { margin-bottom: 1.25rem; }
    .form-group label { display: block; font-weight: 600; margin-bottom: 0.5rem; }
    .form-group input, .form-group textarea {
      width: 100%;
      padding: 0.75rem;
      border: 1px solid #cbd5e1;
      border-radius: 5px;
      font-size: 1rem;
    }
    .form-group input:focus, .form-group textarea:focus {
      outline: none;
      border-color: var(--accent-color);
      box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
    }
    .submit-btn {
      width: 100%;
      background: var(--accent-color);
      color: white;
      border: none;
      padding: 1rem;
      font-size: 1rem;
      font-weight: 600;
      border-radius: 5px;
      cursor: pointer;
    }
    .submit-btn:hover { background: #1d4ed8; }

    /* --- Footer --- */
    footer {
      background: var(--primary-color);
      color: #94a3b8;
      text-align: center;
      padding: 2.5rem 1.5rem;
      margin-top: 5rem;
    }
    footer a { color: #f1f5f9; text-decoration: none; }
  </style>
</head>
<body>

  <!-- NAVIGATION HEADER -->
  <header>
    <div class="brand-title">Pennington Properties</div>
    <nav>
      <a href="#about">About</a>
      <a href="#featured">Listings</a>
      <a href="#contact">Contact</a>
      <a href="tel:2708725469" class="nav-phone">270-872-5469</a>
    </nav>
  </header>

  <!-- HERO SECTION -->
  <section class="hero">
    <h1>Your Trusted Local Real Estate Partner</h1>
    <p>Providing professional real estate services across Elizabethtown and surrounding areas.</p>
    <a href="#contact" class="cta-btn">Get In Touch Today</a>
  </section>

  <!-- MAIN CONTAINER -->
  <main class="container">

    <!-- ABOUT SECTION -->
    <section id="about" style="margin-bottom: 4rem; text-align: center;">
      <h2 class="section-title">Welcome to Pennington Properties</h2>
      <p style="max-width: 800px; margin: 0 auto; font-size: 1.1rem; color: #475569;">
        Whether you are looking to buy your home, sell a property, or explore local investment opportunities, we provide personalized service and local expertise every step of the way.
      </p>
    </section>

    <!-- FEATURED SECTION / SERVICES -->
    <section id="featured">
      <h2 class="section-title">Our Focus Areas</h2>
      <div class="grid">
        
        <div class="card">
          <img src="https://images.unsplash.com/photo-1570129477492-45c003edd2be?auto=format&fit=crop&w=600&q=80" alt="Residential Buying & Selling">
          <div class="card-content">
            <div class="card-title">Residential Real Estate</div>
            <div class="card-subtitle">Buying & Selling</div>
            <p>Guiding homeowners and buyers through seamless residential property transactions.</p>
          </div>
        </div>

        <div class="card">
          <img src="https://images.unsplash.com/photo-1560518883-ce09059eeffa?auto=format&fit=crop&w=600&q=80" alt="Property Management">
          <div class="card-content">
            <div class="card-title">Property Management</div>
            <div class="card-subtitle">Full Service Solutions</div>
            <p>Comprehensive management services ensuring long-term value and operational ease.</p>
          </div>
        </div>

        <div class="card">
          <img src="https://images.unsplash.com/photo-1582407947304-fd86f028f716?auto=format&fit=crop&w=600&q=80" alt="Local Expertise">
          <div class="card-content">
            <div class="card-title">Local Market Expertise</div>
            <div class="card-subtitle">Elizabethtown & Beyond</div>
            <p>In-depth knowledge of local neighborhood trends, valuation, and market conditions.</p>
          </div>
        </div>

      </div>
    </section>

    <!-- FORMSPREE CONTACT SECTION -->
    <section id="contact" class="contact-wrapper">
      <h2 class="section-title" style="margin-bottom: 0.5rem;">Contact Us</h2>
      <p style="text-align: center; color: #64748b; margin-bottom: 2rem;">Send a direct message and we will get back to you promptly.</p>

      <!-- REPLACE "YOUR_FORMSPREE_ID" WITH YOUR ACTUAL FORMSPREE FORM ID -->
      <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST">
        <div class="form-group">
          <label for="full-name">Full Name</label>
          <input type="text" id="full-name" name="name" placeholder="John Doe" required>
        </div>

        <div class="form-group">
          <label for="email-address">Email Address</label>
          <input type="email" id="email-address" name="email" placeholder="name@example.com" required>
        </div>

        <div class="form-group">
          <label for="phone-number">Phone Number</label>
          <input type="tel" id="phone-number" name="phone" placeholder="(270) 555-0123">
        </div>

        <div class="form-group">
          <label for="message">Message</label>
          <textarea id="message" name="message" rows="4" placeholder="How can we help you?" required></textarea>
        </div>

        <button type="submit" class="submit-btn">Send Message</button>
      </form>
    </section>

  </main>

  <!-- FOOTER -->
  <footer>
    <p><strong>Pennington Properties</strong> | Aaron Pennington | Elizabethtown, KY</p>
    <p style="margin-top: 0.5rem;">Direct: <a href="tel:2708725469">270-872-5469</a></p>
    <p style="margin-top: 1.5rem; font-size: 0.85rem;">&copy; All Rights Reserved.</p>
  </footer>

</body>
</html>
