<script>
    import { onMount, onDestroy } from 'svelte';

    // Props
    export let title = "The Million Dollar Gap";
    export let subtitle = "Uncovering the barriers that keep Black-owned businesses from scaling beyond $1 million in revenue";

    // State for floating elements
    let floatingElements;

    // Create floating dots and sparkles
    function createFloatingElements() {
      if (!floatingElements) return;
      for (let i = 0; i < 30; i++) {
        const dot = document.createElement('div');
        dot.className = 'floating-dot';
        dot.style.left = `${Math.random() * 100}%`;
        dot.style.top = `${Math.random() * 100}%`;
        dot.style.animationDelay = `${Math.random() * 6}s`;
        dot.style.animationDuration = `${6 + Math.random() * 4}s`;
        floatingElements.appendChild(dot);
      }
      for (let i = 0; i < 20; i++) {
        const sparkle = document.createElement('div');
        sparkle.className = 'sparkle';
        sparkle.style.left = `${Math.random() * 100}%`;
        sparkle.style.top = `${Math.random() * 100}%`;
        sparkle.style.animationDelay = `${Math.random() * 2}s`;
        sparkle.style.animationDuration = `${2 + Math.random() * 2}s`;
        floatingElements.appendChild(sparkle);
      }
    }

    // Mouse parallax effect
    function handleMouseMove(e) {
      const dots = floatingElements.querySelectorAll('.floating-dot');
      const sparkles = floatingElements.querySelectorAll('.sparkle');
      const mouseX = e.clientX / window.innerWidth;
      const mouseY = e.clientY / window.innerHeight;
      dots.forEach((dot, index) => {
        const speed = (index % 3 + 1) * 0.5;
        const x = (mouseX - 0.5) * speed * 20;
        const y = (mouseY - 0.5) * speed * 20;
        dot.style.transform = `translate(${x}px, ${y}px)`;
      });
    }

    // Lifecycle hooks
    onMount(() => {
      createFloatingElements();
      window.addEventListener('mousemove', handleMouseMove);
    });

    onDestroy(() => {
      window.removeEventListener('mousemove', handleMouseMove);
    });
  </script>

  <div class="floating-elements" bind:this={floatingElements}></div>

  <div class="title-card">
    <div class="content">
      <h1>{title}</h1>
      <p>{subtitle}</p>
      <div class="scroll-indicator">↓ Scroll to explore</div>
    </div>
  </div>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    .title-card {
      background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 2rem;
      box-sizing: border-box;
      position: relative;
      overflow: hidden;
    }

    .title-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: radial-gradient(circle at 50% 50%, rgba(255, 215, 0, 0.1) 0%, transparent 50%);
      animation: pulse 4s ease-in-out infinite alternate;
    }

    @keyframes pulse {
      0% { 
        opacity: 0.3; 
        transform: scale(0.8); 
      }
      100% { 
        opacity: 0.8; 
        transform: scale(1.2); 
      }
    }

    .content {
      max-width: 700px;
      padding: 4rem;
      position: relative;
      z-index: 2;
    }

    h1 {
      font-family: 'Georgia', serif;
      font-size: 4rem;
      font-weight: bold;
      margin-bottom: 1rem;
      background: linear-gradient(45deg, #ffd700, #ffed4e, #fff);
      background-size: 200% 200%;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      animation: textShine 3s ease-in-out infinite alternate;
      text-shadow: 0 0 30px rgba(255, 215, 0, 0.3);
    }

    @keyframes textShine {
      0% { 
        background-position: 0% 50%; 
        transform: scale(1);
      }
      100% { 
        background-position: 100% 50%; 
        transform: scale(1.02);
      }
    }

    p {
      font-family: 'Georgia', serif;
      font-size: 1.5rem;
      color: #ccc;
      max-width: 600px;
      margin: 0 auto 2rem;
      opacity: 0;
      animation: fadeInUp 1.5s ease-out 0.5s forwards;
    }

    @keyframes fadeInUp {
      0% {
        opacity: 0;
        transform: translateY(30px);
      }
      100% {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .scroll-indicator {
      position: absolute;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      color: #ffd700;
      font-size: 1.2rem;
      animation: bounce 2s infinite;
      opacity: 0;
      animation-delay: 2s;
      animation-fill-mode: forwards;
    }

    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% { 
        opacity: 1;
        transform: translateX(-50%) translateY(0); 
      }
      40% { 
        transform: translateX(-50%) translateY(-10px); 
      }
      60% { 
        transform: translateX(-50%) translateY(-5px); 
      }
    }

    .floating-elements {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .floating-dot {
      position: absolute;
      width: 4px;
      height: 4px;
      background: rgba(255, 215, 0, 0.3);
      border-radius: 50%;
      animation: float 6s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { 
        transform: translateY(0px) rotate(0deg);
        opacity: 0.3;
      }
      50% { 
        transform: translateY(-20px) rotate(180deg);
        opacity: 0.8;
      }
    }

    .sparkle {
      position: absolute;
      width: 2px;
      height: 2px;
      background: #fff;
      border-radius: 50%;
      animation: sparkle 2s ease-in-out infinite;
    }

    @keyframes sparkle {
      0%, 100% {
        opacity: 0;
        transform: scale(0);
      }
      50% {
        opacity: 1;
        transform: scale(1);
      }
    }

    @media (max-width: 768px) {
      h1 { font-size: 2.5rem; }
      p { font-size: 1.2rem; padding: 0 20px; }
    }
  </style>
