# Animate-the-UI-like-a-pro
A modern one-page landing built with HTML, CSS, and GSAP. Includes animated gradient background, navbar slide-in, scroll-triggered fade-ins, and pulsing CTA button.A modern one-page landing built with HTML, CSS, and GSAP. Includes animated gradient background, navbar slide-in, scroll-triggered fade-ins, and pulsing CTA button.
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script><script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BuildBand | Animated Landing</title>
  <style>
    * {
      margin: 0; padding: 0; box-sizing: border-box;
    }
    html, body {
      height: 100%;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      overflow-x: hidden;
    }

    body {
      background: linear-gradient(-45deg, #6a11cb, #2575fc, #ff6f61, #42e695);
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
      color: white;
    }

    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    .navbar {
      width: 100%;
      padding: 20px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: fixed;
      top: 0;
      left: 0;
      background: rgba(0,0,0,0.3);
      z-index: 10;
      opacity: 0;
    }

    .navbar h2 {
      font-size: 1.5rem;
      letter-spacing: 1px;
    }

    .hero {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 0 20px;
    }

    .hero h1 {
      font-size: 3.5rem;
      margin-bottom: 20px;
    }

    .hero p {
      font-size: 1.2rem;
      max-width: 600px;
      margin-bottom: 30px;
    }

    .btn {
      background-color: white;
      color: #2575fc;
      padding: 12px 30px;
      font-size: 1.1rem;
      font-weight: bold;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: transform 0.2s ease;
    }

    .section {
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      opacity: 0;
    }

    @media (max-width: 768px) {
      .hero h1 {
        font-size: 2.5rem;
      }
      .hero p {
        font-size: 1rem;
      }
    }
  </style>
</head>
<body>

  <nav class="navbar">
    <h2>BuildBand</h2>
  </nav>

  <section class="hero">
    <h1 class="fade-in">Welcome to BuildBand</h1>
    <p class="fade-in">We design experiences that move people. Let’s build something amazing together.</p>
    <button class="btn pulse">Get Started</button>
  </section>

  <section class="section fade-in">
    🚀 Scroll Animation Triggered
  </section>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
  <script>
    // Navbar slide in
    gsap.to(".navbar", {
      y: 0,
      opacity: 1,
      duration: 1,
      ease: "power2.out"
    });

    // Hero text fade in
    gsap.utils.toArray('.fade-in').forEach((el, i) => {
      gsap.fromTo(el, {
        opacity: 0,
        y: 40
      }, {
        opacity: 1,
        y: 0,
        delay: i * 0.3,
        duration: 1,
        ease: "power2.out"
      });
    });

    // Button pulse infinite
    gsap.to(".pulse", {
      scale: 1.05,
      repeat: -1,
      yoyo: true,
      ease: "power1.inOut",
      duration: 1
    });

    // Scroll-triggered fade in
    gsap.utils.toArray(".section").forEach(section => {
      gsap.to(section, {
        opacity: 1,
        y: -20,
        duration: 1.2,
        scrollTrigger: {
          trigger: section,
          start: "top 80%",
          toggleActions: "play none none reverse"
        }
      });
    });
  </script>
</body>
</html>
