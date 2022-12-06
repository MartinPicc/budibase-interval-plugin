<script>
  import { createEventDispatcher, onDestroy } from "svelte";
  import stopwatchSvg from './icons/stopwatch.svg';

  const dispatch = createEventDispatcher();
  export let interval;
  export let display = true;
  export let text = "Interval";

  let intervalID = null;

  if (interval > 0) {
    intervalID = window.setInterval(() => { dispatch("trigger"); }, interval * 1000);
  }
  onDestroy(() => {
    if(intervalID) window.clearInterval(intervalID);
  });
</script>

{#if display}
  <div class="container">
    {@html stopwatchSvg} 
    <span>{text}</span>
  </div>
{/if}

<style>
  .container {
    display: flex;
    align-items: center;
    gap: 5px;
  }
</style>
