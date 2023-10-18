<script>
  import { createEventDispatcher } from "svelte";
  import Icon from "./Icon.svelte";
  import { plusIcon, minusIcon } from "./icon";

  export let count = 3;

  const dispatch = createEventDispatcher();

  const changeCount = (amount) => {
    dispatch("changeCount", {
      change: amount,
    });
  };
</script>

<section>
  <h1>Create Color Palette for Me!</h1>

  <div class="counter">
    <button on:click={() => changeCount(-1)}>
      <span class="icon"><Icon i={{ ...minusIcon, height: "1.4em" }} /></span>
    </button>
    <div class="counter-viewer">
      <p>{count}</p>
    </div>
    <button on:click={() => changeCount(1)}>
      <span class="icon"><Icon i={{ ...plusIcon, height: "1.4em" }} /></span>
    </button>
  </div>
</section>

<style>
  section {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h1 {
    margin: 0.5em 0;
  }

  .counter {
    display: flex;
    justify-content: center;
  }

  .counter button {
    width: 4em;
    height: 4em;
    border-radius: var(--border-radius);
    background: var(--color-bg-3);
    outline: none;
    border: none;
    cursor: pointer;
  }

  .counter button:hover {
    background: #fff;
  }

  .counter .counter-viewer {
    width: 4em;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .counter .counter-viewer p {
    font-size: 2em;
    font-weight: 600;
  }

  .counter button .icon {
    opacity: 0.5;
  }
</style>
