<script>
  import { onMount } from 'svelte';
  import Header from './Header.svelte';

  let pageContent = '';

  function loadPage(title) {
    console.log(`Loading ${title}...`);
    const url = `https://en.wikipedia.org/api/rest_v1/page/mobile-html/${title}`;
    // const url = `http://localhost:8888/en.wikipedia.org/v1/page/mobile-html/${title}`;
    console.log(`url: ${url}`);
    fetch(url)
    .then(response => {
      return response.text();
    }).then(text => {
      pageContent = text;
    }).catch(err => {
      console.warn('Something went wrong.', err);
    });
  }

  function loadPageEvent(event) {
    loadPage(event.detail.title);
  }

  onMount(async () => {
    loadPage('Main_Page');
  });
</script>

<Header on:loadPage={loadPage}/>
<main>
  {@html pageContent}
</main>

<style>
</style>
