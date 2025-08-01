<script lang="ts">
    let count = $state(0)
</script>


<button class="text-2xl" onclick={() => count++}>
  clicks: {count}
</button>
