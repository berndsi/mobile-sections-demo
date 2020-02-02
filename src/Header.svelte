<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  let title;

  function loadPage() {
    if (title) {
      dispatch("loadPage", { title });
    }
  }
</script>

<header>
  <div class="branding-box">
    <img
      class="logo"
      src="https://en.m.wikipedia.org/static/images/mobile/copyright/wikipedia-wordmark-en.svg"
      alt="Wikipedia"
    />
  </div>
  <form on:submit|preventDefault="{loadPage}">
    <input
      id="searchInput"
      class="search"
      name="search"
      bind:value="{title}"
      autocomplete="off"
      placeholder="Enter page title"
      aria-label="Enter page title"
    />
    <button class="loadButton" aria-label="Load page" type="submit">
      Load
    </button>
  </form>
</header>

<style>
  header {
    display: flex;
    background-color: #eaecf0;
    border: 0;
    box-shadow: inset 0 -1px 3px rgba(0, 0, 0, 0.08);
    height: 2.25em;
    padding: 0.5rem;
    border-top: 1px solid #c8ccd1;
    align-items: baseline;
  }

  .branding-box {
    padding-right: 2rem;
  }

  .logo {
    width: 116px;
    height: 18px;
    vertical-align: middle;
  }
</style>
