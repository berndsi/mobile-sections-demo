<Header on:loadPage="{loadPageEvent}"></Header>
{#if title}
<Page {title}></Page>
{/if}

<script>
  import { onMount } from "svelte";
  import Header from "./Header.svelte";
  import Page from "./Page.svelte";

  let title;

  function loadPageEvent(event) {
    title = event.detail.title;
  }

  onMount(async () => {
    title = "Main_Page";
  });
</script>

<style></style>
