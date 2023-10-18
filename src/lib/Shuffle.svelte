<script>
  import { createEventDispatcher } from "svelte";
  import Icon from "./Icon.svelte";
  import { shuffleIcon } from "./icon";

  const dispatch = createEventDispatcher();
  const handleShuffle = () => {
    dispatch("shuffle");
  };
</script>

<div class="shuffle">
  <button on:click={handleShuffle}>
    <span class="name">Shuffle</span>
    <span class="icon">
      <Icon i={shuffleIcon} />
    </span>
  </button>
</div>

<style>
  .shuffle {
    margin: 0 1em;
  }

  .shuffle button {
    width: 100%;
    height: 2em;
    font-size: 1.5em;
    font-weight: bolder;
    border-radius: var(--border-radius);
    color: var(--color-text);
    background: var(--color-bg-3);
    border: none;
    outline: none;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
  }

  .shuffle button:hover {
    background: #fff;
  }

  button .name {
    margin-left: 1em;
  }

  button .icon {
    opacity: 0.5;
    display: flex;
    margin: 0 0.3em;
  }
</style>
