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

  async function loadJson(uri) {
    let response = await fetch(uri);
    return await response.json();
  }

  async function getMainPageTitle(lang) {
    const uri = `https://${lang}.wikipedia.org/w/api.php?action=query&format=json&meta=siteinfo&siprop=general&origin=*`;
    const siteinfo = await loadJson(uri);
    return siteinfo.query.general.mainpage;
  }

  onMount(async () => {
    rev = undefined;

    const parts = window.location.pathname.split("/");
    lang = parts[1];
    title = parts[2];
    rev = parts[3];

    if (!lang) {
      lang = "en";
    }

    if (!title) {
      if (lang === "en") {
        title = "Main_Page";
        // title = "A";
      } else {
        title = await getMainPageTitle(lang);
      }
    }
  });
</script>

<style></style>
