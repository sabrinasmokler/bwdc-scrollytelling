<script>
    import { onMount } from 'svelte';

  
    onMount(() => {
      const element = document.querySelector('.ripple-wheel');
      element.classList.add('rotate');
    });
  </script>
  
  <section class="ripple-section">
    <div class="container">
      <div class="content-split">
        <div class="text">
          <h2>The Ripple Effect</h2>
          <p>These barriers cause a domino effect to happen over time. A lack of funding impacts growth, which affects visibility, which then limits partnerships and scalability. It becomes a loop that’s hard to break out of over time.</p>
  
          <div class="highlight-stat">
            <span class="stat-number">10x</span>
            <p>Median white family wealth compared to Black family wealth</p>
          </div>
  
          <p>This wealth divide shapes who has the opportunity to build lasting businesses, and who continues to begin from the ground up, time and again.

     </p>
        </div>
  
        <div class="visual">
          <div class="ripple-wheel">
            <span class="center-label">Systemic<br />Barriers</span>
            <div class="dot top"></div>
            <div class="dot right"></div>
            <div class="dot bottom"></div>
            <div class="dot left"></div>
          </div>
        </div>
      </div>
    </div>
  </section>
  
  <style>
    .ripple-section {
      background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
      color: #fff;
      padding: 100px 20px;
    }
  
    .container {
      max-width: 1200px;
      margin: 0 auto;
    }
  
    .content-split {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: center;
    }
  
    .text h2 {
      font-size: 3rem;
      color: #ffd700;
      margin-bottom: 20px;
      position: relative;
    }
  
    .text h2::after {
      content: '';
      width: 100px;
      height: 4px;
      background: linear-gradient(90deg, #ffd700, #ffed4e);
      position: absolute;
      bottom: -10px;
      left: 0;
      border-radius: 2px;
    }
  
    .text p {
      font-size: 1.1rem;
      line-height: 1.8;
      color: #ccc;
      margin-bottom: 20px;
    }
  
    .highlight-stat {
      background: linear-gradient(135deg, rgba(255, 107, 107, 0.2), rgba(255, 215, 0, 0.2));
      border-left: 4px solid #ffd700;
      padding: 20px;
      margin: 20px 0;
      border-radius: 10px;
      backdrop-filter: blur(5px);
    }
  
    .highlight-stat .stat-number {
      font-size: 3rem;
      font-weight: bold;
      color: #ffd700;
      display: block;
      margin-bottom: 10px;
    }
  
    .ripple-wheel {
      width: 220px;
      height: 220px;
      border: 3px solid #ffd700;
      border-radius: 50%;
      margin: 0 auto;
      position: relative;
    }
  
    .ripple-wheel.rotate {
      animation: spin 12s linear infinite;
    }
  
    .center-label {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      text-align: center;
      font-weight: bold;
      color: #ffd700;
    }
  
    .dot {
      width: 20px;
      height: 20px;
      background: #ff6b6b;
      border-radius: 50%;
      position: absolute;
    }
  
    .dot.top {
      top: -10px;
      left: 50%;
      transform: translateX(-50%);
    }
  
    .dot.right {
      top: 50%;
      right: -10px;
      transform: translateY(-50%);
    }
  
    .dot.bottom {
      bottom: -10px;
      left: 50%;
      transform: translateX(-50%);
    }
  
    .dot.left {
      top: 50%;
      left: -10px;
      transform: translateY(-50%);
    }
  
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
  
    @media (max-width: 768px) {
      .content-split {
        grid-template-columns: 1fr;
        gap: 40px;
      }
  
      .text h2 {
        font-size: 2rem;
      }
  
      .text p {
        font-size: 1rem;
      }
  
      .ripple-wheel {
        margin-top: 40px;
      }
    }
  </style>
  