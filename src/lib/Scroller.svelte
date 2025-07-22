<script>
    // `layout` can be either "right" or "left"
    // `sticky` and `scrolly` are the snippets passed in (see one of the examples)
    let { layout, sticky, scrolly } = $props(); 
  </script>
  
  <div class="wrapper {layout}">
      <div class="sticky">
          {@render sticky()}
      </div>
  
      <div class="scrolly">
          {@render scrolly()}
      </div>
  </div>
  
  <style>
      .wrapper {
          background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
          padding: min(100vh, 30rem) 1rem;
          border: 1px solid #ffd700; /* Gold border to match title glow */
          display: flex;
          flex-direction: row;
          flex-wrap: wrap;
          align-items: flex-start;
          position: relative;
      }
  
      .wrapper::before {
          content: '';
          position: absolute;
          top: 0;
          left: 0;
          right: 0;
          bottom: 0;
          background: radial-gradient(circle at 50% 50%, rgba(255, 215, 0, 0.1) 0%, transparent 50%);
          animation: pulse 4s ease-in-out infinite alternate;
          z-index: 0;
      }
  
      @keyframes pulse {
          0% { opacity: 0.3; transform: scale(0.8); }
          100% { opacity: 0.8; transform: scale(1.2); }
      }
  
      .left .scrolly {
          order: 0;
      }
      .left .sticky {
          order: 1;
      }
  
      .right .scrolly {
          order: 1;
      }
      .right .sticky {
          order: 0;
      }
  
      .sticky,
      .scrolly {
          display: flex;
          flex-direction: column;
          flex: 1 1; /* Allows growing, shrinking */
          color: #fff; /* Ensure text is readable against dark gradient */
          position: relative;
          z-index: 1;
      }
  
      .sticky {
          position: sticky;
          top: 50vh;
          transform: translateY(-50%);
          display: flex;
          align-items: center;
          justify-content: center;
      }
  
      .scrolly {
          z-index: 2;
      }
  
      @media (max-width: 768px) {
          .wrapper {
              flex-direction: column;
              padding: 2rem 1rem;
              width: 100vw;
          }
  
          .sticky,
          .scrolly {
              flex: 1 1 auto;
              min-width: 100%;
              position: static; /* remove sticky on mobile */
              transform: none;
          }
  
          .sticky {
              margin-bottom: 2rem;
          }
      }
  </style>