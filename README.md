<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>MARTIAN DRONES— Futuristic Aerial Solutions</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;900&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
    <style>
        /* ───────── RESET & BASE ───────── */
        *,
        *::before,
        *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        html {
            scroll-behavior: smooth;
        }
        body {
            font-family: 'Inter', sans-serif;
            background: #0a0a1a;
            color: #e0e0f0;
            overflow-x: hidden;
            line-height: 1.6;
        }
        a {
            text-decoration: none;
            color: inherit;
        }
        img {
            max-width: 100%;
            display: block;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 24px;
        }
        section {
            padding: 100px 0;
            position: relative;
        }

        /* ───────── SCROLLBAR ───────── */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0a0a1a;
        }
        ::-webkit-scrollbar-thumb {
            background: #00f0ff;
            border-radius: 10px;
            box-shadow: 0 0 20px #00f0ff55;
        }

        /* ───────── CANVAS BACKGROUND ───────── */
        #particleCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* ───────── UTILITY ───────── */
        .glow-text {
            text-shadow: 0 0 20px rgba(0, 240, 255, 0.3), 0 0 60px rgba(0, 240, 255, 0.1);
        }
        .section-label {
            font-family: 'Orbitron', sans-serif;
            font-size: 0.75rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: #00f0ff;
            margin-bottom: 12px;
            display: inline-block;
            border: 1px solid #00f0ff44;
            padding: 4px 16px;
            border-radius: 30px;
            backdrop-filter: blur(4px);
            background: rgba(0, 240, 255, 0.05);
        }
        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(2rem, 5vw, 3.2rem);
            font-weight: 700;
            margin-bottom: 16px;
            line-height: 1.2;
        }
        .section-title span {
            color: #00f0ff;
        }
        .section-desc {
            font-size: 1.05rem;
            color: #aaaacc;
            max-width: 600px;
            margin-bottom: 48px;
        }
        .btn-primary {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: linear-gradient(135deg, #00f0ff, #0066ff);
            color: #0a0a1a;
            font-weight: 600;
            padding: 14px 36px;
            border-radius: 50px;
            font-size: 0.95rem;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 0 30px rgba(0, 240, 255, 0.25);
            font-family: 'Inter', sans-serif;
            letter-spacing: 0.5px;
        }
        .btn-primary:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 0 50px rgba(0, 240, 255, 0.45);
        }
        .btn-outline {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: transparent;
            color: #00f0ff;
            font-weight: 500;
            padding: 13px 34px;
            border-radius: 50px;
            font-size: 0.95rem;
            border: 1.5px solid #00f0ff66;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Inter', sans-serif;
        }
        .btn-outline:hover {
            background: rgba(0, 240, 255, 0.08);
            box-shadow: 0 0 30px rgba(0, 240, 255, 0.15);
            border-color: #00f0ff;
        }

        /* ───────── GLASS CARD ───────── */
        .glass-card {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.06);
            border-radius: 24px;
            padding: 32px;
            transition: all 0.4s ease;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
        }
        .glass-card:hover {
            border-color: rgba(0, 240, 255, 0.25);
            box-shadow: 0 8px 48px rgba(0, 240, 255, 0.08);
            transform: translateY(-6px);
        }

        /* ───────── NAVIGATION ───────── */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            padding: 18px 0;
            transition: all 0.4s ease;
            background: transparent;
        }
        .navbar.scrolled {
            background: rgba(10, 10, 26, 0.85);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            padding: 12px 0;
        }
        .navbar .container {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .logo {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            font-weight: 900;
            letter-spacing: 2px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .logo .icon {
            display: inline-block;
            width: 28px;
            height: 28px;
            background: linear-gradient(135deg, #00f0ff, #0066ff);
            border-radius: 50%;
            box-shadow: 0 0 30px #00f0ff55;
            animation: pulse-glow 2s ease-in-out infinite;
        }
        @keyframes pulse-glow {
            0%,
            100% {
                box-shadow: 0 0 20px #00f0ff55;
            }
            50% {
                box-shadow: 0 0 50px #00f0ffaa;
            }
        }
        .logo span {
            color: #00f0ff;
        }
        .nav-links {
            display: flex;
            align-items: center;
            gap: 32px;
            list-style: none;
        }
        .nav-links a {
            font-size: 0.85rem;
            font-weight: 500;
            letter-spacing: 0.5px;
            color: #aaaacc;
            transition: color 0.3s;
            position: relative;
        }
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            width: 0;
            height: 2px;
            background: #00f0ff;
            transition: width 0.3s;
            box-shadow: 0 0 12px #00f0ff;
        }
        .nav-links a:hover {
            color: #fff;
        }
        .nav-links a:hover::after {
            width: 100%;
        }
        .nav-cta {
            background: linear-gradient(135deg, #00f0ff, #0066ff);
            color: #0a0a1a !important;
            padding: 8px 22px;
            border-radius: 30px;
            font-weight: 600 !important;
        }
        .nav-cta::after {
            display: none !important;
        }
        .nav-cta:hover {
            box-shadow: 0 0 30px #00f0ff55;
            transform: scale(1.04);
        }
        .hamburger {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            background: none;
            border: none;
            padding: 4px;
        }
        .hamburger span {
            width: 28px;
            height: 2px;
            background: #e0e0f0;
            border-radius: 2px;
            transition: all 0.3s;
        }
        .hamburger.active span:nth-child(1) {
            transform: rotate(45deg) translate(5px, 5px);
        }
        .hamburger.active span:nth-child(2) {
            opacity: 0;
        }
        .hamburger.active span:nth-child(3) {
            transform: rotate(-45deg) translate(5px, -5px);
        }

        /* ───────── HERO ───────── */
        #hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding-top: 80px;
            position: relative;
            z-index: 1;
        }
        #hero .container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }
        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: rgba(0, 240, 255, 0.08);
            border: 1px solid #00f0ff33;
            border-radius: 50px;
            padding: 6px 18px 6px 8px;
            font-size: 0.8rem;
            font-weight: 500;
            color: #00f0ff;
            margin-bottom: 24px;
            backdrop-filter: blur(4px);
        }
        .hero-badge .dot {
            width: 8px;
            height: 8px;
            background: #00f0ff;
            border-radius: 50%;
            animation: pulse-dot 1.5s ease-in-out infinite;
        }
        @keyframes pulse-dot {
            0%,
            100% {
                opacity: 1;
                transform: scale(1);
            }
            50% {
                opacity: 0.4;
                transform: scale(0.7);
            }
        }
        .hero-title {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(2.8rem, 7vw, 4.8rem);
            font-weight: 900;
            line-height: 1.05;
            margin-bottom: 20px;
        }
        .hero-title .highlight {
            background: linear-gradient(135deg, #00f0ff, #7b61ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .hero-sub {
            font-size: 1.1rem;
            color: #8888bb;
            max-width: 480px;
            margin-bottom: 36px;
        }
        .hero-actions {
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
        }
        .hero-visual {
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }
        .drone-3d {
            width: 100%;
            max-width: 480px;
            aspect-ratio: 1/1;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .drone-3d .ring {
            position: absolute;
            border-radius: 50%;
            border: 1.5px solid rgba(0, 240, 255, 0.15);
            animation: spin-ring 20s linear infinite;
        }
        .drone-3d .ring:nth-child(1) {
            width: 100%;
            height: 100%;
            border-color: rgba(0, 240, 255, 0.08);
            animation-duration: 30s;
        }
        .drone-3d .ring:nth-child(2) {
            width: 75%;
            height: 75%;
            border-color: rgba(123, 97, 255, 0.12);
            animation-duration: 20s;
            animation-direction: reverse;
        }
        .drone-3d .ring:nth-child(3) {
            width: 50%;
            height: 50%;
            border-color: rgba(0, 240, 255, 0.18);
            animation-duration: 15s;
        }
        @keyframes spin-ring {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
        .drone-icon {
            font-size: 8rem;
            filter: drop-shadow(0 0 60px rgba(0, 240, 255, 0.3));
            animation: float-drone 4s ease-in-out infinite;
            position: relative;
            z-index: 2;
            background: linear-gradient(135deg, #00f0ff, #7b61ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        @keyframes float-drone {
            0%,
            100% {
                transform: translateY(0px) rotate(0deg);
            }
            50% {
                transform: translateY(-20px) rotate(2deg);
            }
        }
        .hero-stats {
            position: absolute;
            bottom: -20px;
            left: 0;
            right: 0;
            display: flex;
            justify-content: center;
            gap: 48px;
            background: rgba(10, 10, 26, 0.7);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 20px 32px;
            max-width: 420px;
            margin: 0 auto;
        }
        .hero-stats .stat {
            text-align: center;
        }
        .hero-stats .stat-number {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.6rem;
            font-weight: 700;
            color: #00f0ff;
        }
        .hero-stats .stat-label {
            font-size: 0.7rem;
            color: #8888bb;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        /* ───────── ABOUT ───────── */
        #about {
            z-index: 1;
            position: relative;
        }
        #about .container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }
        .about-features {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-top: 32px;
        }
        .about-feature {
            padding: 20px;
            border-radius: 16px;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.04);
            transition: all 0.3s;
        }
        .about-feature:hover {
            border-color: rgba(0, 240, 255, 0.2);
            background: rgba(0, 240, 255, 0.04);
        }
        .about-feature .icon {
            font-size: 1.8rem;
            margin-bottom: 8px;
        }
        .about-feature h4 {
            font-weight: 600;
            margin-bottom: 4px;
            font-size: 1rem;
        }
        .about-feature p {
            font-size: 0.85rem;
            color: #8888bb;
        }
        .about-visual {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }
        .about-grid .box {
            aspect-ratio: 1/1;
            border-radius: 20px;
            background: linear-gradient(135deg, rgba(0, 240, 255, 0.05), rgba(123, 97, 255, 0.05));
            border: 1px solid rgba(255, 255, 255, 0.04);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            transition: all 0.4s;
        }
        .about-grid .box:hover {
            border-color: rgba(0, 240, 255, 0.2);
            transform: scale(1.02);
        }
        .about-grid .box.large {
            grid-column: 1 / -1;
            aspect-ratio: 2/1;
            font-size: 5rem;
            background: linear-gradient(135deg, rgba(0, 240, 255, 0.08), rgba(123, 97, 255, 0.08));
        }

        /* ───────── SERVICES ───────── */
        #services {
            z-index: 1;
            position: relative;
            background: radial-gradient(ellipse at 50% 0%, rgba(0, 240, 255, 0.03) 0%, transparent 70%);
        }
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 28px;
        }
        .service-card {
            text-align: center;
            padding: 40px 28px;
            border-radius: 24px;
            background: rgba(255, 255, 255, 0.02);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }
        .service-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(from 0deg, transparent, rgba(0, 240, 255, 0.03), transparent, rgba(123, 97, 255, 0.03), transparent);
            animation: rotate-glow 10s linear infinite;
            opacity: 0;
            transition: opacity 0.6s;
        }
        .service-card:hover::before {
            opacity: 1;
        }
        @keyframes rotate-glow {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
        .service-card>* {
            position: relative;
            z-index: 1;
        }
        .service-card .icon {
            font-size: 3rem;
            margin-bottom: 16px;
            display: block;
        }
        .service-card h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 8px;
        }
        .service-card p {
            color: #8888bb;
            font-size: 0.9rem;
        }
        .service-card:hover {
            transform: translateY(-8px);
            border-color: rgba(0, 240, 255, 0.2);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
        }
        .service-card .badge {
            display: inline-block;
            margin-top: 16px;
            font-size: 0.7rem;
            padding: 4px 14px;
            border-radius: 30px;
            background: rgba(0, 240, 255, 0.1);
            color: #00f0ff;
            border: 1px solid rgba(0, 240, 255, 0.15);
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        /* ───────── CONTACT ───────── */
        #contact {
            z-index: 1;
            position: relative;
        }
        #contact .container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
        }
        .contact-form .form-group {
            margin-bottom: 20px;
        }
        .contact-form label {
            display: block;
            font-size: 0.8rem;
            font-weight: 500;
            color: #aaaacc;
            margin-bottom: 6px;
            letter-spacing: 0.5px;
        }
        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 14px 18px;
            border-radius: 14px;
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.08);
            color: #e0e0f0;
            font-family: 'Inter', sans-serif;
            font-size: 0.95rem;
            transition: all 0.3s;
            outline: none;
        }
        .contact-form input:focus,
        .contact-form textarea:focus {
            border-color: #00f0ff;
            box-shadow: 0 0 30px rgba(0, 240, 255, 0.06);
            background: rgba(255, 255, 255, 0.06);
        }
        .contact-form textarea {
            min-height: 140px;
            resize: vertical;
        }
        .contact-form .btn-primary {
            width: 100%;
            justify-content: center;
            padding: 16px;
            font-size: 1rem;
        }
        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 24px;
        }
        .contact-item {
            display: flex;
            align-items: center;
            gap: 16px;
            padding: 20px 24px;
            border-radius: 16px;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.04);
            transition: all 0.3s;
        }
        .contact-item:hover {
            border-color: rgba(0, 240, 255, 0.15);
            background: rgba(0, 240, 255, 0.03);
        }
        .contact-item .emoji {
            font-size: 1.8rem;
        }
        .contact-item .text {
            font-size: 0.95rem;
        }
        .contact-item .text .label {
            font-size: 0.7rem;
            color: #8888bb;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* ───────── FOOTER ───────── */
        footer {
            z-index: 1;
            position: relative;
            padding: 60px 0 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.04);
            background: rgba(0, 0, 0, 0.2);
        }
        footer .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 24px;
        }
        footer .logo {
            font-size: 1.2rem;
        }
        footer .socials {
            display: flex;
            gap: 20px;
        }
        footer .socials a {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.06);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
            font-size: 1rem;
        }
        footer .socials a:hover {
            background: rgba(0, 240, 255, 0.1);
            border-color: #00f0ff;
            transform: translateY(-3px);
            box-shadow: 0 0 30px rgba(0, 240, 255, 0.1);
        }
        footer .copy {
            font-size: 0.8rem;
            color: #666688;
        }

        /* ───────── RESPONSIVE ───────── */
        @media (max-width: 1024px) {
            #hero .container {
                grid-template-columns: 1fr;
                text-align: center;
            }
            .hero-sub {
                margin-left: auto;
                margin-right: auto;
            }
            .hero-actions {
                justify-content: center;
            }
            .hero-stats {
                position: relative;
                bottom: auto;
                margin-top: 32px;
            }
            .hero-visual {
                order: -1;
            }
            .drone-3d {
                max-width: 320px;
            }
            #about .container {
                grid-template-columns: 1fr;
                text-align: center;
            }
            .about-features {
                grid-template-columns: 1fr 1fr;
            }
            #contact .container {
                grid-template-columns: 1fr;
            }
            .section-desc {
                margin-left: auto;
                margin-right: auto;
            }
        }
        @media (max-width: 768px) {
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 280px;
                height: 100vh;
                background: rgba(10, 10, 26, 0.96);
                backdrop-filter: blur(20px);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                gap: 24px;
                transition: right 0.4s ease;
                border-left: 1px solid rgba(255, 255, 255, 0.05);
            }
            .nav-links.open {
                right: 0;
            }
            .hamburger {
                display: flex;
                z-index: 1001;
            }
            .hero-title {
                font-size: 2.2rem;
            }
            .hero-stats {
                flex-wrap: wrap;
                gap: 24px;
                padding: 16px 24px;
            }
            .hero-stats .stat-number {
                font-size: 1.3rem;
            }
            .about-features {
                grid-template-columns: 1fr;
            }
            .services-grid {
                grid-template-columns: 1fr 1fr;
            }
            footer .container {
                flex-direction: column;
                text-align: center;
            }
            section {
                padding: 60px 0;
            }
        }
        @media (max-width: 480px) {
            .services-grid {
                grid-template-columns: 1fr;
            }
            .hero-actions {
                flex-direction: column;
                align-items: center;
            }
            .hero-actions .btn-primary,
            .hero-actions .btn-outline {
                width: 100%;
                justify-content: center;
            }
            .hero-stats {
                flex-direction: column;
                gap: 12px;
            }
            .about-grid {
                grid-template-columns: 1fr 1fr;
            }
            .about-grid .box.large {
                aspect-ratio: 1/1;
            }
        }

        /* ───────── SCROLL REVEAL ───────── */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s ease;
        }
        .reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .reveal-delay-1 {
            transition-delay: 0.1s;
        }
        .reveal-delay-2 {
            transition-delay: 0.2s;
        }
        .reveal-delay-3 {
            transition-delay: 0.3s;
        }
        .reveal-delay-4 {
            transition-delay: 0.4s;
        }
    </style>
