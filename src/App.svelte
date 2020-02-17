<script>
  import { onMount } from "svelte";
  import Header from "./Header.svelte";

  let lead = "";

  function loadLead(title) {
    console.log(`Loading lead for ${title}...`);
    const url = `https://en.wikipedia.org/api/rest_v1/page/mobile-sections-lead/${title}`;
    console.log(`url: ${url}`);
    fetch(url)
      .then(response => {
        return response.json();
      })
      .then(json => {
        lead = json;
      })
      .catch(err => {
        console.warn("Something went wrong.", err);
      });
  }

  function loadPage(title) {
    loadLead(title);
  }

  function loadPageEvent(event) {
    loadPage(event.detail.title);
  }

  onMount(async () => {
    loadPage("Main_Page");
  });
</script>

<Header on:loadPage="{loadPageEvent}"></Header>
<header>
  <h1>{lead.displaytitle}</h1>
</header>
<main></main>

<style></style>
