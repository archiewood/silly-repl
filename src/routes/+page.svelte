<script>
  import REPL from "$lib/REPL.svelte";

  function share() {
    navigator.clipboard
      .writeText(window.location.href)
      .then(() => alert("Sharing link copied to clipboard"))
      .catch((err) => console.error("Failed to copy URL: ", err));
  }
</script>

<main>
  <h1>Silly Markdown REPL</h1>

  <p>
    The code for this REPL is in <a
      href="https://github.com/archiewood/silly-repl">this repo</a
    >.
  </p>

  <REPL />

  <button on:click={share}>Share Link</button>
</main>

<style>
  h1 {
    /* center */
    text-align: center;
    margin-top: 1em;
  }

  main {
    height: 95vh;
    display: flex;
    flex-direction: column;
  }
  p {
    /* center */
    text-align: center;
  }

  button {
    margin: 1em auto 0;
    padding: 0.5em 1em;
    font-size: 1em;
    color: white;
    background-color: #007bff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  button:hover {
    background-color: #0056b3;
  }
</style>
