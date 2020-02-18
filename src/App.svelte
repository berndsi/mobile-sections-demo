{#if title}
<Page {title}></Page>
{/if}

<script>
  import { onMount } from "svelte";
  import Page from "./Page.svelte";

  let title;

  function loadPageEvent(event) {
    title = event.detail.title;
  }

  onMount(async () => {
    console.log(window.location.pathname);
    if (window.location.pathname === "/") {
      title = "Main_Page";
      // title = "A";
    } else {
      title = window.location.pathname.substring(1);
    }
  });
</script>

<style></style>
