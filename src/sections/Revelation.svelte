<script>
  import ScrollFade from "../lib/ScrollFade.svelte";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";

  let chartOptions1 = {
    chart: { type: "bar", backgroundColor: "transparent" },
    title: { text: null },
    xAxis: { categories: ["$500K-$1M", "> $1M"], title: { text: null } },
    yAxis: { title: { text: "Number of Black-Owned Firms" }, min: 0 },
    series: [{
      name: "Black-Owned Firms",
      data: [23288, 28550],
      color: "#ffd700"
    }],
    plotOptions: {
      bar: {
        dataLabels: {
          enabled: true,
          color: "#fff"
        }
      }
    },
    legend: { enabled: false }
  };

  let chartOptions2 = {
    chart: { type: "bar", backgroundColor: "transparent" },
    title: { text: null },
    xAxis: { categories: ["$500K-$1M", "> $1M"], title: { text: null } },
    yAxis: { title: { text: "Number of White-Owned Firms" }, min: 0 },
    series: [{
      name: "White-Owned Firms",
      data: [742415, 1342757],
      color: "#87CEEB"
    }],
    plotOptions: {
      bar: {
        dataLabels: {
          enabled: true,
          color: "#fff"
        }
      }
    },
    legend: { enabled: false }
  };
</script>

<Scroller layout="left">
  {#snippet sticky()}
    <ScrollFade>
      <div class="chart-container">
        <h3 style="color: #ffd700; margin-bottom: 20px; text-align: center;">
          Revenue Distribution Comparison
        </h3>
        <p style="text-align: center; color: #ccc;">
          This chart displays the number of Black-owned compared to White-owned firms across revenue brackets.
        </p>
        <div style="display: flex; gap: 20px;">
          <div style="flex: 1;">
            <Chart options={chartOptions1} />
          </div>
          <div style="flex: 1;">
            <Chart options={chartOptions2} />
          </div>
        </div>
      </div>
    </ScrollFade>
  {/snippet}

  {#snippet scrolly()}
    <ScrollFade>
      <div class="content-split">
        <div>
          <h2>The Startling Discovery</h2>
          <p>
            A surprising pattern emerged when exploring data and research.
            The vast majority of Black-owned employer firms cluster in the lower revenue brackets,
            with very few breaking the $1 million threshold.
          </p>

          <div class="highlight-stat">
            <div style="text-align: center;">
              <span class="stat-number">Only 20%</span>
            </div>
            <div style="text-align: center;">
              <p>Black-owned businesses exceed $500K in annual revenue</p>
            </div>
          </div>

          <p>
            This distribution raises critical questions about the systemic challenges Black entrepreneurs face in scaling their businesses.
          </p>
          <p>Including: Why does growth stop at a certain threshold?</p>
        </div>
      </div>
    </ScrollFade>
  {/snippet}
</Scroller>

<style>
  .content-split {
    max-width: 700px;
    margin: 0 auto;
    padding: 2rem 1rem;
  }

  h2 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    color: #ffd700;
  }

  .highlight-stat {
    background: rgba(255, 215, 0, 0.1);
    padding: 1rem;
    border-left: 4px solid #ffd700;
    margin: 1rem 0;
  }

  .stat-number {
    font-size: 2rem;
    font-weight: bold;
    color: #ffd700;
    display: block;
  }

  .chart-container {
    flex: 1;
    min-width: 300px;
    max-width: 600px;
    margin: auto;
  }

  @media (max-width: 768px) {
    .content-split {
      padding: 1rem;
    }

    h2 {
      font-size: 2rem;
    }

    .chart-container div {
      flex-direction: column;
      gap: 10px;
    }
  }
</style>
