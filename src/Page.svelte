<svelte:head>
  <meta charset="utf-8" />
  <base href="//en.wikipedia.org/wiki/" />
  <meta http-equiv="content-language" content="en" />
  <link
    rel="stylesheet"
    href="//meta.wikimedia.org/api/rest_v1/data/css/mobile/base"
  />
  <link
    rel="stylesheet"
    href="//en.wikipedia.org/api/rest_v1/data/css/mobile/site"
  />
  <link
    rel="stylesheet"
    href="//meta.wikimedia.org/api/rest_v1/data/css/mobile/pagelib"
  />
  <meta
    name="viewport"
    content="width=device-width, user-scalable=no, initial-scale=1, shrink-to-fit=no"
  />
</svelte:head>

{#await loadLead(title)}
<p>Loading {title}...</p>
{:then lead}
<div
  class="content mw-content mw-content-ltr sitedir-ltr ltr mw-body-content parsoid-body mediawiki mw-parser-output"
>
  <header>
    <div class="pcs-edit-section-header">
      <h1 data-id="0" class="pcs-edit-section-title">{lead.displaytitle}</h1>
      <span class="pcs-edit-section-link-container">
        <a
          href="/w/index.php?title=A&amp;action=edit&amp;section=0"
          data-id="0"
          data-action="edit_section"
          class="pcs-edit-section-link"
        >
        </a>
      </span>
    </div>
  </header>
  <main id="content">
    <section data-mw-section-id="0">{@html lead.sections[0].text}</section>
  </main>
</div>
{/await}

<script>
  export let title;

  let lead = "";

  async function loadLead(title) {
    console.log(`Loading lead for ${title}...`);
    const url = `https://en.wikipedia.org/api/rest_v1/page/mobile-sections-lead/${title}`;
    console.log(`url: ${url}`);
    return fetch(url)
      .then(response => {
        return response.json();
      })
      .then(json => {
        lead = json;
        return json;
      });
  }

  async function loadPage(title) {
    loadLead(title);
  }
</script>

<style></style>
