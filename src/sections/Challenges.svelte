<script>
  import { onMount } from "svelte";

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("visible");
          }
        });
      },
      { threshold: 0.1 }
    );

    document.querySelectorAll(".barrier-card").forEach((card) => {
      observer.observe(card);
    });
  });
</script>
<section class="challenges-section">
  <div class="container">
    <h2>Challenges and Solutions</h2>
    <p class="intro">The barriers Black entrepreneurs face overlap each other causing making growth even harder. Here's a closer look at some of the most pressing obstacles.</p>

    <div class="barriers-grid">
      <div class="barrier-card">
        <div class="icon">💰</div>
        <h3>Funding Desert</h3>
        <p>Loan denial rates are twice as high for Black entrepreneurs. Many also lack access to family funding or generational wealth.</p>
      </div>

      <div class="barrier-card">
        <div class="icon">📍</div>
        <h3>Geographic Isolation</h3>
        <p>Many Black-owned businesses are located in underserved areas with limited customer bases and investor access.</p>
      </div>

      <div class="barrier-card">
        <div class="icon">👨‍👩‍👧‍👦</div>
        <h3>Wealth Gap Legacy</h3>
        <p>Historical exclusion from wealth-building opportunities has left many Black founders starting from scratch.</p>
      </div>

      <div class="barrier-card">
        <div class="icon">⚖️</div>
        <h3>Risk Bias</h3>
        <p>Lenders and investors frequently overestimate risk, even when credit profiles are equal to white-owned firms.</p>
      </div>

   
    </div>
  </div>
</section>

<style>
  .challenges-section {
    background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
    padding: 100px 20px;
    color: #fff;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
  }

  h2 {
    font-size: 3rem;
    text-align: center;
    color: #ffd700;
    margin-bottom: 20px;
    position: relative;
  }

  h2::after {
    content: '';
    width: 100px;
    height: 4px;
    background: linear-gradient(90deg, #ffd700, #ffed4e);
    position: absolute;
    bottom: -10px;
    left: 50%;
    transform: translateX(-50%);
    border-radius: 2px;
  }

  .intro {
    text-align: center;
    max-width: 800px;
    margin: 0 auto 60px;
    font-size: 1.2rem;
    color: #ccc;
  }

  .barriers-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 40px;
  }

  .barrier-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(8px);
    padding: 30px;
    border-radius: 20px;
    border: 1px solid rgba(255, 215, 0, 0.15);
    color: #ddd;
    transition: all 0.4s ease;
  }

  .barrier-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 40px rgba(255, 215, 0, 0.2);
    border-color: rgba(255, 215, 0, 0.4);
  }

  .icon {
    font-size: 2.5rem;
    margin-bottom: 15px;
    color: #ffd700;
    text-align: center;
  }

  h3 {
    font-size: 1.3rem;
    text-align: center;
    color: #ffd700;
    margin-bottom: 10px;
  }

  p {
    font-size: 1rem;
    text-align: center;
    line-height: 1.6;
  }
</style> 
