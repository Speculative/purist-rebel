<script lang="ts">
  export let text;

  function handleBlur(e: Event) {
    const target = e.currentTarget as HTMLElement;
    if (target.textContent === "") {
      text = "...";
    }
  }

  function handleFocus(e: Event) {
    const target = e.currentTarget;
    // https://stackoverflow.com/questions/3805852/select-all-text-in-contenteditable-div-when-it-focus-click
    setTimeout(function () {
      let sel, range;
      if (window.getSelection && document.createRange) {
        range = document.createRange();
        range.selectNodeContents(target);
        sel = window.getSelection();
        sel.removeAllRanges();
        sel.addRange(range);
      }
    }, 1);
  }
</script>

<span
  contenteditable="true"
  spellcheck="false"
  on:focus={handleFocus}
  on:blur={handleBlur}
  bind:textContent={text}>{text}</span
>
