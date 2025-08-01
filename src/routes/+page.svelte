<script lang="ts">
  let count = $state(0);
  let doubled = $derived(count * 2);

  let size = $state(50);
  let color = $state('#ff3e00');
  let canvas: HTMLCanvasElement | null;
  $effect(() => {
    if (canvas) {
      const context = canvas.getContext('2d');
      if (!context) return;
      context.clearRect(0, 0, canvas.width, canvas.height);

      // this will re-run whenever `color` or `size` change
      context.fillStyle = color;
      context.fillRect(0, 0, size, size);
    }
  });
</script>

<div class="flex flex-row content-center items-center gap-4 p-1">
  <button class="rounded bg-blue-500 p-2 px-3 text-lg text-white" onclick={() => count++}>
    clicks: {count}
  </button>

  <p class="text-lg">{count} doubled is {doubled}</p>

  <canvas bind:this={canvas} width="100" height="100"></canvas>
</div>
