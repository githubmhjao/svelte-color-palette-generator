<script>
  import { flip } from "svelte/animate";
  import { send, receive } from "./transition.js";

  import lock from "../assets/lock.svg";
  import unlock from "../assets/unlock.svg";

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
            <img src={lock} alt="color-locked" />
          {:else}
            <img src={unlock} alt="color-unlocked" />
          {/if}
        </label>
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
    display: flex;
    width: 3em;
    height: 3em;
    padding: 0.7em;
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
