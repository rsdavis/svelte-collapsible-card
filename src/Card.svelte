<script>
  // 	https://css-tricks.com/using-css-transitions-auto-dimensions/#technique-3-javascript

  let state = "OPEN";
  let ref = null;
  const transition = "height 0.2s ease";

  const prefersReducedMotion = window.matchMedia(
    "(prefers-reduced-motion: reduce)"
  ).matches;

  function requestFrame() {
    return new Promise((r) => requestAnimationFrame(r));
  }

  function transitionEnd() {
    return new Promise((resolve) => {
      ref.addEventListener("transitionend", function f() {
        ref.removeEventListener("transitionend", f);
        resolve();
      });
    });
  }

  async function closeCard() {
    if (prefersReducedMotion) {
      ref.style.height = "0";
      state = "CLOSED";
      return;
    }

    state = "CLOSING";

    // temporarily turn off transitions
    ref.style.transition = "";
    await requestFrame();

    // set height to pixels and turn transition back on
    ref.style.height = ref.scrollHeight.toString() + "px";
    ref.style.transition = transition;
    await requestFrame();

    // start the closing transition
    ref.style.height = "0px";

    // wait for transition to finish
    await transitionEnd();
    state = "CLOSED";
  }

  async function openCard() {
    if (prefersReducedMotion) {
      ref.style.height = ref.scrollHeight + "px";
      state = "OPEN";
      return;
    }

    state = "OPENING";
    ref.style.height = ref.scrollHeight + "px";

    await transitionEnd();

    // set height back to auto for dynamic content
    ref.style.height = "auto";
    state = "OPEN";
  }

  function toggle() {
    if (state === "OPEN") closeCard();
    else if (state === "CLOSED") openCard();
  }
</script>

<style>
  .card {
    position: relative;
    border: 1px solid black;
    border-radius: 5px;
  }

  .card + .card {
    margin-top: 1em;
  }

  .header {
    border-radius: 5px 5px 0 0;
    background-color: white;
    cursor: pointer;
  }

  .header.closed {
    border-radius: 5px;
  }

  .body {
    border-radius: 0 0 5px 5px;
    padding: 0;
    height: auto;
    overflow: hidden;
  }

  .body.closed {
    border: none;
  }

  @media (prefers-reduced-motion) {
    .body {
      transition: none;
    }
  }
</style>

<div class="card" aria-expanded={state === 'OPEN'}>
  <div
    class="header"
    on:click={() => toggle()}
    class:closed={state === 'CLOSED'}>
    <slot name="header" />
  </div>

  <div class="body" bind:this={ref} class:closed={state === 'CLOSED'}>
    <slot name="body" />
  </div>

  <slot />
</div>
