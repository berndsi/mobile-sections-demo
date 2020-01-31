<header>
  <div class="branding-box">
    <img
      class="logo"
      src="https://en.m.wikipedia.org/static/images/mobile/copyright/wikipedia-wordmark-en.svg"
      alt="Wikipedia"
    />
  </div>
  <div class="search-box">
    <input
      id="searchInput"
      class="search"
      name="search"
      autocomplete="off"
      placeholder="Enter Wikipedia page title"
      aria-label="Wikipedia page title"
    />
  </div>
  <button class="loadButton">Load</button>
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
