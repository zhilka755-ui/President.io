
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Даниил Жильников - Кандидат в президенты школы №108</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #000000;
            --secondary: #ffffff;
            --accent: #666666;
            --gray-light: #f5f5f5;
            --gray-medium: #e0e0e0;
            --shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
            --border-radius: 12px;
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
            font-size: 16px;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            line-height: 1.6;
            color: var(--primary);
            background: var(--secondary);
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* Навигация */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            padding: 1rem 2rem;
            box-shadow: var(--shadow);
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: var(--transition);
        }

        .navbar.scrolled {
            padding: 0.75rem 2rem;
            background: rgba(255, 255, 255, 0.98);
        }

        .logo {
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2.5rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--primary);
            font-weight: 500;
            font-size: 0.95rem;
            transition: var(--transition);
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: var(--transition);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Бургер-меню */
        .burger {
            display: none;
            flex-direction: column;
            cursor: pointer;
            padding: 0.5rem;
            z-index: 1001;
        }

        .burger span {
            width: 22px;
            height: 2px;
            background: var(--primary);
            margin: 2px 0;
            transition: var(--transition);
            transform-origin: center;
        }

        .burger.active span:nth-child(1) {
            transform: rotate(45deg) translate(6px, 6px);
        }

        .burger.active span:nth-child(2) {
            opacity: 0;
            transform: translateX(-10px);
        }

        .burger.active span:nth-child(3) {
            transform: rotate(-45deg) translate(6px, -6px);
        }

        .mobile-nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background: var(--secondary);
            z-index: 999;
            display: flex;
            align-items: center;
            justify-content: center;
            transform: translateX(100%);
            transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .mobile-nav.active {
            transform: translateX(0);
        }

        .mobile-nav-links {
            list-style: none;
            text-align: center;
        }

        .mobile-nav-links li {
            margin-bottom: 2rem;
        }

        .mobile-nav-links a {
            text-decoration: none;
            color: var(--primary);
            font-size: 1.5rem;
            font-weight: 600;
            transition: var(--transition);
        }

        .mobile-nav-links a:hover {
            color: var(--accent);
        }

        /* Секции */
        section {
            padding: 6rem 2rem;
            min-height: 100vh;
            display: flex;
            align-items: center;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            width: 100%;
        }

        /* Герой секция */
        .hero {
            background: linear-gradient(135deg, var(--gray-light) 0%, var(--secondary) 100%);
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 20% 80%, rgba(0, 0, 0, 0.03) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(0, 0, 0, 0.03) 0%, transparent 50%);
            pointer-events: none;
        }

        .hero-content {
            text-align: center;
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 700;
            margin-bottom: 1.5rem;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeUp 0.8s ease forwards;
        }

        .hero p {
            font-size: clamp(1.1rem, 2.5vw, 1.5rem);
            margin-bottom: 2.5rem;
            color: var(--accent);
            opacity: 0;
            transform: translateY(30px);
            animation: fadeUp 0.8s ease 0.2s forwards;
        }

        .cta-button {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 1rem 2.5rem;
            background: var(--primary);
            color: var(--secondary);
            text-decoration: none;
            border-radius: var(--border-radius);
            font-weight: 600;
            transition: var(--transition);
            opacity: 0;
            transform: translateY(30px);
            animation: fadeUp 0.8s ease 0.4s forwards;
            border: 2px solid var(--primary);
        }

        .cta-button:hover {
            background: transparent;
            color: var(--primary);
            transform: translateY(-2px);
        }

        /* Обо мне */
        .about {
            background: var(--secondary);
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .profile-image {
            position: relative;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transform: translateX(-50px);
            opacity: 0;
            transition: all 0.8s ease;
        }

        .profile-image.visible {
            transform: translateX(0);
            opacity: 1;
        }

        .profile-image img {
            width: 100%;
            height: 400px;
            object-fit: cover;
            display: block;
            transition: var(--transition);
        }

        .profile-image:hover img {
            transform: scale(1.05);
        }

        .about-text h2 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            font-weight: 700;
        }

        .about-text p {
            font-size: 1.1rem;
            color: var(--accent);
            margin-bottom: 1.5rem;
            line-height: 1.8;
        }

        /* Инициативы */
        .initiatives {
            background: var(--gray-light);
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-header h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .section-header p {
            font-size: 1.1rem;
            color: var(--accent);
        }

        .initiatives-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .initiative-card {
            background: var(--secondary);
            padding: 2.5rem;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            transition: var(--transition);
            opacity: 0;
            transform: translateY(30px);
            border: 1px solid var(--gray-medium);
        }

        .initiative-card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .initiative-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
        }

        .initiative-icon {
            font-size: 3rem;
            margin-bottom: 1.5rem;
            display: block;
        }

        .initiative-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            font-weight: 600;
        }

        .initiative-card p {
            color: var(--accent);
            margin-bottom: 1.5rem;
        }

        .initiative-image {
            width: 100%;
            height: 200px;
            border-radius: 8px;
            overflow: hidden;
            margin-top: 1rem;
        }

        .initiative-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .initiative-card:hover .initiative-image img {
            transform: scale(1.05);
        }

        /* Навыки */
        .skills {
            background: var(--secondary);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .skill-item {
            opacity: 0;
            transform: translateX(-30px);
            transition: all 0.6s ease;
        }

        .skill-item.visible {
            opacity: 1;
            transform: translateX(0);
        }

        .skill-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }

        .skill-name {
            font-weight: 600;
            font-size: 1.1rem;
        }

        .skill-duration {
            color: var(--accent);
            font-size: 0.9rem;
        }

        .skill-bar {
            height: 6px;
            background: var(--gray-medium);
            border-radius: 3px;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: var(--primary);
            border-radius: 3px;
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 1.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* Контакты */
        .contact {
            background: var(--gray-light);
            text-align: center;
        }

        .contact-content {
            max-width: 600px;
            margin: 0 auto;
        }

        .contact h2 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            font-weight: 700;
        }

        .contact p {
            font-size: 1.1rem;
            color: var(--accent);
            margin-bottom: 2rem;
        }

        .contact-info {
            background: var(--secondary);
            padding: 2rem;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            display: inline-block;
        }

        /* Анимации */
        @keyframes fadeUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Адаптивность */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .burger {
                display: flex;
            }

            section {
                padding: 5rem 1.5rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 2rem;
                text-align: center;
            }

            .profile-image {
                max-width: 300px;
                margin: 0 auto;
            }

            .initiatives-grid {
                grid-template-columns: 1fr;
            }

            .skills-grid {
                grid-template-columns: 1fr;
            }

            .initiative-card,
            .skill-item {
                transform: none !important;
            }
        }

        @media (max-width: 480px) {
            section {
                padding: 4rem 1rem;
            }
            
            .navbar {
                padding: 1rem;
            }
            
            .navbar.scrolled {
                padding: 0.75rem 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Навигация -->
    <nav class="navbar">
        <a href="#" class="logo">Даниил Жильников</a>
        <ul class="nav-links">
            <li><a href="#home">Главная</a></li>
            <li><a href="#about">Обо мне</a></li>
            <li><a href="#initiatives">Инициативы</a></li>
            <li><a href="#skills">Навыки</a></li>
            <li><a href="#contact">Контакты</a></li>
        </ul>
        <div class="burger">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </nav>

    <!-- Мобильное меню -->
    <div class="mobile-nav">
        <ul class="mobile-nav-links">
            <li><a href="#home">Главная</a></li>
            <li><a href="#about">Обо мне</a></li>
            <li><a href="#initiatives">Инициативы</a></li>
            <li><a href="#skills">Навыки</a></li>
            <li><a href="#contact">Контакты</a></li>
        </ul>
    </div>

    <!-- Главная секция -->
    <section id="home" class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Жильников Даниил</h1>
                <p>Кандидат в президенты школы №108 · Омск</p>
                <a href="#about" class="cta-button">
                    Узнать больше
                    <span>↓</span>
                </a>
            </div>
        </div>
    </section>

    <!-- Обо мне -->
    <section id="about" class="about">
        <div class="container">
            <div class="about-content">
                <div class="profile-image">
                    <!-- Замените на реальное изображение -->
                    <img src="profile-placeholder.jpg" 
                         alt="Даниил Жильников" 
                         onerror="this.src='data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNTAwIiBoZWlnaHQ9IjYwMCIgdmlld0JveD0iMCAwIDUwMCA2MDAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxyZWN0IHdpZHRoPSI1MDAiIGhlaWdodD0iNjAwIiBmaWxsPSIjRjVGNUY1Ii8+CjxjaXJjbGUgY3g9IjI1MCIgY3k9IjIwMCIgcj0iODAiIGZpbGw9IiNEOEQ4RDgiLz4KPHJlY3QgeD0iMTUwIiB5PSIzMDAiIHdpZHRoPSIyMDAiIGhlaWdodD0iMjAwIiBmaWxsPSIjRDhEOEQ4Ii8+Cjwvc3ZnPgo=';this.alt='Изображение не загружено';">
                </div>
                <div class="about-text">
                    <h2>Обо мне</h2>
                    <p>Мне 15 лет, я учусь в 8А классе школы №108 в Омске. Уже 2 года активно занимаюсь программированием и глубоко разбираюсь в современных технологиях.</p>
                    <p>Также я успешно закончил курсы звукорежиссера, что научило меня внимательности к деталям, работе со сложным оборудованием и ответственности за конечный результат.</p>
                    <p>Мой опыт в программировании и звукорежиссуре помогает мне подходить к решению задач системно и творчески.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Инициативы -->
    <section id="initiatives" class="initiatives">
        <div class="container">
            <div class="section-header">
                <h2>Мой план изменений</h2>
                <p>Конкретные предложения по улучшению жизни в нашей школе</p>
            </div>
            <div class="initiatives-grid">
                <div class="initiative-card">
                    <span class="initiative-icon">🗑️</span>
                    <h3>Чистота и порядок</h3>
                    <p>Предлагаю расставить современные урны в коридорах школы и на пришкольной территории. Это поможет поддерживать чистоту и привьёт культуру ответственного отношения к пространству.</p>
                    <div class="initiative-image">
                        <!-- Замените на реальное изображение -->
                        <img src="initiative1-placeholder.jpg" 
                             alt="Система урн в школе" 
                             onerror="this.src='data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNTAwIiBoZWlnaHQ9IjMwMCIgdmlld0JveD0iMCAwIDUwMCAzMDAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxyZWN0IHdpZHRoPSI1MDAiIGhlaWdodD0iMzAwIiBmaWxsPSIjRjVGNUY1Ii8+CjxyZWN0IHg9IjE1MCIgeT0iMTAwIiB3aWR0aD0iMjAwIiBoZWlnaHQ9IjE1MCIgZmlsbD0iI0Q4RDhEOCIvPgo8cmVjdCB4PSIyMDAiIHk9IjE1MCIgd2lkdGg9IjEwMCIgaGVpZ2h0PSI1MCIgZmlsbD0iI0E4QThBOCIvPgo8L3N2Zz4K';this.alt='Изображение не загружено';">
                    </div>
                </div>
                <div class="initiative-card">
                    <span class="initiative-icon">📊</span>
                    <h3>Твой голос важен!</h3>
                    <p>Создам современную онлайн-платформу для сбора идей и голосования за новые проекты. Каждый ученик сможет предложить свою идею и участвовать в принятии решений.</p>
                    <div class="initiative-image">
                        <!-- Замените на реальное изображение -->
                        <img src="initiative2-placeholder.jpg" 
                             alt="Платформа для голосования" 
                             onerror="this.src='data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNTAwIiBoZWlnaHQ9IjMwMCIgdmlld0JveD0iMCAwIDUwMCAzMDAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxyZWN0IHdpZHRoPSI1MDAiIGhlaWdodD0iMzAwIiBmaWxsPSIjRjVGNUY1Ii8+CjxyZWN0IHg9IjEwMCIgeT0iNTAiIHdpZHRoPSIzMDAiIGhlaWdodD0iMjAwIiByeD0iMTAiIGZpbGw9IiNEOEQ4RDgiLz4KPGNpcmNsZSBjeD0iMTUwIiBjeT0iMTI1IiByPSIyMCIgZmlsbD0iI0E4QThBOCIvPgo8cmVjdCB4PSIxODAiIHk9IjExNSIgd2lkdGg9IjE1MCIgaGVpZ2h0PSIyMCIgZmlsbD0iI0E4QThBOCIvPgo8Y2lyY2xlIGN4PSIxNTAiIGN5PSIxNzUiIHI9IjIwIiBmaWxsPSIjQThBOEE4Ii8+CjxyZWN0IHg9IjE4MCIgeT0iMTY1IiB3aWR0aD0iMTUwIiBoZWlnaHQ9IjIwIiBmaWxsPSIjQThBOEE4Ii8+Cjwvc3ZnPgo=';this.alt='Изображение не загружено';">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Навыки -->
    <section id="skills" class="skills">
        <div class="container">
            <div class="section-header">
                <h2>Мои навыки</h2>
                <p>Опыт, который поможет реализовать обещанные изменения</p>
            </div>
            <div class="skills-grid">
                <div class="skill-item">
                    <div class="skill-header">
                        <span class="skill-name">Программирование</span>
                        <span class="skill-duration">2 года</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" data-width="85"></div>
                    </div>
                </div>
                <div class="skill-item">
                    <div class="skill-header">
                        <span class="skill-name">Звукорежиссура</span>
                        <span class="skill-duration">Завершенный курс</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" data-width="78"></div>
                    </div>
                </div>
                <div class="skill-item">
                    <div class="skill-header">
                        <span class="skill-name">Работа в команде</span>
                        <span class="skill-duration">Постоянно</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" data-width="90"></div>
                    </div>
                </div>
                <div class="skill-item">
                    <div class="skill-header">
                        <span class="skill-name">Организация проектов</span>
                        <span class="skill-duration">1 год</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" data-width="75"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Контакты -->
    <section id="contact" class="contact">
        <div class="container">
            <div class="contact-content">
                <h2>Вместе мы сделаем школу лучше!</h2>
                <p>Поддержи мою кандидатуру! Твой голос – это реальный шаг к позитивным изменениям в нашей школе.</p>
                <div class="contact-info">
                    <p><strong>Свяжитесь со мной:</strong></p>
                    <p>Telegram/VK: @daniil_zhilnikov</p>
                    <p>Email: daniil@school108.ru</p>
                </div>
            </div>
        </div>
    </section>

    <script>
        // Упрощенный и исправленный код
        document.addEventListener('DOMContentLoaded', function() {
            // Навигация
            const burger = document.querySelector('.burger');
            const mobileNav = document.querySelector('.mobile-nav');
            const navLinks = document.querySelectorAll('.nav-links a, .mobile-nav-links a');
            
            if (burger && mobileNav) {
                burger.addEventListener('click', function() {
                    burger.classList.toggle('active');
                    mobileNav.classList.toggle('active');
                    document.body.style.overflow = mobileNav.classList.contains('active') ? 'hidden' : '';
                });
                
                // Закрытие меню при клике на ссылку
                navLinks.forEach(link => {
                    link.addEventListener('click', () => {
                        burger.classList.remove('active');
                        mobileNav.classList.remove('active');
                        document.body.style.overflow = '';
                    });
                });
            }
            
            // Плавная прокрутка
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href');
                    const target = document.querySelector(targetId);
                    
                    if (target) {
                        const headerHeight = document.querySelector('.navbar').offsetHeight;
                        const targetPosition = target.offsetTop - headerHeight;
                        
                        window.scrollTo({
                            top: targetPosition,
                            behavior: 'smooth'
                        });
                    }
                });
            });
            
            // Анимация при скролле
            function checkVisibility() {
                const elements = document.querySelectorAll('.profile-image, .initiative-card, .skill-item');
                
                elements.forEach(el => {
                    const rect = el.getBoundingClientRect();
                    const windowHeight = window.innerHeight;
                    
                    if (rect.top < windowHeight * 0.85) {
                        el.classList.add('visible');
                        
                        // Анимация прогресс-баров
                        if (el.classList.contains('skill-item')) {
                            const progressBar = el.querySelector('.skill-progress');
                            if (progressBar && !progressBar.dataset.animated) {
                                const width = progressBar.dataset.width;
                                progressBar.style.transform = `scaleX(${parseInt(width)/100})`;
                                progressBar.dataset.animated = 'true';
                            }
                        }
                    }
                });
            }
            
            // Эффект навигации при скролле
            function updateNavbar() {
                const navbar = document.querySelector('.navbar');
                if (window.scrollY > 50) {
                    navbar.classList.add('scrolled');
                } else {
                    navbar.classList.remove('scrolled');
                }
            }
            
            // Обработчики событий
            window.addEventListener('scroll', function() {
                updateNavbar();
                checkVisibility();
            });
            
            window.addEventListener('resize', checkVisibility);
            
            // Инициализация
            updateNavbar();
            checkVisibility();
            
            // Обработка ошибок загрузки изображений
            const images = document.querySelectorAll('img');
            images.forEach(img => {
                img.addEventListener('error', function() {
                    console.warn('Изображение не загружено:', this.src);
                });
            });
        });
    </script>
</body>
</html>
