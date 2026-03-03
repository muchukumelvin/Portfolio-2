// ============================================
// WELCOME SCREEN
// ============================================
// Single language welcome - fast and impactful
setTimeout(function() {
    const welcome = document.getElementById('welcome');
    if (welcome) {
        welcome.style.opacity = '0';
        setTimeout(() => {
            welcome.style.display = 'none';
        }, 800);
    }
}, 1800);

// ============================================
// BACKGROUND CANVAS - Refined particles
// ============================================
const canvas = document.getElementById('canvas-bg');
if (canvas) {
    const ctx = canvas.getContext('2d');
    
    function resizeCanvas() {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
    }
    resizeCanvas();
    window.addEventListener('resize', resizeCanvas);
    
    // Fewer particles, larger, slower - more elegant
    const particles = [];
    const particleCount = 25; // Reduced from 65
    
    for (let i = 0; i < particleCount; i++) {
        particles.push({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height,
            radius: Math.random() * 2.5 + 1.2, // Larger
            speedX: (Math.random() - 0.5) * 0.15, // Slower
            speedY: (Math.random() - 0.5) * 0.15,
            opacity: Math.random() * 0.25 + 0.1
        });
    }
    
    function drawParticles() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        
        // Draw connections between nearby particles
        ctx.strokeStyle = 'rgba(201, 168, 76, 0.05)';
        ctx.lineWidth = 0.5;
        
        for (let i = 0; i < particles.length; i++) {
            for (let j = i + 1; j < particles.length; j++) {
                const dx = particles[i].x - particles[j].x;
                const dy = particles[i].y - particles[j].y;
                const distance = Math.sqrt(dx * dx + dy * dy);
                
                if (distance < 150) {
                    ctx.beginPath();
                    ctx.moveTo(particles[i].x, particles[i].y);
                    ctx.lineTo(particles[j].x, particles[j].y);
                    ctx.strokeStyle = `rgba(201, 168, 76, ${0.05 * (1 - distance/150)})`;
                    ctx.stroke();
                }
            }
        }
        
        // Draw particles
        particles.forEach(p => {
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
            ctx.fillStyle = `rgba(201, 168, 76, ${p.opacity})`;
            ctx.fill();
            
            // Update position
            p.x += p.speedX;
            p.y += p.speedY;
            
            // Boundary check
            if (p.x < 0 || p.x > canvas.width) p.speedX *= -1;
            if (p.y < 0 || p.y > canvas.height) p.speedY *= -1;
        });
        
        // Throttle animation when tab not active
        if (!document.hidden) {
            requestAnimationFrame(drawParticles);
        }
    }
    
    drawParticles();
    
    // Pause animation when tab not active
    document.addEventListener('visibilitychange', () => {
        if (!document.hidden) {
            drawParticles();
        }
    });
}

// ============================================
// TYPED TEXT ANIMATION
// ============================================
const roles = [
    "CEO, Ace Zest Technology",
    "Developer and Innovator",
    "Multilingual Creator",
    "Duke of Edinburgh Awardee",
    "African Tech Builder"
];

let roleIndex = 0;
let charIndex = 0;
let isDeleting = false;
const typedText = document.getElementById('typed-text');

function typeEffect() {
    if (!typedText) return;
    
    const currentRole = roles[roleIndex];
    
    if (isDeleting) {
        typedText.textContent = currentRole.substring(0, charIndex - 1);
        charIndex--;
    } else {
        typedText.textContent = currentRole.substring(0, charIndex + 1);
        charIndex++;
    }
    
    if (!isDeleting && charIndex === currentRole.length) {
        isDeleting = true;
        setTimeout(typeEffect, 2000);
        return;
    }
    
    if (isDeleting && charIndex === 0) {
        isDeleting = false;
        roleIndex = (roleIndex + 1) % roles.length;
    }
    
    setTimeout(typeEffect, isDeleting ? 40 : 80);
}

typeEffect();

// ============================================
// NAVIGATION ACTIVE STATE & SCROLL EFFECT
// ============================================
const navbar = document.getElementById('navbar');
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-link');

function updateNavOnScroll() {
    // Add background on scroll
    if (window.scrollY > 50) {
        navbar.classList.add('scrolled');
    } else {
        navbar.classList.remove('scrolled');
    }
    
    // Update active nav link
    let current = '';
    sections.forEach(section => {
        const sectionTop = section.offsetTop - 150;
        if (window.scrollY >= sectionTop) {
            current = section.getAttribute('id');
        }
    });
    
    navLinks.forEach(link => {
        link.classList.remove('active');
        if (link.getAttribute('href') === `#${current}`) {
            link.classList.add('active');
        }
    });
}

window.addEventListener('scroll', updateNavOnScroll);

// Smooth scroll for nav links
navLinks.forEach(link => {
    link.addEventListener('click', (e) => {
        e.preventDefault();
        const targetId = link.getAttribute('href');
        const targetSection = document.querySelector(targetId);
        if (targetSection) {
            targetSection.scrollIntoView({ behavior: 'smooth' });
        }
    });
});

// ============================================
// REVEAL ANIMATIONS ON SCROLL
// ============================================
const revealElements = document.querySelectorAll('.reveal');

const revealObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('active');
            // Optional: unobserve after reveal to save performance
            revealObserver.unobserve(entry.target);
        }
    });
}, { threshold: 0.15, rootMargin: '0px 0px -50px 0px' });

revealElements.forEach(el => revealObserver.observe(el));

// ============================================
// HERO PARALLAX EFFECT
// ============================================
const heroImage = document.querySelector('.hero-image');
if (heroImage) {
    window.addEventListener('scroll', () => {
        const scrolled = window.scrollY;
        if (scrolled < window.innerHeight) {
            heroImage.style.transform = `translateY(${scrolled * 0.3}px) scale(1.1)`;
        }
    });
}

// ============================================
// PERFORMANCE OPTIMIZATIONS
// ============================================
// Throttle scroll events for better performance
let ticking = false;
window.addEventListener('scroll', () => {
    if (!ticking) {
        window.requestAnimationFrame(() => {
            updateNavOnScroll();
            ticking = false;
        });
        ticking = true;
    }
});

// ============================================
// PREVENT DEFAULT ANCHOR BEHAVIOR
// ============================================
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
            target.scrollIntoView({ behavior: 'smooth' });
        }
    });
});