</head>
<body>

    <!-- ─── PARTICLE CANVAS ─── -->
    <canvas id="particleCanvas"></canvas>

    <!-- ─── NAVBAR ─── -->
    <nav class="navbar" id="navbar">
        <div class="container">
            <a href="#" class="logo">
                <span class="icon"></span>
                NOVA<span>DRONE</span>
            </a>
            <ul class="nav-links" id="navLinks">
                <li><a href="#about">About</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#contact">Contact</a></li>
                <li><a href="#contact" class="nav-cta">Get Started</a></li>
            </ul>
            <button class="hamburger" id="hamburger" aria-label="Toggle navigation">
                <span></span>
                <span></span>
                <span></span>
            </button>
        </div>
    </nav>

    <!-- ─── HERO ─── -->
    <section id="hero">
        <div class="container">
            <div class="hero-content">
                <div class="hero-badge">
                    <span class="dot"></span>
                    Next-Gen Aerial Tech
                </div>
                <h1 class="hero-title glow-text">
                    The Future of <br />
                    <span class="highlight">Flight</span> is Here
                </h1>
                <p class="hero-sub">
                    Autonomous drones, AI-powered analytics, and real-time
                    data solutions for enterprises that demand the extraordinary.
                </p>
                <div class="hero-actions">
                    <a href="#contact" class="btn-primary">
                        🚀 Launch Mission
                    </a>
                    <a href="#services" class="btn-outline">
                        Explore Solutions
                    </a>
                </div>
            </div>
            <div class="hero-visual">
                <div class="drone-3d">
                    <div class="ring"></div>
                    <div class="ring"></div>
                    <div class="ring"></div>
                    <div class="drone-icon">🛸</div>
                </div>
                <div class="hero-stats">
                    <div class="stat">
                        <div class="stat-number">12K+</div>
                        <div class="stat-label">Missions Flown</div>
                    </div>
                    <div class="stat">
                        <div class="stat-number">99.7%</div>
                        <div class="stat-label">Success Rate</div>
                    </div>
                    <div class="stat">
                        <div class="stat-number">24/7</div>
                        <div class="stat-label">AI Monitoring</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ─── ABOUT ─── -->
    <section id="about">
        <div class="container">
            <div class="about-content reveal">
                <span class="section-label">✦ About</span>
                <h2 class="section-title">Redefining <span>Aerial</span> Intelligence</h2>
                <p class="section-desc">
                    We build next-generation drone systems that combine
                    autonomous navigation, edge computing, and real-time
                    telemetry to deliver actionable insights from the sky.
                </p>
                <div class="about-features">
                    <div class="about-feature reveal reveal-delay-1">
                        <div class="icon">🧠</div>
                        <h4>AI Autonomy</h4>
                        <p>Self-learning flight paths with obstacle avoidance.</p>
                    </div>
                    <div class="about-feature reveal reveal-delay-2">
                        <div class="icon">📡</div>
                        <h4>Real-Time Data</h4>
                        <p>Live telemetry &amp; 4K streaming to your command center.</p>
                    </div>
                    <div class="about-feature reveal reveal-delay-3">
                        <div class="icon">🔋</div>
                        <h4>Extended Range</h4>
                        <p>90+ minutes of flight time with rapid-swap batteries.</p>
                    </div>
                    <div class="about-feature reveal reveal-delay-4">
                        <div class="icon">🛡️</div>
                        <h4>Military-Grade</h4>
                        <p>Encrypted comms &amp; anti-jamming technology.</p>
                    </div>
                </div>
            </div>
            <div class="about-visual reveal">
                <div class="about-grid">
                    <div class="box">🚁</div>
                    <div class="box">📊</div>
                    <div class="box large">🌍</div>
                </div>
            </div>
        </div>
    </section>

    <!-- ─── SERVICES ─── -->
    <section id="services">
        <div class="container">
            <div class="reveal">
                <span class="section-label">✦ Services</span>
                <h2 class="section-title">Built for <span>Tomorrow</span></h2>
                <p class="section-desc">
                    From delivery to defense, our drone ecosystem adapts to your mission.
                </p>
            </div>
            <div class="services-grid">
                <div class="service-card reveal reveal-delay-1">
                    <span class="icon">📦</span>
                    <h3>Autonomous Delivery</h3>
                    <p>Last-mile logistics with zero human intervention. AI-optimized routes.</p>
                    <span class="badge">⚡ 5 min setup</span>
                </div>
                <div class="service-card reveal reveal-delay-2">
                    <span class="icon">🔍</span>
                    <h3>Inspection &amp; Survey</h3>
                    <p>High-res mapping, thermal imaging, and structural analysis for industry.</p>
                    <span class="badge">📸 4K + Thermal</span>
                </div>
                <div class="service-card reveal reveal-delay-3">
                    <span class="icon">🛡️</span>
                    <h3>Security &amp; Surveillance</h3>
                    <p>Perimeter monitoring with facial recognition and anomaly detection.</p>
                    <span class="badge">🔒 Encrypted</span>
                </div>
                <div class="service-card reveal reveal-delay-4">
                    <span class="icon">🌾</span>
                    <h3>Agri &amp; Environment</h3>
                    <p>Crop health analysis, pesticide targeting, and wildlife conservation.</p>
                    <span class="badge">🌱 30% yield boost</span>
                </div>
            </div>
        </div>
    </section>

    <!-- ─── CONTACT ─── -->
    <section id="contact">
        <div class="container">
            <div class="contact-form reveal">
                <span class="section-label">✦ Contact</span>
                <h2 class="section-title">Launch Your <span>Mission</span></h2>
                <p class="section-desc" style="margin-bottom:32px;">
                    Ready to deploy? Reach out and we'll design a drone solution for your needs.
                </p>
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">Full Name</label>
                        <input type="text" id="name" placeholder="Enter your name" required />
                    </div>
                    <div class="form-group">
                        <label for="email">Email Address</label>
                        <input type="email" id="email" placeholder="you@company.com" required />
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" placeholder="Tell us about your mission..." required></textarea>
                    </div>
                    <button type="submit" class="btn-primary">🚀 Send Message</button>
                </form>
            </div>
            <div class="contact-info reveal reveal-delay-1">
                <div class="contact-item">
                    <span class="emoji">📍</span>
                    <div class="text">
                        <div class="label">HQ</div>
                        Nova Drone Labs, Silicon Valley
                    </div>
                </div>
                <div class="contact-item">
                    <span class="emoji">📧</span>
                    <div class="text">
                        <div class="label">Email</div>
                        mission@novadrone.tech
                    </div>
                </div>
                <div class="contact-item">
                    <span class="emoji">📞</span>
                    <div class="text">
                        <div class="label">Phone</div>
                        +1 (800) 555-NOVA
                    </div>
                </div>
                <div class="contact-item">
                    <span class="emoji">🕒</span>
                    <div class="text">
                        <div class="label">Support</div>
                        24/7 — AI dispatch ready
                    </div>
                </div>
                <div style="margin-top: 8px; padding: 20px 24px; border-radius: 16px; background: rgba(0,240,255,0.03); border: 1px solid rgba(0,240,255,0.08);">
                    <p style="font-size:0.9rem; color:#8888bb;">
                        "We deployed 3 Nova units and cut inspection time by 72%."
                        <br />
                        <span style="color:#00f0ff; font-weight:500;">— SpaceX Operations Team</span>
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- ─── FOOTER ─── -->
    <footer>
        <div class="container">
            <div>
                <a href="#" class="logo" style="font-size:1.1rem;">
                    <span class="icon" style="width:20px;height:20px;"></span>
                    NOVA<span>DRONE</span>
                </a>
                <p class="copy" style="margin-top:6px;">&copy; 2026 — Autonomous. Intelligent. Future-ready.</p>
            </div>
            <div class="socials">
                <a href="#" aria-label="Twitter">🐦</a>
                <a href="#" aria-label="GitHub">💻</a>
                <a href="#" aria-label="LinkedIn">🔗</a>
                <a href="#" aria-label="YouTube">📺</a>
            </div>
        </div>
    </footer>

    <!-- ─── JAVASCRIPT ─── -->
    <script>
        // ─── PARTICLE NETWORK ───
        (function() {
            const canvas = document.getElementById('particleCanvas');
            const ctx = canvas.getContext('2d');
            let particles = [];
            let mouseX = null;
            let mouseY = null;

            function resize() {
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
            }
            window.addEventListener('resize', resize);
            resize();

            const PARTICLE_COUNT = 90;
            const CONNECT_DIST = 150;
            const MOUSE_RADIUS = 200;

            class Particle {
                constructor() {
                    this.x = Math.random() * canvas.width;
                    this.y = Math.random() * canvas.height;
                    this.vx = (Math.random() - 0.5) * 0.4;
                    this.vy = (Math.random() - 0.5) * 0.4;
                    this.radius = Math.random() * 2 + 1;
                }
                update() {
                    this.x += this.vx;
                    this.y += this.vy;
                    if (this.x < 0 || this.x > canvas.width) this.vx *= -1;
                    if (this.y < 0 || this.y > canvas.height) this.vy *= -1;
                }
                draw() {
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                    ctx.fillStyle = 'rgba(0, 240, 255, 0.25)';
                    ctx.fill();
                }
            }

            function initParticles() {
                particles = [];
                for (let i = 0; i < PARTICLE_COUNT; i++) {
                    particles.push(new Particle());
                }
            }
            initParticles();

            function drawLines() {
                for (let i = 0; i < particles.length; i++) {
                    for (let j = i + 1; j < particles.length; j++) {
                        const dx = particles[i].x - particles[j].x;
                        const dy = particles[i].y - particles[j].y;
                        const dist = Math.sqrt(dx * dx + dy * dy);
                        if (dist < CONNECT_DIST) {
                            const alpha = 1 - dist / CONNECT_DIST;
                            ctx.beginPath();
                            ctx.moveTo(particles[i].x, particles[i].y);
                            ctx.lineTo(particles[j].x, particles[j].y);
                            ctx.strokeStyle = `rgba(0, 240, 255, ${alpha * 0.12})`;
                            ctx.lineWidth = 1;
                            ctx.stroke();
                        }
                    }
                }
                // Mouse connections
                if (mouseX !== null && mouseY !== null) {
                    for (let p of particles) {
                        const dx = p.x - mouseX;
                        const dy = p.y - mouseY;
                        const dist = Math.sqrt(dx * dx + dy * dy);
                        if (dist < MOUSE_RADIUS) {
                            const alpha = 1 - dist / MOUSE_RADIUS;
                            ctx.beginPath();
                            ctx.moveTo(p.x, p.y);
                            ctx.lineTo(mouseX, mouseY);
                            ctx.strokeStyle = `rgba(123, 97, 255, ${alpha * 0.25})`;
                            ctx.lineWidth = 1.2;
                            ctx.stroke();
                        }
                    }
                }
            }

            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                for (let p of particles) {
                    p.update();
                    p.draw();
                }
                drawLines();
                requestAnimationFrame(animate);
            }
            animate();

            window.addEventListener('mousemove', (e) => {
                mouseX = e.clientX;
                mouseY = e.clientY;
            });
            window.addEventListener('mouseleave', () => {
                mouseX = null;
                mouseY = null;
            });
            window.addEventListener('touchmove', (e) => {
                const touch = e.touches[0];
                mouseX = touch.clientX;
                mouseY = touch.clientY;
            });
            window.addEventListener('touchend', () => {
                mouseX = null;
                mouseY = null;
            });

            // Resize re-init
            window.addEventListener('resize', () => {
                resize();
                initParticles();
            });
        })();

        // ─── NAVBAR SCROLL ───
        const navbar = document.getElementById('navbar');
        let lastScroll = 0;
        window.addEventListener('scroll', () => {
            const scrollY = window.scrollY;
            if (scrollY > 60) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
            lastScroll = scrollY;
        });

        // ─── HAMBURGER ───
        const hamburger = document.getElementById('hamburger');
        const navLinks = document.getElementById('navLinks');
        hamburger.addEventListener('click', () => {
            hamburger.classList.toggle('active');
            navLinks.classList.toggle('open');
        });
        // Close on link click
        navLinks.querySelectorAll('a').forEach(link => {
            link.addEventListener('click', () => {
                hamburger.classList.remove('active');
                navLinks.classList.remove('open');
            });
        });

        // ─── SCROLL REVEAL (Intersection Observer) ───
        const revealElements = document.querySelectorAll('.reveal');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, {
            threshold: 0.15,
            rootMargin: '0px 0px -40px 0px'
        });
        revealElements.forEach(el => observer.observe(el));

        // ─── CONTACT FORM ───
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const btn = this.querySelector('button[type="submit"]');
            const originalText = btn.innerHTML;
            btn.innerHTML = '✦ Sending...';
            btn.disabled = true;
            setTimeout(() => {
                btn.innerHTML = '✅ Message Sent!';
                btn.style.background = 'linear-gradient(135deg, #00d4aa, #00aaff)';
                setTimeout(() => {
                    btn.innerHTML = originalText;
                    btn.style.background = '';
                    btn.disabled = false;
                    this.reset();
                }, 2500);
            }, 1200);
        });

        // ─── SMOOTH ANCHOR SCROLL ───
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    e.preventDefault();
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });

        console.log('🚁 NOVA DRONE — Futuristic Aerial Solutions');
        console.log('✨ Built with ❤️ for the future of flight.');
    </script>
</body>
</html>
