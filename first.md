```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alex Chen - Product Designer & Developer</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #0f172a;
            --secondary: #1e293b;
            --accent: #3b82f6;
            --accent-light: #60a5fa;
            --text: #e2e8f0;
            --text-secondary: #cbd5e1;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background: linear-gradient(135deg, var(--primary) 0%, #1a1f3a 100%);
            color: var(--text);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow-x: hidden;
            position: relative;
        }

        /* Background animation */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 50%, rgba(59, 130, 246, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 80% 80%, rgba(59, 130, 246, 0.05) 0%, transparent 50%);
            pointer-events: none;
            z-index: -1;
        }

        /* Navbar */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            background: rgba(15, 23, 42, 0.7);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(59, 130, 246, 0.1);
            transition: all 0.3s ease;
        }

        .navbar.scrolled {
            background: rgba(15, 23, 42, 0.95);
            border-bottom: 1px solid rgba(59, 130, 246, 0.2);
        }

        .navbar-content {
            max-width: 1400px;
            margin: 0 auto;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--accent-light) 0%, var(--accent) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: -1px;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-secondary);
            text-decoration: none;
            font-size: 0.95rem;
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s ease;
        }

        .nav-links a:hover,
        .nav-links a.active {
            color: var(--accent);
        }

        .nav-links a:hover::after,
        .nav-links a.active::after {
            width: 100%;
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 2rem;
            margin-top: 60px;
        }

        .hero-content {
            max-width: 900px;
            text-align: center;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .hero-subtitle {
            color: var(--accent);
            font-size: 1rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            margin-bottom: 1rem;
            font-weight: 600;
        }

        .hero-title {
            font-size: 4.5rem;
            font-weight: 900;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            letter-spacing: -2px;
        }

        .hero-title .gradient-text {
            background: linear-gradient(135deg, var(--accent-light) 0%, #1e90ff 50%, var(--accent) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero-description {
            font-size: 1.2rem;
            color: var(--text-secondary);
            margin-bottom: 2rem;
            line-height: 1.8;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            animation: fadeInUp 1s ease 0.4s both;
        }

        .btn {
            padding: 1rem 2.5rem;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            border: 2px solid transparent;
            cursor: pointer;
            font-size: 1rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--accent-light) 0%, var(--accent) 100%);
            color: white;
            box-shadow: 0 10px 30px rgba(59, 130, 246, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(59, 130, 246, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: var(--accent);
            border: 2px solid var(--accent);
        }

        .btn-secondary:hover {
            background: rgba(59, 130, 246, 0.1);
            transform: translateY(-3px);
        }

        @media (max-width: 768px) {
            .hero-title {
                font-size: 2.5rem;
            }

            .hero-description {
                font-size: 1rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .btn {
                width: 100%;
                max-width: 300px;
            }
        }

        /* Scroll Indicator */
        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
        }

        .scroll-indicator svg {
            width: 24px;
            height: 24px;
            stroke: var(--accent);
        }

        @keyframes bounce {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(10px); }
        }

        /* Projects Section */
        .section {
            padding: 6rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 3rem;
            font-weight: 900;
            margin-bottom: 3rem;
            text-align: center;
            letter-spacing: -1px;
        }

        .section-title .accent {
            background: linear-gradient(135deg, var(--accent-light) 0%, var(--accent) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: rgba(30, 41, 59, 0.5);
            border: 1px solid rgba(59, 130, 246, 0.1);
            border-radius: 12px;
            overflow: hidden;
            transition: all 0.3s ease;
            cursor: pointer;
            backdrop-filter: blur(10px);
            position: relative;
            group: 'card';
        }

        .project-card:hover {
            border-color: rgba(59, 130, 246, 0.3);
            background: rgba(30, 41, 59, 0.7);
            transform: translateY(-8px);
            box-shadow: 0 20px 50px rgba(59, 130, 246, 0.15);
        }

        .project-image {
            width: 100%;
            height: 250px;
            background: linear-gradient(135deg, rgba(59, 130, 246, 0.1) 0%, rgba(59, 130, 246, 0.05) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            overflow: hidden;
            position: relative;
        }

        .project-image::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(255, 255, 255, 0.1) 50%, transparent 70%);
            transform: translateX(-100%);
            transition: transform 0.6s ease;
        }

        .project-card:hover .project-image::after {
            transform: translateX(100%);
        }

        .project-content {
            padding: 2rem;
        }

        .project-tag {
            display: inline-block;
            background: rgba(59, 130, 246, 0.1);
            color: var(--accent-light);
            padding: 0.4rem 0.8rem;
            border-radius: 4px;
            font-size: 0.75rem;
            font-weight: 600;
            margin-bottom: 1rem;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .project-title {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 0.8rem;
        }

        .project-description {
            color: var(--text-secondary);
            font-size: 0.95rem;
            line-height: 1.6;
            margin-bottom: 1.5rem;
        }

        .project-tech {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }

        .tech-badge {
            background: rgba(59, 130, 246, 0.2);
            color: var(--accent-light);
            padding: 0.25rem 0.75rem;
            border-radius: 20px;
            font-size: 0.8rem;
            border: 1px solid rgba(59, 130, 246, 0.3);
        }

        /* Skills Section */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .skill-card {
            background: rgba(30, 41, 59, 0.5);
            border: 1px solid rgba(59, 130, 246, 0.1);
            border-radius: 12px;
            padding: 2rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            text-align: center;
        }

        .skill-card:hover {
            border-color: rgba(59, 130, 246, 0.3);
            background: rgba(30, 41, 59, 0.7);
            transform: translateY(-5px);
        }

        .skill-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: var(--accent);
        }

        .skill-title {
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 0.8rem;
        }

        .skill-description {
            color: var(--text-secondary);
            font-size: 0.95rem;
            line-height: 1.6;
        }

        /* Stats Section */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .stat-box {
            text-align: center;
            padding: 2rem;
            background: rgba(30, 41, 59, 0.5);
            border-radius: 12px;
            border: 1px solid rgba(59, 130, 246, 0.1);
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 900;
            background: linear-gradient(135deg, var(--accent-light) 0%, var(--accent) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: var(--text-secondary);
            font-size: 0.95rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Contact Section */
        .contact-section {
            text-align: center;
            padding: 4rem 2rem;
        }

        .contact-description {
            font-size: 1.2rem;
            color: var(--text-secondary);
            margin-bottom: 2rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            line-height: 1.8;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-top: 2rem;
            flex-wrap: wrap;
        }

        .social-link {
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(59, 130, 246, 0.1);
            border: 2px solid rgba(59, 130, 246, 0.2);
            border-radius: 50%;
            color: var(--accent);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            background: var(--accent);
            color: white;
            transform: translateY(-5px);
            border-color: var(--accent);
        }

        /* Footer */
        footer {
            background: rgba(15, 23, 42, 0.8);
            border-top: 1px solid rgba(59, 130, 246, 0.1);
            padding: 2rem;
            text-align: center;
            color: var(--text-secondary);
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .fade-in-up {
            animation: fadeInUp 0.8s ease both;
        }

        .slide-in-left {
            animation: slideInLeft 0.8s ease both;
        }

        .slide-in-right {
            animation: slideInRight 0.8s ease both;
        }

        /* Responsive Design */
        @media (max-width: 1024px) {
            .section {
                padding: 4rem 1.5rem;
            }

            .section-title {
                font-size: 2.5rem;
            }
        }

        @media (max-width: 640px) {
            .hero {
                min-height: calc(100vh - 60px);
                padding: 1rem;
            }

            .hero-title {
                font-size: 2rem;
            }

            .section {
                padding: 3rem 1rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .skills-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Loading animation */
        .loading-spinner {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(59, 130, 246, 0.3);
            border-top-color: var(--accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Form Styles */
        .form-group {
            margin-bottom: 1.5rem;
            text-align: left;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--text-secondary);
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.75rem;
            background: rgba(30, 41, 59, 0.5);
            border: 1px solid rgba(59, 130, 246, 0.2);
            border-radius: 6px;
            color: var(--text);
            font-family: inherit;
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--accent);
            background: rgba(30, 41, 59, 0.7);
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 120px;
        }

        /* Glow effect */
        .glow {
            position: relative;
        }

        .glow::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(59, 130, 246, 0.2) 0%, transparent 70%);
            opacity: 0;
            animation: glow-pulse 3s ease-in-out infinite;
        }

        @keyframes glow-pulse {
            0%, 100% { opacity: 0; transform: scale(0.8); }
            50% { opacity: 1; transform: scale(1); }
        }

        /* Divider */
        .divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(59, 130, 246, 0.3), transparent);
            margin: 3rem 0;
        }

        /* Floating animation */
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        .float {
            animation: float 3s ease-in-out infinite;
        }

        .float:nth-child(2) {
            animation-delay: 0.3s;
        }

        .float:nth-child(3) {
            animation-delay: 0.6s;
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <div class="navbar-content">
            <div class="logo">AC</div>
            <ul class="nav-links">
                <li><a href="#home" class="nav-link active">Home</a></li>
                <li><a href="#projects" class="nav-link">Projects</a></li>
                <li><a href="#skills" class="nav-link">Skills</a></li>
                <li><a href="#contact" class="nav-link">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-content">
            <p class="hero-subtitle">Welcome to my portfolio</p>
            <h1 class="hero-title">
                I'm <span class="gradient-text">Alex Chen</span>, a creative
                <span class="gradient-text">Product Designer</span> & <span class="gradient-text">Developer</span>
            </h1>
            <p class="hero-description">
                Crafting beautiful, functional digital experiences with a focus on user-centered design and modern development practices. Let's build something amazing together.
            </p>
            <div class="cta-buttons">
                <a href="#projects" class="btn btn-primary">View My Work</a>
                <a href="#contact" class="btn btn-secondary">Get In Touch</a>
            </div>
        </div>
        <div class="scroll-indicator">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
        </div>
    </section>

    <!-- Projects Section -->
    <section class="section" id="projects">
        <h2 class="section-title">Featured <span class="accent">Projects</span></h2>
        <div class="projects-grid">
            <div class="project-card">
                <div class="project-image">💼</div>
                <div class="project-content">
                    <span class="project-tag">Web Design</span>
                    <h3 class="project-title">Enterprise Dashboard</h3>
                    <p class="project-description">
                        A comprehensive analytics dashboard for Fortune 500 companies with real-time data visualization and advanced filtering capabilities.
                    </p>
                    <div class="project-tech">
                        <span class="tech-badge">React</span>
                        <span class="tech-badge">TypeScript</span>
                        <span class="tech-badge">Tailwind</span>
                    </div>
                </div>
            </div>

            <div class="project-card">
                <div class="project-image">🛍️</div>
                <div class="project-content">
                    <span class="project-tag">E-Commerce</span>
                    <h3 class="project-title">Fashion Store</h3>
                    <p class="project-description">
                        Modern e-commerce platform featuring AI-powered recommendations, seamless checkout, and personalized shopping experience.
                    </p>
                    <div class="project-tech">
                        <span class="tech-badge">Next.js</span>
                        <span class="tech-badge">Node.js</span>
                        <span class="tech-badge">MongoDB</span>
                    </div>
                </div>
            </div>

            <div class="project-card">
                <div class="project-image">📱</div>
                <div class="project-content">
                    <span class="project-tag">Mobile App</span>
                    <h3 class="project-title">Fitness Tracker</h3>
                    <p class="project-description">
                        iOS and Android app for tracking workouts with social features, achievement badges, and personalized fitness recommendations.
                    </p>
                    <div class="project-tech">
                        <span class="tech-badge">React Native</span>
                        <span class="tech-badge">Firebase</span>
                        <span class="tech-badge">Redux</span>
                    </div>
                </div>
            </div>

            <div class="project-card">
                <div class="project-image">🎨</div>
                <div class="project-content">
                    <span class="project-tag">UI/UX Design</span>
                    <h3 class="project-title">Design System</h3>
                    <p class="project-description">
                        Comprehensive design system and component library for consistent branding across all digital products and platforms.
                    </p>
                    <div class="project-tech">
                        <span class="tech-badge">Figma</span>
                        <span class="tech-badge">Storybook</span>
                        <span class="tech-badge">CSS</span>
                    </div>
                </div>
            </div>

            <div class="project-card">
                <div class="project-image">📊</div>
                <div class="project-content">
                    <span class="project-tag">Data Visualization</span>
                    <h3 class="project-title">Analytics Platform</h3>
                    <p class="project-description">
                        Interactive data visualization platform with custom charts, real-time updates, and exportable reports for business intelligence.
                    </p>
                    <div class="project-tech">
                        <span class="tech-badge">D3.js</span>
                        <span class="tech-badge">Vue.js</span>
                        <span class="tech-badge">WebSocket</span>
                    </div>
                </div>
            </div>

            <div class="project-card">
                <div class="project-image">🎮</div>
                <div class="project-content">
                    <span class="project-tag">Interactive</span>
                    <h3 class="project-title">3D Experience</h3>
                    <p class="project-description">
                        Immersive 3D web experience with interactive elements, smooth animations, and cross-browser compatibility.
                    </p>
                    <div class="project-tech">
                        <span class="tech-badge">Three.js</span>
                        <span class="tech-badge">GSAP</span>
                        <span class="tech-badge">WebGL</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="divider"></div>

        <!-- Stats -->
        <div class="stats-container">
            <div class="stat-box">
                <div class="stat-number" data-target="50">0</div>
                <div class="stat-label">Projects Completed</div>
            </div>
            <div class="stat-box">
                <div class="stat-number" data-target="200">0</div>
                <div class="stat-label">Happy Clients</div>
            </div>
            <div class="stat-box">
                <div class="stat-number" data-target="8">0</div>
                <div class="stat-label">Years Experience</div>
            </div>
            <div class="stat-box">
                <div class="stat-number" data-target="15">0</div>
                <div class="stat-label">Awards Won</div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section class="section" id="skills">
        <h2 class="section-title">My <span class="accent">Skills</span></h2>
        <div class="skills-grid">
            <div class="skill-card">
                <div class="skill-icon">
                    <i class="fas fa-pencil-ruler"></i>
                </div>
                <h3 class="skill-title">UI/UX Design</h3>
                <p class="skill-description">
                    Creating intuitive, beautiful interfaces with a deep understanding of user psychology and behavior patterns.
                </p>
            </div>

            <div class="skill-card">
                <div class="skill-icon">
                    <i class="fas fa-code"></i>
                </div>
                <h3 class="skill-title">Frontend Development</h3>
                <p class="skill-description">
                    Building responsive, performant web applications using modern frameworks and best practices.
                </p>
            </div>

            <div class="skill-card">
                <div class="skill-icon">
                    <i class="fas fa-server"></i>
                </div>
                <h3 class="skill-title">Backend Development</h3>
                <p class="skill-description">
                    Designing scalable architectures and robust APIs with Node.js, Python, and cloud technologies.
                </p>
            </div>

            <div class="skill-card">
                <div class="skill-icon">
                    <i class="fas fa-mobile-alt"></i>
                </div>
                <h3 class="skill-title">Mobile Development</h3>
                <p class="skill-description">
                    Creating native and cross-platform mobile applications with exceptional user experiences.
                </p>
            </div>

            <div class="skill-card">
                <div class="skill-icon">
                    <i class="fas fa-chart-line"></i>
                </div>
                <h3 class="skill-title">Data Visualization</h3>
                <p class="skill-description">
                    Transforming complex data into compelling visual stories using D3.js and modern charting libraries.
                </p>
            </div>

            <div class="skill-card">
                <div class="skill-icon">
                    <i class="fas fa-cube"></i>
                </div>
                <h3 class="skill-title">3D & Animation</h3>
                <p class="skill-description">
                    Creating engaging 3D experiences and smooth animations with Three.js, GSAP, and WebGL.
                </p>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="section contact-section" id="contact">
        <h2 class="section-title">Let's <span class="accent">Connect</span></h2>
        <p class="contact-description">
            I'm always interested in hearing about new projects and opportunities. Feel free to reach out if you'd like to collaborate or just chat!
        </p>
        <a href="mailto:hello@alexchen.com" class="btn btn-primary">Send Me an Email</a>
        
        <div class="social-links">
            <a href="#" class="social-link" title="LinkedIn">
                <i class="fab fa-linkedin-in"></i>
            </a>
            <a href="#" class="social-link" title="GitHub">
                <i class="fab fa-github"></i>
            </a>
            <a href="#" class="social-link" title="Twitter">
                <i class="fab fa-twitter"></i>
            </a>
            <a href="#" class="social-link" title="Dribbble">
                <i class="fab fa-dribbble"></i>
            </a>
            <a href="#" class="social-link" title="Instagram">
                <i class="fab fa-instagram"></i>
            </a>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2024 Alex Chen. All rights reserved. | Designed & Developed with <span style="color: #ef4444;">❤</span></p>
    </footer>

    <script>
        // Initialize GSAP
        gsap.registerPlugin(ScrollTrigger);

        // Navbar active link and scroll effect
        const navLinks = document.querySelectorAll('.nav-link');
        const navbar = document.querySelector('.navbar');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }

            // Update active nav link
            let current = '';
            const sections = document.querySelectorAll('section');
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                if (pageYOffset >= sectionTop - 200) {
                    current = section.getAttribute('id');
                }
            });

            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href').slice(1) === current) {
                    link.classList.add('active');
                }
            });
        });

        // Smooth scroll for nav links
        navLinks.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const targetId = link.getAttribute('href');
                const targetSection = document.querySelector(targetId);
                targetSection.scrollIntoView({ behavior: 'smooth' });
            });
        });

        // Animate project cards on scroll
        gsap.utils.toArray('.project-card').forEach((card, index) => {
            gsap.from(card, {
                scrollTrigger: {
                    trigger: card,
                    start: 'top 80%',
                    toggleActions: 'play none none reverse'
                },
                opacity: 0,
                y: 50,
                duration: 0.8,
                delay: index * 0.1
            });
        });

        // Animate skill cards
        gsap.utils.toArray('.skill-card').forEach((card, index) => {
            gsap.from(card, {
                scrollTrigger: {
                    trigger: card,
                    start: 'top 80%',
                    toggleActions: 'play none none reverse'
                },
                opacity: 0,
                y: 50,
                duration: 0.8,
                delay: index * 0.1
            });
        });

        // Animate stat numbers
        gsap.utils.toArray('.stat-number').forEach(stat => {
            const target = parseInt(stat.getAttribute('data-target'));
            gsap.from(stat, {
                scrollTrigger: {
                    trigger: stat,
                    start: 'top 80%',
                    toggleActions: 'play none none reverse'
                },
                textContent: 0,
                duration: 2,
                snap: { textContent: 1 },
                onUpdate: function() {
                    stat.textContent = Math.round(parseFloat(stat.textContent));
                }
            });
        });

        // Animate section titles
        gsap.utils.toArray('.section-title').forEach(title => {
            gsap.from(title, {
                scrollTrigger: {
                    trigger: title,
                    start: 'top 80%',
                    toggleActions: 'play none none reverse'
                },
                opacity: 0,
                y: 30,
                duration: 0.8
            });
        });

        // Parallax effect for hero
        gsap.to('.hero-content', {
            scrollTrigger: {
                trigger: '.hero',
                start: 'top top',
                end: 'bottom top',
                scrub: 1
            },
            y: 100,
            opacity: 0.7
        });

        // Add hover animation for social links
        document.querySelectorAll('.social-link').forEach(link => {
            link.addEventListener('mouseenter', function() {
                gsap.to(this, { scale: 1.2, duration: 0.3 });
            });
            link.addEventListener('mouseleave', function() {
                gsap.to(this, { scale: 1, duration: 0.3 });
            });
        });

        // Button click animations
        document.querySelectorAll('.btn').forEach(btn => {
            btn.addEventListener('click', function(e) {
                const ripple = document.createElement('div');
                ripple.style.position = 'absolute';
                ripple.style.width = '20px';
                ripple.style.height = '20px';
                ripple.style.background = 'rgba(255, 255, 255, 0.5)';
                ripple.style.borderRadius = '50%';
                ripple.style.pointerEvents = 'none';
                
                const rect = this.getBoundingClientRect();
                ripple.style.left = (e.clientX - rect.left - 10) + 'px';
                ripple.style.top = (e.clientY - rect.top - 10) + 'px';
                
                this.style.position = 'relative';
                this.style.overflow = 'hidden';
                this.appendChild(ripple);

                gsap.to(ripple, {
                    width: 300,
                    height: 300,
                    opacity: 0,
                    duration: 0.6,
                    ease: 'power2.out',
                    onComplete: () => ripple.remove()
                });
            });
        });

        // Page load animation
        window.addEventListener('load', () => {
            gsap.from('.hero-content', {
                opacity: 0,
                y: 50,
                duration: 1,
                ease: 'power2.out'
            });
        });

        // Mouse follow effect for hero
        const heroSection = document.querySelector('.hero');
        let mouseX = 0;
        let mouseY = 0;

        document.addEventListener('mousemove', (e) => {
            mouseX = e.clientX;
            mouseY = e.clientY;
        });

        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.project-card, .skill-card').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            observer.observe(el);
        });
    </script>
</body>
</html>
```
