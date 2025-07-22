<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
</script>

<Scroller layout="left">
  {#snippet sticky()}
    <div style="padding: 50px; background-color: #cce5ff;">
      <h1>Hello from Test Section!</h1>
    </div>
  {/snippet}

  {#snippet scrolly()}
    <ArticleText>
      <p>This is the first bit of scrollable content.</p>
    </ArticleText>
    <ArticleText>
      <p>Here's another scrollable paragraph.</p>
    </ArticleText>
  {/snippet}
</Scroller>
