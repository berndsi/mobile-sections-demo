<script>
  import Header from './Header.svelte';

  function loadPage(event) {
    alert(event.detail.title);
  }
</script>

<Header on:loadPage={loadPage}/>
<main></main>

<style>
</style>
