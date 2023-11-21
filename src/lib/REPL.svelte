<script>
    import { afterUpdate } from 'svelte';
  
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
  
    // Run evaluateCode after each update (keystroke)
    afterUpdate(evaluateCode);
  </script>
  
  <main>
    <div class="input-container">
      <h3>Input</h3>
      <textarea class=input bind:value={inputCode} placeholder="Enter HTML" on:input={evaluateCode}></textarea>
    </div>
    <div class="output-container">
      <h3>Output</h3>
      <div class=output>
        {@html outputHtml}
      </div>
    </div>
  </main>
  
  <style>
    main {
      display: flex;
      gap: 20px;
    }
  
    .input-container {
      flex: 1;
      display: flex;
      flex-direction: column;
    }
  
    .output-container {
      flex: 1;
    }
  
    .output {
      border: 1px solid #ccc;
      height: 200px;
      overflow: auto;
      padding: 10px;
    }
  
    .input {
      height: 200px;
      border: 1px solid #ccc;
      padding: 10px;
    }
  </style>
  