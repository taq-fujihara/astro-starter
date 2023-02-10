<script>
  let input = '{"foo":"bar"}'
  let errorMessage = null

  function format() {
    try {
      input = JSON.stringify(JSON.parse(input), null, 2)
      errorMessage = null
    } catch (error) {
      errorMessage = error.message
    }
  }

  function copyToClipboard() {
    navigator.clipboard.writeText(input)
  }
</script>

{#if errorMessage}
  <div class="error">
    {errorMessage}
  </div>
{/if}

<div>
  <textarea bind:value={input} cols="30" rows="10" />
</div>
<div>
  <button on:click={format}>Format</button>
  <button on:click={copyToClipboard}>Copy</button>
</div>

<style>
  .error {
    color: red;
  }
</style>
