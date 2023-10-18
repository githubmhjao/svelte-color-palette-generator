<script>
  import { flip } from "svelte/animate";
  import { send, receive } from "./transition.js";

  import Icon from "./Icon.svelte";
  import { lockIcon, unlockIcon } from "./icon.js";

  export let palettes;
</script>

<div class="palettes">
  {#each palettes as palette (palette.id)}
    <div
      class="card"
      in:receive={{ key: palette.id }}
      out:send={{ key: palette.id }}
      animate:flip={{ duration: 200 }}
    >
      <div class="palette" style:--color-palette={"#" + palette.color} />
      <div class="hex-code">
        <label>
          <input bind:value={palette.color} />
        </label>
      </div>
      <div class="lock-icon">
        <label>
          <input type="checkbox" bind:checked={palette.lock} />
          {#if palette.lock}
            <Icon i={{ ...lockIcon, height: "1.5em" }} />
          {:else}
            <Icon i={{ ...unlockIcon, height: "1.5em" }} />
          {/if}
        </label>
      </div>
    </div>
  {:else}
    <div class="card no-color">
      <div>
        <p>No color to show. Please add a color.</p>
      </div>
    </div>
  {/each}
</div>

<style>
  .palettes {
    margin: 1em;
    flex: 1;
    display: grid;
    gap: 0.5em;
  }

  .card {
    padding: 0.5em;
    background: var(--color-bg-3);
    border-radius: var(--border-radius);
    display: grid;
    grid-template-columns: 1fr 2fr 0.5fr;
    align-items: center;
  }

  .card.no-color {
    grid-template-columns: 1fr;
    font-size: 1.5em;
  }

  .card .palette {
    height: 100%;
    border-radius: 0.2em;
    background: var(--color-palette);
  }

  .card .hex-code input {
    font-size: 2em;
    padding: 0.2em 0;
    width: 80%;
    background: transparent;
    border-radius: 0.2em;
    text-align: center;
    text-transform: uppercase;
    border: none;
    outline: none;
    cursor: pointer;
  }

  .card .hex-code input:focus {
    background: var(--color-bg-2);
  }

  .card .lock-icon label {
    opacity: 0.3;
    cursor: pointer;
  }

  .card .lock-icon label:hover {
    opacity: 0.5;
  }

  .card .lock-icon input {
    display: none;
  }
</style>
