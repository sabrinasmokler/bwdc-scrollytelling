<script>
    import { Chart } from "@highcharts/svelte";
    import { onMount } from "svelte";
    import Scroller from "../../lib/Scroller.svelte";
  
    let chartOptions = {
      chart: { type: "bar", backgroundColor: "transparent" },
      title: { text: null },
      xAxis: {
        categories: [
          "<$5K",
          "$5K-$9.9K",
          "$10K-$24.9K",
          "$25K-$49.9K",
          "$50K-$99.9K",
          "$100K-$249.9K",
          "$250K-$499.9K",
          "$500K-$999.9K",
          "$1M+"
        ],
        title: { text: null }
      },
      yAxis: { title: { text: "Number of Firms" }, min: 0 },
      series: [
        {
          name: "Revenue Bracket",
          data: [1717, 2159, 5241, 9667, 15393, 32906, 30407, 23288, 28550],
          color: "#ffd700"
        }
      ],
      plotOptions: { bar: { dataLabels: { enabled: true, color: "#fff" } } },
      legend: { enabled: false }
    };
  
    let chart;
    let floatingElements;
  
    onMount(() => {
      chart = chartOptions;
      createFloatingElements();
    });
  
    function createFloatingElements() {
      if (!floatingElements) return;
      for (let i = 0; i < 5; i++) {
        const dot = document.createElement("div");
        dot.className = "floating-dot";
        dot.style.left = `${Math.random() * 100}%`;
        dot.style.top = `${Math.random() * 100}%`;
        dot.style.animationDelay = `${Math.random() * 6}s`;
        dot.style.animationDuration = `${6 + Math.random() * 4}s`;
        floatingElements.appendChild(dot);
      }
    }
  </script>
  
  <div class="floating-elements" bind:this={floatingElements}></div>
  <Scroller layout="left">
    {#snippet sticky()}
      <div class="chart-container">
        <h3 style="color: #ffd700; margin-bottom: 20px; text-align: center;">Revenue Distribution</h3>
        <Chart options={chartOptions} />
      </div>
    {/snippet}
  
    {#snippet scrolly()}
      <div class="content-split">
        <div>
          <h2>The Startling Discovery</h2>
          <p>While exploring data from the Black Wealth Data Center, a surprising pattern emerged. The vast majority of Black-owned employer firms cluster in the lower revenue brackets, with very few breaking the $1 million threshold.</p>
          <div class="highlight-stat">
            <span class="stat-number">Only 23%</span>
            <p>of Black-owned businesses exceed $500K in annual revenue</p>
          </div>
          <p>This distribution raises critical questions about the systemic challenges Black entrepreneurs face in scaling their businesses.</p>
        </div>
      </div>
    {/snippet}
  </Scroller>
  
  <style>
    .floating-elements {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      pointer-events: none;
      z-index: -1;
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
      0%,
      100% {
        transform: translateY(0px) rotate(0deg);
      }
      50% {
        transform: translateY(-20px) rotate(180deg);
      }
    }
  
    .content-split {
      display: flex;
      gap: 60px;
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
    }
  
    h2 {
      font-size: 3rem;
      margin-bottom: 2rem;
      color: #ffd700;
    }
  
    h2::after {
      content: "";
      position: absolute;
      bottom: -10px;
      left: 0;
      width: 100px;
      height: 3px;
      background: linear-gradient(45deg, #ffd700, #ffed4e);
      border-radius: 2px;
    }
  
    .highlight-stat {
      background: linear-gradient(135deg, rgba(255, 107, 107, 0.2), rgba(255, 215, 0, 0.2));
      border-left: 4px solid #ffd700;
      padding: 20px;
      margin: 20px 0;
      border-radius: 10px;
      backdrop-filter: blur(5px);
    }
  
    .stat-number {
      font-size: 3rem;
      font-weight: bold;
      color: #ffd700;
      display: block;
      margin-bottom: 10px;
    }
  
    .chart-container {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border-radius: 20px;
      padding: 30px;
      border: 1px solid rgba(255, 215, 0, 0.2);
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
    }
  
    @media (max-width: 768px) {
      .content-split {
        flex-direction: column;
        gap: 40px;
      }
      h2 {
        font-size: 2rem;
      }
    }
  </style>