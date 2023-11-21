<script>
  import REPL from "$lib/REPL.svelte";
</script>

<main>
  <h1>Silly Markdown REPL</h1>

  <p>
    The code for this REPL is in <a
      href="https://github.com/archiewood/silly-repl">this repo</a
    >.
  </p>

  <REPL />
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
</style>
