<script lang="ts">
  let start: number | null = $state(null);
  let counter = $state(0);

  const showDuration = (duration: number) => {
    const ms = Math.floor(duration % 1000);
    const seconds = Math.floor((duration / 1000) % 60);
    const minutes = Math.floor((duration / 1000 / 60) % 60);
    return `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}:${ms.toString().padStart(3, '0')}`;
  };
  $effect(() => {
    if (start !== null) {
      const interval = setInterval(() => {
        if (start !== null) {
          counter = Date.now() - start;
        }
      }, 50);
      return () => clearInterval(interval);
    }
  });
</script>

<div class="flex h-full w-full flex-col items-center justify-center">
  <div class="flex flex-col content-center items-center gap-4 p-1">
    <p class="text-lg">
      {showDuration(counter)}
    </p>
    <div>
      <button
        class="rounded bg-blue-500 p-2 px-3 text-lg text-white disabled:bg-gray-300"
        disabled={start !== null}
        onclick={() => {
          counter = 0;
          start = Date.now();
        }}
      >
        Start
      </button>
      <button
        disabled={start === null}
        class="rounded bg-red-600 p-2 px-3 text-lg text-white disabled:bg-gray-300"
        onclick={() => {
          start = null;
        }}
      >
        Stop
      </button>
    </div>
  </div>
</div>
