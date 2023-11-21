<script>
    let inputCode = '';
    let outputHtml = '';
  
    const compile = (input) => {
      // Placeholder for the compile function
      // You can replace this with your actual compilation logic
      return input;
    };
  
    const evaluateCode = () => {
      try {
        outputHtml = compile(inputCode);
      } catch (error) {
        outputHtml = `Error: ${error.message}`;
      }
    };
  </script>
  
  <style>
    main {
      display: flex;
      gap: 20px;
    }
  
    textarea {
      flex: 1;
      height: 200px;
    }
  
    button {
      flex: 0;
    }
  
    .output-container {
      flex: 1;
    }
  </style>
  
  <main>
    <textarea bind:value={inputCode} placeholder="Enter HTML code"></textarea>
    <button on:click={evaluateCode}>Run</button>
    {#if outputHtml}
      <div class="output-container">
        <h3>Output:</h3>
        {@html outputHtml}
      </div>
    {/if}
  </main>
  