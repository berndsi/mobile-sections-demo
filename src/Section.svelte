<section data-mw-section-id="${section.id}">
  {@html heading} {@html section.text}
</section>

<script>
  export let section;
  let headingTag = `h${section.toclevel + 1}`;
  let heading = `<${headingTag} id=${section.anchor}>${section.line}</${headingTag}>`;
</script>
