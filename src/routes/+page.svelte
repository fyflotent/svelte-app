<script lang="ts">
    let count = $state(0)
</script>


<button class="text-lg text-white p-2 px-3 m-1 rounded bg-blue-500" onclick={() => count++}>
  clicks: {count}
</button>
