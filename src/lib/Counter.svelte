<script>
  import { createEventDispatcher } from "svelte";
  
  export let count = 3;

  const dispatch = createEventDispatcher();

  const changeCount = (amount) => {
    dispatch('changeCount', {
      change: amount
    })
  };

</script>

<section>
  <h1>Create Color Palette for Me!</h1>

  <div class='counter'>
    <button on:click={() => changeCount(-1)}>
      <svg aria-hidden="true" viewBox="0 0 1 1">
        <path d="M0,0.5 L1,0.5" />
      </svg>
    </button>
    <div class="counter-viewer">
      <p>{count}</p>
    </div>
    <button on:click={() => changeCount(1)}>
      <svg aria-hidden="true" viewBox="0 0 1 1">
        <path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
      </svg>
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

  svg {
		width: 25%;
		height: 25%;
	}

	path {
		vector-effect: non-scaling-stroke;
		stroke-width: 2px;
		stroke: #444;
	}
</style>
