<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SSPL DRDO Portal</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary-color: #264f7a;
      --secondary-color: #1976d2;
      --dark-color: #333;
      --light-color: #f9f9f9;
      --danger-color: #dc3545;
      --success-color: #28a745;
      --warning-color: #ffc107;
      --info-color: #17a2b8;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.6;
      color: #333;
      background-color: #f5f5f5;
    }

    .header {
      background-color: var(--primary-color);
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 20px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }

    .header-content {
      display: flex;
      align-items: center;
      gap: 20px;
    }

    .header img {
      height: 80px;
      width: auto;
    }

    .header-text {
      color: white;
    }

    .header-text h1 {
      font-size: 1.8rem;
      margin-bottom: 5px;
    }

    .header-text p {
      font-size: 0.9rem;
      opacity: 0.9;
    }

    .navbar {
      background-color: var(--dark-color);
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 20px;
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .navbar-links {
      display: flex;
      gap: 5px;
    }

    .navbar a {
      display: block;
      color: #f2f2f2;
      text-align: center;
      padding: 14px 16px;
      text-decoration: none;
      transition: all 0.3s ease;
      font-weight: 500;
    }

    .navbar a:hover {
      background-color: #575757;
      color: white;
    }

    .navbar a.active {
      background-color: var(--secondary-color);
      color: white;
    }

    .navbar button {
      background-color: var(--secondary-color);
      color: white;
      padding: 10px 16px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: all 0.3s ease;
      font-weight: 500;
    }

    .navbar button:hover {
      background-color: #145ca1;
      transform: translateY(-2px);
    }

    /* Mobile menu button */
    .mobile-menu-btn {
      display: none;
      background: none;
      border: none;
      color: white;
      font-size: 1.5rem;
      cursor: pointer;
    }

    /* Modal styles */
    .modal {
      display: none;
      position: fixed;
      z-index: 1000;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      overflow: auto;
      background-color: rgba(0,0,0,0.5);
      animation: fadeIn 0.3s;
    }

    @keyframes fadeIn {
      from {opacity: 0;}
      to {opacity: 1;}
    }

    .modal-content {
      background-color: #fff;
      margin: 10% auto;
      padding: 25px;
      border-radius: 10px;
      width: 90%;
      max-width: 450px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.2);
      animation: slideDown 0.4s;
    }

    @keyframes slideDown {
      from {
        transform: translateY(-50px);
        opacity: 0;
      }
      to {
        transform: translateY(0);
        opacity: 1;
      }
    }

    .close {
      float: right;
      font-size: 24px;
      cursor: pointer;
      color: #aaa;
      transition: color 0.3s;
    }

    .close:hover {
      color: var(--danger-color);
    }

    .modal-content h2 {
      text-align: center;
      margin-bottom: 20px;
      color: var(--primary-color);
    }

    .modal-content form {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    .form-group {
      display: flex;
      flex-direction: column;
    }

    .modal-content label {
      margin-bottom: 5px;
      font-weight: 500;
      color: #555;
    }

    .modal-content input {
      padding: 12px;
      border-radius: 5px;
      border: 1px solid #ddd;
      font-size: 1rem;
      transition: border 0.3s;
    }

    .modal-content input:focus {
      border-color: var(--secondary-color);
      outline: none;
      box-shadow: 0 0 0 2px rgba(25, 118, 210, 0.2);
    }

    .login-options {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-top: 15px;
    }

    .login-options button {
      padding: 12px;
      border: none;
      background-color: var(--secondary-color);
      color: white;
      border-radius: 5px;
      cursor: pointer;
      font-weight: 500;
      transition: all 0.3s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }

    .login-options button:hover {
      background-color: #145ca1;
      transform: translateY(-2px);
    }

    .login-options button i {
      font-size: 1.1rem;
    }

    .signup-link {
      margin-top: 15px;
      text-align: center;
      font-size: 0.9rem;
    }

    .signup-link a {
      color: var(--secondary-color);
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s;
    }

    .signup-link a:hover {
      color: #145ca1;
      text-decoration: underline;
    }

    .forgot-password {
      text-align: right;
      margin-top: -10px;
    }

    .forgot-password a {
      color: #666;
      font-size: 0.85rem;
      text-decoration: none;
      transition: color 0.3s;
    }

    .forgot-password a:hover {
      color: var(--secondary-color);
    }

    /* Hero Section */
    .hero {
      height: 80vh;
      background: linear-gradient(rgba(38, 79, 122, 0.8), rgba(38, 79, 122, 0.8)), 
                  url('https://images.unsplash.com/photo-1451187580459-43490279c0fa?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1472&q=80') no-repeat center center/cover;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      color: white;
      position: relative;
      padding: 0 20px;
    }

    .hero-content {
      max-width: 800px;
    }

    .hero-content h1 {
      font-size: 3rem;
      margin-bottom: 20px;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
    }

    .hero-content p {
      font-size: 1.2rem;
      margin-bottom: 30px;
      opacity: 0.9;
    }

    .hero-buttons {
      display: flex;
      gap: 15px;
      justify-content: center;
    }

    .hero-btn {
      background-color: var(--secondary-color);
      color: white;
      padding: 15px 30px;
      font-size: 1rem;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: all 0.3s;
      font-weight: 500;
    }

    .hero-btn:hover {
      background-color: #145ca1;
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }

    .hero-btn.secondary {
      background-color: transparent;
      border: 2px solid white;
    }

    .hero-btn.secondary:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }

    /* About Section */
    .section {
      padding: 80px 20px;
      text-align: center;
    }

    .section-title {
      font-size: 2.5rem;
      margin-bottom: 30px;
      color: var(--primary-color);
      position: relative;
      display: inline-block;
    }

    .section-title::after {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 50%;
      transform: translateX(-50%);
      width: 80px;
      height: 4px;
      background-color: var(--secondary-color);
      border-radius: 2px;
    }

    .section-text {
      font-size: 1.1rem;
      max-width: 800px;
      margin: 0 auto 40px;
      color: #555;
    }

    #about {
      background-color: white;
    }

    .features {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
      margin-top: 50px;
    }

    .feature-card {
      background-color: white;
      border-radius: 8px;
      padding: 30px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
      transition: transform 0.3s, box-shadow 0.3s;
      text-align: center;
    }

    .feature-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
    }

    .feature-icon {
      font-size: 3rem;
      color: var(--secondary-color);
      margin-bottom: 20px;
    }

    .feature-card h3 {
      font-size: 1.5rem;
      margin-bottom: 15px;
      color: var(--primary-color);
    }

    /* What's New Section */
    #whats-new {
      background-color: var(--light-color);
    }

    .news-container {
      max-width: 900px;
      margin: 0 auto;
      background: white;
      border-radius: 8px;
      padding: 30px;
      box-shadow: 0 2px 15px rgba(0, 0, 0, 0.05);
    }

    .news-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 30px;
    }

    .news-title {
      font-size: 1.8rem;
      color: var(--primary-color);
      border-bottom: 3px solid var(--secondary-color);
      padding-bottom: 5px;
    }

    .news-list {
      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    .news-item {
      padding: 20px;
      border-radius: 6px;
      background-color: #f9f9f9;
      transition: all 0.3s;
      border-left: 4px solid var(--secondary-color);
    }

    .news-item:hover {
      background-color: #f0f0f0;
      transform: translateX(5px);
    }

    .news-item-date {
      font-size: 0.9rem;
      color: #666;
      margin-bottom: 5px;
    }

    .news-item-title {
      font-size: 1.1rem;
      color: #333;
      font-weight: 500;
    }

    .news-badge {
      background-color: var(--warning-color);
      color: #333;
      font-weight: bold;
      font-size: 0.7rem;
      padding: 3px 8px;
      border-radius: 10px;
      margin-left: 10px;
      display: inline-block;
    }

    .view-all {
      display: inline-block;
      margin-top: 30px;
      color: var(--secondary-color);
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s;
      display: flex;
      align-items: center;
      gap: 5px;
    }

    .view-all:hover {
      color: #145ca1;
      text-decoration: underline;
    }

    /* Footer */
    footer {
      background-color: var(--dark-color);
      color: white;
      padding: 50px 20px 20px;
    }

    .footer-content {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 30px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .footer-column h3 {
      font-size: 1.3rem;
      margin-bottom: 20px;
      color: white;
      position: relative;
      padding-bottom: 10px;
    }

    .footer-column h3::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 50px;
      height: 2px;
      background-color: var(--secondary-color);
    }

    .footer-column p {
      margin-bottom: 15px;
      opacity: 0.8;
      font-size: 0.95rem;
    }

    .footer-links {
      list-style: none;
    }

    .footer-links li {
      margin-bottom: 10px;
    }

    .footer-links a {
      color: white;
      text-decoration: none;
      opacity: 0.8;
      transition: opacity 0.3s;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .footer-links a:hover {
      opacity: 1;
      color: var(--secondary-color);
    }

    .footer-links i {
      font-size: 0.8rem;
    }

    .social-links {
      display: flex;
      gap: 15px;
      margin-top: 20px;
    }

    .social-links a {
      color: white;
      background-color: rgba(255, 255, 255, 0.1);
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s;
    }

    .social-links a:hover {
      background-color: var(--secondary-color);
      transform: translateY(-3px);
    }

    .footer-bottom {
      text-align: center;
      padding-top: 30px;
      margin-top: 30px;
      border-top: 1px solid rgba(255, 255, 255, 0.1);
      font-size: 0.9rem;
      opacity: 0.7;
    }

    /* Responsive styles */
    @media (max-width: 992px) {
      .hero-content h1 {
        font-size: 2.5rem;
      }
    }

    @media (max-width: 768px) {
      .header {
        flex-direction: column;
        text-align: center;
        padding: 20px;
      }

      .header-content {
        flex-direction: column;
        gap: 10px;
      }

      .header-text {
        margin-bottom: 15px;
      }

      .navbar-links {
        display: none;
        flex-direction: column;
        width: 100%;
        position: absolute;
        top: 100%;
        left: 0;
        background-color: var(--dark-color);
        padding: 10px 0;
      }

      .navbar-links.active {
        display: flex;
      }

      .mobile-menu-btn {
        display: block;
      }

      .hero {
        height: 70vh;
      }

      .hero-content h1 {
        font-size: 2rem;
      }

      .hero-content p {
        font-size: 1rem;
      }

      .hero-buttons {
        flex-direction: column;
        gap: 10px;
      }

      .hero-btn {
        width: 100%;
      }

      .section {
        padding: 60px 20px;
      }

      .section-title {
        font-size: 2rem;
      }
    }

    @media (max-width: 576px) {
      .modal-content {
        padding: 20px 15px;
      }

      .hero-content h1 {
        font-size: 1.8rem;
      }
    }
  </style>
</head>

<body>
  <!-- Header -->
  <div class="header">
    <div class="header-content">
      <img src="data:image/jpeg;base64,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" alt="SSPL DRDO Logo">
      <div class="header-text">
        <h1>SSPL DRDO</h1>
        <p>Solid State Physics Laboratory, Defence Research & Development Organisation</p>
      </div>
    </div>
  </div>

  <!-- Navigation -->
  <div class="navbar">
    <button class="mobile-menu-btn" id="mobileMenuBtn">
      <i class="fas fa-bars"></i>
    </button>
    <div class="navbar-links" id="navbarLinks">
      <a href="#home" class="active"><i class="fas fa-home"></i> Home</a>
      <a href="#about"><i class="fas fa-info-circle"></i> About</a>
      <a href="#services"><i class="fas fa-cogs"></i> Services</a>
      <a href="#whats-new"><i class="fas fa-newspaper"></i> What's New</a>
      <a href="#contact"><i class="fas fa-envelope"></i> Contact</a>
    </div>
    <div>
      <button id="openLoginModal"><i class="fas fa-sign-in-alt"></i> Login</button>
    </div>
  </div>

  <!-- Login Modal -->
  <div id="loginModal" class="modal">
    <div class="modal-content">
      <span class="close">&times;</span>
      <h2>Login to Portal</h2>
      <form id="loginForm">
        <div class="form-group">
          <label for="userid">User ID</label>
          <input type="text" id="userid" name="userid" placeholder="Enter your user ID" required>
        </div>
        
        <div class="form-group">
          <label for="password">Password</label>
          <input type="password" id="password" name="password" placeholder="Enter your password" required>
          <div class="forgot-password">
            <a href="#"><i class="fas fa-key"></i> Forgot Password?</a>
          </div>
        </div>

        <div class="login-options">
          <button type="submit"><i class="fas fa-user-shield"></i> Login as Admin</button>
          <button type="submit"><i class="fas fa-university"></i> Login as Institute</button>
          <button type="submit"><i class="fas fa-user-tie"></i> Login as Director</button>
        </div>

        <p class="signup-link">Not a user? <a href="#"><i class="fas fa-user-plus"></i> Sign up here</a></p>
      </form>
    </div>
  </div>

  <!-- Hero Section -->
  <section class="hero" id="home">
    <div class="hero-content">
      <h1>Advancing Defense Technologies Through Research</h1>
      <p>SSPL DRDO is committed to excellence in solid state physics research for national security applications.</p>
      <div class="hero-buttons">
        <button class="hero-btn" onclick="document.getElementById('about').scrollIntoView({ behavior: 'smooth' })">
          <i class="fas fa-book-open"></i> Learn More
        </button>
        <button class="hero-btn secondary" id="openLoginModal2">
          <i class="fas fa-user-lock"></i> Member Login
        </button>
      </div>
    </div>
  </section>

  <!-- About Section -->
  <section class="section" id="about">
    <h2 class="section-title">About SSPL DRDO</h2>
    <p class="section-text">
      The Solid State Physics Laboratory (SSPL) of DRDO is a premier laboratory engaged in research and development 
      of advanced materials and devices for defense applications. Our mission is to develop cutting-edge technologies 
      in the field of solid state physics to meet the requirements of the Indian Armed Forces.
    </p>
    
    <div class="features">
      <div class="feature-card">
        <div class="feature-icon">
          <i class="fas fa-flask"></i>
        </div>
        <h3>Research Excellence</h3>
        <p>World-class research facilities and expertise in materials science, semiconductor devices, and quantum technologies.</p>
      </div>
      
      <div class="feature-card">
        <div class="feature-icon">
          <i class="fas fa-shield-alt"></i>
        </div>
        <h3>Defense Applications</h3>
        <p>Developing critical technologies for radar systems, night vision, communication, and electronic warfare.</p>
      </div>
      
      <div class="feature-card">
        <div class="feature-icon">
          <i class="fas fa-users"></i>
        </div>
        <h3>Collaborative Ecosystem</h3>
        <p>Strong partnerships with academic institutions, industries, and other DRDO labs for technology development.</p>
      </div>
    </div>
  </section>

  <!-- What's New Section -->
  <section class="section" id="whats-new">
    <h2 class="section-title">What's New</h2>
    <p class="section-text">
      Stay updated with the latest announcements, opportunities, and developments at SSPL DRDO.
    </p>
    
    <div class="news-container">
      <div class="news-header">
        <h3 class="news-title">Latest Updates</h3>
      </div>
      
      <div class="news-list" id="newsList">
        <!-- News items will be dynamically inserted here -->
      </div>
      
      <a href="#" class="view-all" id="viewAllLink">
        <span>View All Announcements</span>
        <i class="fas fa-arrow-right"></i>
      </a>
    </div>
  </section>

  <!-- Footer -->
  <footer id="contact">
    <div class="footer-content">
      <div class="footer-column">
        <h3>About SSPL</h3>
        <p>The Solid State Physics Laboratory (SSPL) is a premier laboratory of DRDO engaged in research and development of advanced materials and devices.</p>
        <div class="social-links">
          <a href="#"><i class="fab fa-facebook-f"></i></a>
          <a href="#"><i class="fab fa-twitter"></i></a>
          <a href="#"><i class="fab fa-linkedin-in"></i></a>
          <a href="#"><i class="fab fa-youtube"></i></a>
        </div>
      </div>
      
      <div class="footer-column">
        <h3>Quick Links</h3>
        <ul class="footer-links">
          <li><a href="#home"><i class="fas fa-chevron-right"></i> Home</a></li>
          <li><a href="#about"><i class="fas fa-chevron-right"></i> About Us</a></li>
          <li><a href="#whats-new"><i class="fas fa-chevron-right"></i> What's New</a></li>
          <li><a href="#"><i class="fas fa-chevron-right"></i> Careers</a></li>
          <li><a href="#"><i class="fas fa-chevron-right"></i> Tenders</a></li>
        </ul>
      </div>
      
      <div class="footer-column">
        <h3>Contact Us</h3>
        <ul class="footer-links">
          <li><a href="#"><i class="fas fa-map-marker-alt"></i> Lucknow Road, Timarpur, Delhi - 110054</a></li>
          <li><a href="tel:+911123904101"><i class="fas fa-phone"></i> +91-11-23904101</a></li>
          <li><a href="mailto:director@sspl.drdo.in"><i class="fas fa-envelope"></i> director@sspl.drdo.in</a></li>
          <li><a href="#"><i class="fas fa-clock"></i> Mon-Fri: 9:00 AM - 5:30 PM</a></li>
        </ul>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p>&copy; 2023 SSPL DRDO. All Rights Reserved. | Designed and Maintained by SSPL IT Team</p>
    </div>
  </footer>

  <script>
    // Modal functionality
    const modal = document.getElementById("loginModal");
    const btn = document.getElementById("openLoginModal");
    const btn2 = document.getElementById("openLoginModal2");
    const span = document.getElementsByClassName("close")[0];
    const mobileMenuBtn = document.getElementById("mobileMenuBtn");
    const navbarLinks = document.getElementById("navbarLinks");

    // Open modal
    btn.onclick = function() {
      modal.style.display = "block";
      document.body.style.overflow = "hidden";
    }

    btn2.onclick = function() {
      modal.style.display = "block";
      document.body.style.overflow = "hidden";
    }

    // Close modal
    span.onclick = function() {
      modal.style.display = "none";
      document.body.style.overflow = "auto";
    }

    // Close modal when clicking outside
    window.onclick = function(event) {
      if (event.target === modal) {
        modal.style.display = "none";
        document.body.style.overflow = "auto";
      }
    }

    // Toggle mobile menu
    mobileMenuBtn.onclick = function() {
      navbarLinks.classList.toggle("active");
    }

    // Close mobile menu when clicking on a link
    document.querySelectorAll('.navbar-links a').forEach(link => {
      link.addEventListener('click', () => {
        navbarLinks.classList.remove("active");
      });
    });

    // Form submission
    document.getElementById("loginForm").addEventListener("submit", function(e) {
      e.preventDefault();
      alert("Login functionality will be implemented in the backend");
      modal.style.display = "none";
      document.body.style.overflow = "auto";
    });

    // News data
    const newsData = [
      {
        date: '09/05/2025',
        title: 'Advertisement for the Post of Director, DIA-CoE, IIT Delhi',
        isNew: true
      },
      {
        date: '09/05/2025',
        title: 'Announcement for the Post of Director, DIA RCoE, IIT Madras - Advt.85/2025',
        isNew: true
      },
      {
        date: '08/05/2025',
        title: 'Engagement of retired Government Officials as Consultant on Contract Basis in DRDO',
        isNew: true
      },
      {
        date: '05/05/2025',
        title: 'Advertisement for engaging Technician Apprentices under the Apprentices Act 1961',
        isNew: false
      },
      {
        date: '03/05/2025',
        title: 'SSPL Annual Research Symposium 2025 - Call for Papers',
        isNew: false
      }
    ];

    // Render news items
    const newsList = document.getElementById("newsList");
    
    newsData.forEach(item => {
      const newsItem = document.createElement("div");
      newsItem.className = "news-item";
      
      newsItem.innerHTML = `
        <div class="news-item-date">${item.date}</div>
        <div class="news-item-title">
          ${item.title}
          ${item.isNew ? '<span class="news-badge">NEW</span>' : ''}
        </div>
      `;
      
      newsList.appendChild(newsItem);
    });

    // Smooth scrolling for anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function(e) {
        e.preventDefault();
        
        const targetId = this.getAttribute('href');
        if (targetId === '#') return;
        
        const targetElement = document.querySelector(targetId);
        if (targetElement) {
          targetElement.scrollIntoView({
            behavior: 'smooth'
          });
        }
      });
    });

    // Active link highlighting
    window.addEventListener('scroll', function() {
      const scrollPosition = window.scrollY;
      
      document.querySelectorAll('section').forEach(section => {
        const sectionTop = section.offsetTop - 100;
        const sectionBottom = sectionTop + section.offsetHeight;
        const sectionId = section.getAttribute('id');
        
        if (scrollPosition >= sectionTop && scrollPosition < sectionBottom) {
          document.querySelectorAll('.navbar-links a').forEach(link => {
            link.classList.remove('active');
            if (link.getAttribute('href') === `#${sectionId}`) {
              link.classList.add('active');
            }
          });
        }
      });
    });
  </script>
</body>
</html>
