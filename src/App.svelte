<script>
  import Header from './Header.svelte';

  let pageContent = '';

  function loadPage(event) {
    const title = event.detail.title;
    console.log(`Loading ${title}...`);
    const url = `https://en.wikipedia.org/api/rest_v1/page/mobile-html/${title}`;
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
</script>

<Header on:loadPage={loadPage}/>
<main>
  {@html pageContent}
</main>

<style>
</style>
