<script>
  import Header from "./lib/Header.svelte";
  import Counter from "./lib/Counter.svelte";
  import Palettes from "./lib/Palettes.svelte";
  import Shuffle from "./lib/Shuffle.svelte";
  import Modal from "./lib/Modal.svelte";

  let showModal = false;
  const initCount = 3;
  let globalId = 0;
  const generateTone = () =>
    ("0" + Math.round(255 * Math.random()).toString(16)).slice(-2);
  const generateColor = () =>
    [generateTone(), generateTone(), generateTone()].reduce(
      (a, c) => a + c,
      ""
    );
  const generatePalette = () => ({
    id: globalId++,
    color: generateColor(),
    lock: false,
  });

  let palettes = [...Array(initCount)].map(generatePalette);
  $: count = palettes.length;

  const handleCount = (event) => {
    const change = event.detail.change;
    const tobeCount = count + change;

    if (change === 1 && tobeCount < 7) {
      palettes = [...palettes, generatePalette()];
    } else if (change === -1 && tobeCount > 0) {
      palettes = palettes.slice(0, -1);
    } else {
      showModal = true;
    }
  };

  const handleLock = (event) => {
    const eventId = event.detail.id;
    palettes = palettes.map((p) => {
      if (p.id === eventId) {
        return { ...p, lock: !p.lock };
      } else {
        return p;
      }
    });
  };

  const handleShuffle = () => {
    palettes = palettes.map((p) => {
      if (p.lock) return p;
      else {
        return { ...p, color: generateColor() };
      }
    });
  };
</script>

<main>
  <Header />

  <Counter {count} on:changeCount={handleCount} />

  <Palettes bind:palettes on:lock={handleLock} />

  <Shuffle on:shuffle={handleShuffle} />

  <div class="footer">
    <p class="comment">
      Check out <a
        href="https://ithelp.ithome.com.tw/users/20120178/ironman/7031"
        target="_blank"
        rel="noreferrer">Svelte Tutorial</a
      >, the awesome article powered by TheGreatSvelte!
    </p>
  </div>
</main>

<Modal bind:showModal />

<style>
  main {
    height: 100vh;
    max-width: 500px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .footer {
    margin: 1em 0;
  }

  p.comment {
    color: #888;
    margin: 1em 0.5em;
  }

  p.comment a {
    text-decoration: none;
  }
</style>
