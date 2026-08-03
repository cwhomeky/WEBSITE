<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lot 21 - Low Country Court, Hodgenville, KY</title>
  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@400;600;700;800&family=Open+Sans:wght@400;600&display=swap" rel="stylesheet">
  
  <style>
    :root {
      --primary-blue: #1D3D8F;
      --accent-gold: #F1B318;
      --bg-light: #F4F6FB;
      --card-bg: #FFFFFF;
      --text-main: #222222;
      --text-muted: #555555;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Open Sans', sans-serif;
      background-color: var(--primary-blue);
      color: var(--text-main);
      display: flex;
      justify-content: center;
      padding: 20px;
    }

    .flyer-container {
      width: 100%;
      max-width: 650px;
      background-color: var(--primary-blue);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 16px;
    }

    /* Top Banner */
    .top-banner {
      background-color: var(--accent-gold);
      color: #000;
      font-family: 'Montserrat', sans-serif;
      font-weight: 800;
      font-size: 0.9rem;
      letter-spacing: 1px;
      padding: 6px 24px;
      border-radius: 20px;
      text-transform: uppercase;
      text-align: center;
      box-shadow: 0 2px 4px rgba(0,0,0,0.15);
    }

    /* Main Title */
    .headline {
      font-family: 'Great Vibes', cursive;
      color: #FFFFFF;
      font-size: 2.8rem;
      text-align: center;
      line-height: 1.2;
      margin-top: 4px;
    }

    /* Address Bar */
    .address-bar {
      width: 100%;
      background-color: #FFFFFF;
      color: var(--primary-blue);
      text-align: center;
      padding: 10px 15px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 800;
      font-size: 1.1rem;
      border-radius: 6px;
      letter-spacing: 0.5px;
    }

    /* Info Badges (Price & Size) */
    .info-badges {
      display: flex;
      justify-content: space-between;
      width: 100%;
      gap: 15px;
    }

    .badge {
      flex: 1;
      background-color: rgba(255, 255, 255, 0.15);
      border: 1px solid rgba(255, 255, 255, 0.3);
      color: #FFFFFF;
      text-align: center;
      padding: 8px 12px;
      border-radius: 6px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 1rem;
    }

    /* Card Layouts */
    .card {
      width: 100%;
      background-color: var(--card-bg);
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    }

    .plat-images {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }

    .plat-images img {
      width: 100%;
      height: auto;
      border-radius: 6px;
      border: 1px solid #E0E0E0;
      object-fit: cover;
    }

    .description-text {
      font-size: 1.05rem;
      line-height: 1.6;
      color: #333333;
      margin-bottom: 20px;
    }

    .specs-list {
      list-style: none;
      font-size: 1.05rem;
      line-height: 1.8;
      color: #222222;
      border-bottom: 1px solid #EEEEEE;
      padding-bottom: 16px;
      margin-bottom: 16px;
    }

    .specs-list li strong {
      font-weight: 700;
      color: #000;
    }

    .highlights-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      font-weight: 700;
      color: #222222;
      font-size: 0.95rem;
    }

    .highlight-item {
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .highlight-item span {
      color: var(--primary-blue);
      font-weight: 900;
    }

    /* Lead Capture Form Styling */
    .lead-form-card {
      border: 2px solid var(--accent-gold);
    }

    .form-title {
      font-family: 'Montserrat', sans-serif;
      font-weight: 800;
      font-size: 1.25rem;
      color: var(--primary-blue);
      margin-bottom: 6px;
      text-align: center;
    }

    .form-subtitle {
      font-size: 0.9rem;
      color: var(--text-muted);
      text-align: center;
      margin-bottom: 16px;
    }

    .contact-form {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .form-group label {
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--text-main);
    }

    .form-group input,
    .form-group textarea {
      width: 100%;
      padding: 10px 12px;
      border: 1px solid #CCCCCC;
      border-radius: 6px;
      font-family: inherit;
      font-size: 0.95rem;
      background-color: #FAFAFA;
      transition: border-color 0.2s ease;
    }

    .form-group input:focus,
    .form-group textarea:focus {
      outline: none;
      border-color: var(--primary-blue);
      background-color: #FFFFFF;
    }

    .submit-btn {
      background-color: var(--primary-blue);
      color: #FFFFFF;
      font-family: 'Montserrat', sans-serif;
      font-weight: 800;
      font-size: 1rem;
      padding: 12px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      transition: background-color 0.2s ease;
      margin-top: 8px;
    }

    .submit-btn:hover {
      background-color: #142B66;
    }

    /* Agent Footer Section */
    .footer-section {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 16px;
      margin-top: 10px;
    }

    .agent-details-wrapper {
      display: flex;
      width: 100%;
      align-items: center;
      justify-content: space-between;
      gap: 15px;
    }

    .agent-profile {
      display: flex;
      align-items: center;
      gap: 15px;
    }

    .agent-avatar {
      width: 90px;
      height: 90px;
      border-radius: 50%;
      border: 3px solid #FFFFFF;
      object-fit: cover;
    }

    .agent-info {
      color: #FFFFFF;
    }

    .broker-line {
      font-size: 0.8rem;
      color: #CBD5E1;
      margin-bottom: 4px;
    }

    .agent-name {
      font-family: 'Montserrat', sans-serif;
      font-size: 1.25rem;
      font-weight: 800;
      color: #FFFFFF;
    }

    .contact-link {
      color: #FFFFFF;
      text-decoration: none;
      font-size: 0.95rem;
      display: block;
      margin-top: 2px;
    }

    .contact-link:hover {
      text-decoration: underline;
    }

    .qr-box {
      background: #FFFFFF;
      padding: 6px;
      border-radius: 8px;
    }

    .qr-box img {
      width: 80px;
      height: 80px;
      display: block;
    }

    .brokerage-logo {
      background-color: #000000;
      padding: 8px 16px;
      border-radius: 4px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    @media (max-width: 480px) {
      .headline { font-size: 2.2rem; }
      .agent-details-wrapper { flex-direction: column; text-align: center; }
      .agent-profile { flex-direction: column; }
      .highlights-grid { grid-template-columns: 1fr; }
      .plat-images { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

  <main class="flyer-container">
    
    <!-- Top Banner -->
    <div class="top-banner">
      DON'T MISS THIS OPPORTUNITY!
    </div>

    <!-- Title Header -->
    <h1 class="headline">
      Your Dream Build Lot in Scenic LaRue County!
    </h1>

    <!-- Address Bar -->
    <div class="address-bar">
      LOT 21, LOW COUNTRY COURT, HODGENVILLE, KY., 42748
    </div>

    <!-- Info Badges -->
    <div class="info-badges">
      <div class="badge">💲 Price: $49,000</div>
      <div class="badge">📐 Size: 0.82 AC</div>
    </div>

    <!-- Image Gallery -->
    <div class="card">
      <div class="plat-images">
        <img src="https://via.placeholder.com/300x400?text=Plat+Map+Detail" alt="Plat Map Lot Detail">
        <img src="https://via.placeholder.com/300x400?text=Subdivision+Overview" alt="Subdivision Overview Map">
      </div>
    </div>

    <!-- Property Details -->
    <div class="card">
      <p class="description-text">
        Discover your opportunity to build the home of your dreams on this newly developed lot in Magnolia Fields! Here is your opportunity to build the home of your dreams on one of these newly developed lots nestled in the heart of scenic LaRue County, Kentucky. These pristine, build-ready lots are situated in a peaceful rural setting while still offering convenient access to nearby amenities, schools, and commuter routes.
      </p>

      <ul class="specs-list">
        <li><strong>Topography:</strong> Level</li>
        <li><strong>Water:</strong> County</li>
        <li><strong>Sewer:</strong> Septic System</li>
        <li><strong>Electricity:</strong> Available - On Property</li>
        <li><strong>Fence:</strong> None</li>
        <li><strong>Outer Structures:</strong> None</li>
        <li><strong>Location Features:</strong> County</li>
      </ul>

      <div class="highlights-grid">
        <div class="highlight-item"><span>✓</span> Build-Ready Site</div>
        <div class="highlight-item"><span>✓</span> LaRue County Schools</div>
        <div class="highlight-item"><span>✓</span> Scenic Location</div>
        <div class="highlight-item"><span>✓</span> MLS #1234567</div>
      </div>
    </div>

    <!-- Lead Capture Form -->
    <div class="card lead-form-card">
      <h2 class="form-title">Interested in Lot 21?</h2>
      <p class="form-subtitle">Fill out the form below to request a private walkthrough or more details.</p>
      
      <!-- Set up your free endpoint at formspree.io and replace the action URL below -->
      <form action="https://formspree.io/f/YOUR_FORMSPREE_ID_HERE" method="POST" class="contact-form">
        <div class="form-group">
          <label for="full-name">Full Name</label>
          <input type="text" id="full-name" name="name" placeholder="John Doe" required>
        </div>

        <div class="form-group">
          <label for="email-address">Email Address</label>
          <input type="email" id="email-address" name="email" placeholder="john@example.com" required>
        </div>

        <div class="form-group">
          <label for="phone-number">Phone Number</label>
          <input type="tel" id="phone-number" name="phone" placeholder="(502) 555-0199">
        </div>

        <div class="form-group">
          <label for="message">Message / Questions</label>
          <textarea id="message" name="message" rows="4" placeholder="I'd like more information regarding Lot 21 on Low Country Court..."></textarea>
        </div>

        <input type="hidden" name="_subject" value="New Lead: Lot 21 Low Country Court Inquiry">

        <button type="submit" class="submit-btn">Send Inquiry</button>
      </form>
    </div>

    <!-- Agent Footer Section -->
    <footer class="footer-section">
      <div class="agent-details-wrapper">
        
        <div class="agent-profile">
          <img src="https://via.placeholder.com/90" alt="Patrick C. Washington" class="agent-avatar">
          <div class="agent-info">
            <div class="broker-line">Brokered by Pennington Properties | Aaron Pennington</div>
            <div class="agent-name">Patrick C. Washington</div>
            <a href="tel:5022308636" class="contact-link">📱 Direct: (502) 230-8636</a>
            <a href="mailto:cwhomeky@gmail.com" class="contact-link">✉️ cwhomeky@gmail.com</a>
            <div class="broker-line" style="margin-top: 4px;">Office: (270) 872-5469 | Elizabethtown, KY</div>
          </div>
        </div>

        <div class="qr-box">
          <img src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=mailto:cwhomeky@gmail.com" alt="Scan QR Code">
        </div>

      </div>

      <div class="brokerage-logo">
        <h3 style="color: red; font-family: sans-serif; text-transform: uppercase;">Pennington Properties</h3>
      </div>
    </footer>

  </main>

</body>
</html>
