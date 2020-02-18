{#if title}
<Page {lang} {title} {rev}></Page>
{/if}

<script>
  import { onMount } from "svelte";
  import Page from "./Page.svelte";

  let lang;
  let title;
  let rev;

  function loadPageEvent(event) {
    title = event.detail.title;
  }

  onMount(async () => {
    if (window.location.pathname === "/") {
      rev = undefined;
    } else {
      const parts = window.location.pathname.split("/");
      lang = parts[1];
      title = parts[2];
      rev = parts[3];
    }
    if (!title) {
      title = "Main_Page";
      // title = "A";
    }
    if (!lang) {
      lang = "en";
    }
  });
</script>

<style></style>
