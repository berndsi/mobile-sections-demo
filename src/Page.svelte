{#await loadLead(title)}
<p>waiting for {title} to be loaded...</p>
{:then lead}
<header>
  <h1>{lead.displaytitle}</h1>
</header>
<main>{@html lead.sections[0].text}</main>
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
