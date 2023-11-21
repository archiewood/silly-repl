<script>
    import SvelteMarkdown from 'svelte-markdown'
    let inputCode = '';
  </script>
  
  <main>
    <div class="input-container">
      <h3>Input</h3>
      <textarea class=input bind:value={inputCode} placeholder="Write Markdown" ></textarea>
    </div>
    <div class="output-container">
      <h3>Output</h3>
      
      <div class=output>
        {#if inputCode === ''}
            <div class=default-text>
                Output will appear here
            </div>
        {:else}
            <SvelteMarkdown source={inputCode}/>
        {/if}
      </div>
    </div>
  </main>
  
  <style>
    
    main {
      display: flex;
      gap: 20px;
      height: 100vh;
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
      height: 50%; /* Set the height to 100% */
      overflow: auto;
      padding: 10px;
    }
  
    .input {
      height: 50%; /* Set the height to 100% */
      border: 1px solid #ccc;
      padding: 10px;
    }

    .default-text {
        color: #777;
    }
  </style>
  
  