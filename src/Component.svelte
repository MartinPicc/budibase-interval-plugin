<script>
  import { getContext } from "svelte";
  import Interval from "./lib/Interval.svelte";

  export let trigger;
  export let interval;
  export let display;
  export let text;

  const { styleable } = getContext("sdk");
  const component = getContext("component");
</script>

<div use:styleable={$component.styles}>
  <Interval on:trigger={trigger} interval={interval} display={display} text={text}/>
</div>
