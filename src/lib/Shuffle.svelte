<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  const handleShuffle = () => {
    dispatch("shuffle");
  };
</script>

<div class="shuffle">
  <button on:click={handleShuffle}>
    <span class="name">Shuffle</span><span class="icon" />
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
    width: 2em;
    height: 2em;
    background-image: url(../assets/shuffle.svg);
    background-size: 1em 1em;
    background-position: center;
    background-repeat: no-repeat;
    opacity: 0.5;
  }
</style>
