<script>
  import { onMount } from 'svelte';
  import SvelteMarkdown from 'svelte-markdown';

  let inputCode = "";

  // When the component mounts, read the inputCode from the URL
  onMount(() => {
    if (typeof window !== 'undefined') {
      const params = new URLSearchParams(window.location.search);
      inputCode = params.get('inputCode') || '';
    }
  });

  // Whenever inputCode changes, update the URL
  $: {
    if (inputCode && typeof window !== 'undefined') {
      const params = new URLSearchParams();
      params.set('inputCode', inputCode);
      window.history.pushState({}, '', '?' + params.toString());
    }
  }
</script>

<article>
  <div class="input-container">
    <h3>Input</h3>
    <textarea
      class="input"
      bind:value={inputCode}
      placeholder="Write Markdown"
    />
  </div>
  <div class="output-container">
    <h3>Output</h3>

    <div class="output">
      {#if inputCode === ""}
        <div class="default-text">Output will appear here</div>
      {:else}
        <SvelteMarkdown source={inputCode} />
      {/if}
    </div>
  </div>
</article>
<style>
  * {
    box-sizing: border-box;
  }

  article {
    display: flex;
    flex-direction: row;
    height: 100%;
    margin-left: 1em;
    margin-right: 1em;
  }

  h3 {
    text-align: center;
    margin-top: 1em;
    margin-bottom: 1em;
  }

  .input-container,
  .output-container {
    flex: 1;
    display: flex;
    flex-direction: column;
    margin-left: 1em;
    margin-right: 1em;
    max-height: 100vh; /* Set a maximum height */
    overflow: auto; /* Add a scrollbar when necessary */
  }

  .input,
  .output {
    flex: 1;
    border: 1px solid #ccc;
    padding: 10px;
    overflow: auto;
    resize: none;
    border-radius: 5px;
  }

  .default-text {
    color: #777;
  }

  @media (max-width: 600px) {
    article {
      flex-direction: column;
    }
  }
</style>
