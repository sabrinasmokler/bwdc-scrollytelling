<script>
  import { fly } from 'svelte/transition';
  import { onMount } from 'svelte';
  export let threshold = 0.2;

  let visible = false;
  let hasEntered = false;
  let el;

  onMount(() => {
    const observer = new IntersectionObserver(
      ([entry]) => {
        if (entry.isIntersecting) {
          visible = true;
          hasEntered = true;
        }
      },
      { threshold }
    );

    if (el) observer.observe(el);
  });
</script>

<div bind:this={el}>
  {#if hasEntered}
    <div transition:fly="{{ y: 40, opacity: 0, duration: 600 }}">
      <slot />
    </div>
  {/if}
</div>

<style>
  div {
    will-change: transform, opacity;
  }
</style>
