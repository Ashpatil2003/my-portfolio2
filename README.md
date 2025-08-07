<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Ashish Lokhande | Portfolio</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
    />
    <style>
      :root {
        --primary: #6e45e2;
        --secondary: #88d3ce;
        --dark: #1a1a2e;
        --light: #f8f9fa;
        --accent: #ff7e5f;
        --text: #333;
        --card-bg: rgba(255, 255, 255, 0.9);
      }

      [data-theme="dark"] {
        --primary: #7f5af0;
        --secondary: #2cb67d;
        --dark: #010101;
        --light: #fffffe;
        --accent: #ff8906;
        --text: #e8e8e8;
        --card-bg: rgba(30, 30, 46, 0.9);
      }

      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        transition: background 0.3s, color 0.2s;
      }

      body {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        background: linear-gradient(135deg, var(--dark), #16213e);
        color: var(--text);
        line-height: 1.6;
        overflow-x: hidden;
      }

      /* Particle background */
      #particles-js {
        position: fixed;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        z-index: -1;
      }

      /* Navigation */
      nav {
        position: fixed;
        top: 0;
        width: 100%;
        padding: 1.5rem 5%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background: rgba(26, 26, 46, 0.8);
        backdrop-filter: blur(10px);
        z-index: 1000;
        box-shadow: 0 2px 15px rgba(0, 0, 0, 0.1);
      }

      .logo {
        font-size: 1.8rem;
        font-weight: 700;
        color: var(--light);
        text-decoration: none;
      }

      .logo span {
        color: var(--accent);
      }

      .nav-links {
        display: flex;
        gap: 2rem;
      }

      .nav-links a {
        color: var(--light);
        text-decoration: none;
        font-weight: 500;
        position: relative;
        padding: 0.5rem 0;
      }

      .nav-links a::after {
        content: "";
        position: absolute;
        bottom: 0;
        left: 0;
        width: 0;
        height: 2px;
        background: var(--accent);
        transition: width 0.3s ease;
      }

      .nav-links a:hover::after {
        width: 100%;
      }

      .theme-toggle {
        background: none;
        border: none;
        color: var(--light);
        font-size: 1.2rem;
        cursor: pointer;
        margin-left: 2rem;
      }

      /* Hero Section */
      .hero {
        min-height: 100vh;
        display: flex;
        align-items: center;
        padding: 0 10%;
        position: relative;
        overflow: hidden;
      }

      .hero-content {
        max-width: 600px;
        z-index: 1;
        transform: translateY(50px);
        opacity: 0;
        animation: fadeInUp 1s forwards 0.5s;
      }

      .hero h1 {
        font-size: 3.5rem;
        margin-bottom: 1rem;
        background: linear-gradient(to right, var(--primary), var(--accent));
        -webkit-background-clip: text;
        background-clip: text;
        color: transparent;
      }

      .hero h2 {
        font-size: 1.8rem;
        font-weight: 400;
        margin-bottom: 1.5rem;
        color: var(--light);
      }

      .hero p {
        margin-bottom: 2rem;
        color: rgba(255, 255, 255, 0.8);
      }

      .cta-buttons {
        display: flex;
        gap: 1rem;
      }

      .btn {
        padding: 0.8rem 1.8rem;
        border-radius: 30px;
        font-weight: 600;
        text-decoration: none;
        transition: all 0.3s ease;
      }

      .btn-primary {
        background: var(--accent);
        color: white;
        box-shadow: 0 4px 15px rgba(255, 126, 95, 0.4);
      }

      .btn-primary:hover {
        transform: translateY(-3px);
        box-shadow: 0 6px 20px rgba(255, 126, 95, 0.6);
      }

      .btn-secondary {
        border: 2px solid var(--accent);
        color: var(--accent);
        background: transparent;
      }

      .btn-secondary:hover {
        background: rgba(255, 126, 95, 0.1);
      }

      /* About Section */
      .section {
        padding: 6rem 10%;
      }

      .section-title {
        font-size: 2.5rem;
        margin-bottom: 3rem;
        text-align: center;
        position: relative;
        color: var(--light);
      }

      .section-title::after {
        content: "";
        position: absolute;
        bottom: -10px;
        left: 50%;
        transform: translateX(-50%);
        width: 80px;
        height: 4px;
        background: linear-gradient(to right, var(--primary), var(--accent));
        border-radius: 2px;
      }

      .about-content {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 3rem;
        align-items: center;
      }

      .about-img {
        position: relative;
        max-width: 400px;
        border-radius: 20px;
        overflow: hidden;
        box-shadow: 0 20px 30px rgba(0, 0, 0, 0.3);
        transform: perspective(1000px) rotateY(-10deg);
        transition: transform 0.5s ease;
      }

      .about-img:hover {
        transform: perspective(1000px) rotateY(0deg);
      }

      .about-img img {
        width: 100%;
        display: block;
      }

      .about-img::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(45deg, var(--primary), var(--secondary));
        opacity: 0.3;
        z-index: 1;
      }

      .about-text h3 {
        font-size: 1.8rem;
        margin-bottom: 1.5rem;
        color: var(--light);
      }

      .skills {
        margin-top: 2rem;
      }

      .skill-item {
        margin-bottom: 1.5rem;
      }

      .skill-name {
        display: flex;
        justify-content: space-between;
        margin-bottom: 0.5rem;
      }

      .skill-bar {
        height: 10px;
        background: rgba(255, 255, 255, 0.1);
        border-radius: 5px;
        overflow: hidden;
      }

      .skill-progress {
        height: 100%;
        background: linear-gradient(to right, var(--primary), var(--accent));
        border-radius: 5px;
        position: relative;
        width: 0;
        transition: width 1.5s ease;
      }

      /* Projects Section */
      .projects-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
        gap: 2rem;
      }

      .project-card {
        background: var(--card-bg);
        border-radius: 15px;
        overflow: hidden;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
        transform: translateY(20px);
        opacity: 0;
      }

      .project-card.visible {
        transform: translateY(0);
        opacity: 1;
      }

      .project-card:hover {
        transform: translateY(-10px);
        box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
      }

      .project-img {
        height: 200px;
        overflow: hidden;
      }

      .project-img img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.5s ease;
      }

      .project-card:hover .project-img img {
        transform: scale(1.1);
      }

      .project-info {
        padding: 1.5rem;
      }

      .project-title {
        font-size: 1.5rem;
        margin-bottom: 0.5rem;
        color: var(--light);
      }

      .project-description {
        margin-bottom: 1rem;
        color: var(--text);
      }

      .project-tech {
        display: flex;
        flex-wrap: wrap;
        gap: 0.5rem;
        margin-bottom: 1.5rem;
      }

      .tech-tag {
        background: rgba(110, 69, 226, 0.1);
        color: var(--primary);
        padding: 0.3rem 0.8rem;
        border-radius: 20px;
        font-size: 0.8rem;
        font-weight: 600;
      }

      .project-links {
        display: flex;
        gap: 1rem;
      }

      .project-link {
        display: inline-flex;
        align-items: center;
        gap: 0.5rem;
        color: var(--accent);
        text-decoration: none;
        font-weight: 600;
        transition: all 0.3s ease;
      }

      .project-link:hover {
        color: var(--primary);
        transform: translateX(5px);
      }

      /* Contact Section */
      .contact-container {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 3rem;
      }

      .contact-info {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
      }

      .contact-item {
        display: flex;
        align-items: center;
        gap: 1rem;
      }

      .contact-icon {
        width: 50px;
        height: 50px;
        background: linear-gradient(45deg, var(--primary), var(--secondary));
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        font-size: 1.2rem;
      }

      .contact-text h3 {
        color: var(--light);
        margin-bottom: 0.3rem;
      }

      .contact-form {
        background: var(--card-bg);
        padding: 2rem;
        border-radius: 15px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      }

      .form-group {
        margin-bottom: 1.5rem;
      }

      .form-control {
        width: 100%;
        padding: 1rem;
        border: none;
        background: rgba(255, 255, 255, 0.1);
        border-radius: 8px;
        color: var(--text);
        font-size: 1rem;
      }

      .form-control:focus {
        outline: 2px solid var(--primary);
      }

      textarea.form-control {
        min-height: 150px;
        resize: vertical;
      }

      .submit-btn {
        background: linear-gradient(to right, var(--primary), var(--accent));
        color: white;
        border: none;
        padding: 1rem 2rem;
        border-radius: 8px;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
        width: 100%;
      }

      .submit-btn:hover {
        transform: translateY(-3px);
        box-shadow: 0 5px 15px rgba(110, 69, 226, 0.4);
      }

      /* Footer */
      footer {
        background: var(--dark);
        padding: 2rem 10%;
        text-align: center;
      }

      .social-links {
        display: flex;
        justify-content: center;
        gap: 1.5rem;
        margin-bottom: 1.5rem;
      }

      .social-link {
        width: 45px;
        height: 45px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.1);
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--light);
        font-size: 1.2rem;
        transition: all 0.3s ease;
      }

      .social-link:hover {
        background: var(--accent);
        transform: translateY(-5px);
      }

      .copyright {
        color: rgba(255, 255, 255, 0.7);
        font-size: 0.9rem;
      }

      /* Animations */
      @keyframes fadeInUp {
        from {
          opacity: 0;
          transform: translateY(50px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      @keyframes float {
        0%,
        100% {
          transform: translateY(0);
        }
        50% {
          transform: translateY(-20px);
        }
      }

      /* Responsive Design */
      @media (max-width: 992px) {
        .about-content,
        .contact-container {
          grid-template-columns: 1fr;
        }

        .about-img {
          max-width: 300px;
          margin: 0 auto;
        }
      }

      @media (max-width: 768px) {
        .hero h1 {
          font-size: 2.5rem;
        }

        .hero h2 {
          font-size: 1.4rem;
        }

        .nav-links {
          display: none;
        }

        .projects-grid {
          grid-template-columns: 1fr;
        }
      }
    </style>
  </head>
  <body>
    <!-- Particle Background -->
    <div id="particles-js"></div>

    <!-- Navigation -->
    <nav>
      <a
        href="https://cdn.vectorstock.com/i/preview-2x/47/99/a-logo-vector-47234799.webp"
        class="logo"
        >@SH!SH<span>.</span></a
      >
      <div class="nav-links">
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
      </div>
      <button class="theme-toggle" id="themeToggle">
        <i class="fas fa-moon"></i>
      </button>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <h1>Ashish Lokhande</h1>
        <h2>Computer Science Undergrad & Developer</h2>
        <p>
          I build responsive web applications and visualize algorithms with a
          focus on user experience and clean code.
        </p>
        <div class="cta-buttons">
          <a href="#projects" class="btn btn-primary">View My Work</a>
          <a href="#contact" class="btn btn-secondary">Contact Me</a>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section class="section" id="about">
      <h2 class="section-title">About Me</h2>
      <div class="about-content">
        <div class="about-img">
          <img
            src="https://via.placeholder.com/400x500"
            alt="Ashish Lokhande"
          />
        </div>
        <div class="about-text">
          <p>
            Hi, I'm Ashish Lokhande - a final-year Computer Science student and
            passionate Full Stack Python Developer. I'm skilled in
            Python,Html,CSS, Django, JavaScript, C++, and MySQL, with hands-on
            experience building real-world projects.
          </p>

          <p>
            I've developed apps like a Bank Security System and a Grid Puzzle
            Game, and I'm currently learning Angular and exploring
            cybersecurity. Always learning, always building!
          </p>

          <div class="skills">
            <div class="skill-item">
              <div class="skill-name">
                <span>Python</span>
                <span>92%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-progress" style="width: 92%"></div>
              </div>
            </div>
            <div class="skill-item">
              <div class="skill-name">
                <span>JavaScript</span>
                <span>87%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-progress" style="width: 87%"></div>
              </div>
            </div>
            <div class="skill-item">
              <div class="skill-name">
                <span>HTML/CSS</span>
                <span>95%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-progress" style="width: 95%"></div>
              </div>
            </div>
            <div class="skill-item">
              <div class="skill-name">
                <span>Angular</span>
                <span>85%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-progress" style="width: 85%"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section class="section" id="projects">
      <h2 class="section-title">My Projects</h2>
      <div class="projects-grid">
        <div class="project-card">
          <div class="project-img">
            <img
              src="https://ohzsecurity.com/wp-content/uploads/2023/10/shutterstock_11501807991.jpg"
              alt="Bank Security Project"
            />
          </div>

          <div class="project-info">
            <h3 class="project-title">Bank Security Project</h3>
            <p class="project-description">
              Designed a secure banking system that detects suspicious activity
              and protects user data using advanced Python logic and encryption.
            </p>

            <div class="project-tech">
              <span class="tech-tag">Python</span>
              <span class="tech-tag">MySQL</span>
              <span class="tech-tag">Encryption</span>
              <span class="tech-tag">Security Algorithms</span>
            </div>

            <div class="project-links">
              <a href="#" class="project-link">
                <i class="fas fa-external-link-alt"></i> Live Demo
              </a>
              <a href="#" class="project-link">
                <i class="fab fa-github"></i> View Code
              </a>
            </div>
          </div>
        </div>

        <div class="project-card">
          <div class="project-img">
            <img
              src="https://thumbs.dreamstime.com/b/puzzle-26505553.jpg"
              alt="Grid Puzzle Game"
            />
          </div>

          <div class="project-info">
            <h3 class="project-title">Grid Puzzle Game</h3>
            <p class="project-description">
              Developed a grid-based puzzle game inspired by Ludo logic with
              score tracking, player turns, and dynamic gameplay using Python
              and web technologies.
            </p>

            <div class="project-tech">
              <span class="tech-tag">Python</span>
              <span class="tech-tag">MySQL</span>
              <span class="tech-tag">HTML</span>
              <span class="tech-tag">CSS</span>
              <span class="tech-tag">Angular</span>
            </div>

            <div class="project-links">
              <a href="#" class="project-link">
                <i class="fas fa-external-link-alt"></i> Live Demo
              </a>
              <a href="#" class="project-link">
                <i class="fab fa-github"></i> View Code
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="section" id="contact">
      <h2 class="section-title">Get In Touch</h2>
      <div class="contact-container">
        <div class="contact-info">
          <div class="contact-item">
            <div class="contact-icon">
              <i class="fas fa-map-marker-alt"></i>
            </div>
            <div class="contact-text">
              <h3>Location</h3>
              <p>Ameerpet, Hyderabad</p>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">
              <i class="fas fa-envelope"></i>
            </div>
            <div class="contact-text">
              <h3>Email</h3>
              <p>official.ashish2005@gmail.com</p>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">
              <i class="fas fa-phone-alt"></i>
            </div>
            <div class="contact-text">
              <h3>Phone</h3>
              <p>+917666773084</p>
            </div>
          </div>
        </div>
        <form class="contact-form">
          <div class="form-group">
            <input
              type="text"
              class="form-control"
              placeholder="Your Name"
              required
            />
          </div>
          <div class="form-group">
            <input
              type="email"
              class="form-control"
              placeholder="Your Email"
              required
            />
          </div>
          <div class="form-group">
            <input type="text" class="form-control" placeholder="Subject" />
          </div>
          <div class="form-group">
            <textarea
              class="form-control"
              placeholder="Your Message"
              required
            ></textarea>
          </div>
          <button type="submit" class="submit-btn">Send Message</button>
        </form>
      </div>
    </section>

    <!-- Footer -->
    <footer>
      <div class="social-links">
        <a
          href="https://www.linkedin.com/in/ashish-lokhande-888497313/"
          class="social-link"
          ><i class="fab fa-linkedin-in"></i
        ></a>
        <a href="https://github.com/Ashpatil2003/MyDemo" class="social-link"
          ><i class="fab fa-github"></i
        ></a>
        <a href="https://x.com/AshishLokh14597" class="social-link"
          ><i class="fab fa-twitter"></i
        ></a>
        <a href="https://www.instagram.com/ashpatil503/" class="social-link"
          ><i class="fab fa-instagram"></i
        ></a>
      </div>
      <p class="copyright">© 2025 Ashish Lokhande. All rights reserved.</p>
    </footer>

    <!-- JavaScript -->
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script>
      // Theme Toggle
      const themeToggle = document.getElementById("themeToggle");
      const body = document.body;
      let darkMode = false;

      // Check for saved theme preference
      if (localStorage.getItem("darkMode") === "enabled") {
        enableDarkMode();
      }

      themeToggle.addEventListener("click", () => {
        darkMode = !darkMode;
        if (darkMode) {
          enableDarkMode();
        } else {
          disableDarkMode();
        }
      });

      function enableDarkMode() {
        body.setAttribute("data-theme", "dark");
        themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
        localStorage.setItem("darkMode", "enabled");
        darkMode = true;
      }

      function disableDarkMode() {
        body.removeAttribute("data-theme");
        themeToggle.innerHTML = '<i class="fas fa-moon"></i>';
        localStorage.setItem("darkMode", "disabled");
        darkMode = false;
      }

      // Particles.js Configuration
      particlesJS("particles-js", {
        particles: {
          number: {
            value: 80,
            density: {
              enable: true,
              value_area: 800,
            },
          },
          color: {
            value: "#6e45e2",
          },
          shape: {
            type: "circle",
            stroke: {
              width: 0,
              color: "#000000",
            },
            polygon: {
              nb_sides: 5,
            },
          },
          opacity: {
            value: 0.5,
            random: false,
            anim: {
              enable: false,
              speed: 1,
              opacity_min: 0.1,
              sync: false,
            },
          },
          size: {
            value: 3,
            random: true,
            anim: {
              enable: false,
              speed: 40,
              size_min: 0.1,
              sync: false,
            },
          },
          line_linked: {
            enable: true,
            distance: 150,
            color: "#6e45e2",
            opacity: 0.4,
            width: 1,
          },
          move: {
            enable: true,
            speed: 2,
            direction: "none",
            random: false,
            straight: false,
            out_mode: "out",
            bounce: false,
            attract: {
              enable: false,
              rotateX: 600,
              rotateY: 1200,
            },
          },
        },
        interactivity: {
          detect_on: "canvas",
          events: {
            onhover: {
              enable: true,
              mode: "grab",
            },
            onclick: {
              enable: true,
              mode: "push",
            },
            resize: true,
          },
          modes: {
            grab: {
              distance: 140,
              line_linked: {
                opacity: 1,
              },
            },
            bubble: {
              distance: 400,
              size: 40,
              duration: 2,
              opacity: 8,
              speed: 3,
            },
            repulse: {
              distance: 200,
              duration: 0.4,
            },
            push: {
              particles_nb: 4,
            },
            remove: {
              particles_nb: 2,
            },
          },
        },
        retina_detect: true,
      });

      // Scroll Animation
      const projectCards = document.querySelectorAll(".project-card");
      const skillBars = document.querySelectorAll(".skill-progress");

      function checkScroll() {
        projectCards.forEach((card, index) => {
          const cardTop = card.getBoundingClientRect().top;
          if (cardTop < window.innerHeight - 100) {
            setTimeout(() => {
              card.classList.add("visible");
            }, index * 200);
          }
        });

        skillBars.forEach((bar) => {
          const barTop = bar.getBoundingClientRect().top;
          if (barTop < window.innerHeight - 100 && !bar.style.width) {
            const width =
              bar.parentElement.previousElementSibling.lastElementChild
                .textContent;
            bar.style.width = width;
          }
        });
      }

      window.addEventListener("scroll", checkScroll);
      window.addEventListener("load", checkScroll);
    </script>
  </body>
</html>
