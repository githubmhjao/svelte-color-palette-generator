<header>
  <nav>
		<svg viewBox="0 0 2 3" aria-hidden="true">
			<path d="M0,0 L1,2 C1.5,3 1.5,3 2,3 L2,0 Z" />
		</svg>
    <div class='title'>
      Color Palettes by Svelte
    </div>
		<svg viewBox="0 0 2 3" aria-hidden="true">
			<path d="M0,0 L0,3 C0.5,3 0.5,3 1,2 L2,0 Z" />
		</svg>
	</nav>
</header>

<style>
  header {
    display: flex;
    justify-content: center;
  }

  nav {
		display: flex;
		justify-content: center;
    --height: 3em;
	}

	svg {
		width: 2em;
		height: var(--height);
		display: block;
	}

	path {
		fill: var(--color-bg-3);
	}

  .title {
    background: var(--color-bg-3);
    line-height: var(--height);
  }
</style>