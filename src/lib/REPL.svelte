<script>
    import SvelteMarkdown from 'svelte-markdown'
    let inputCode = '';
  </script>
  
  <article>
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
  </article>
  
  <style>
    
    * {
  box-sizing: border-box;
}

article {
  display: flex;
  flex-direction: row;
  height: 100%;
  margin-left: 10px;
  margin-right: 10px;
}

h3 {
  text-align: center;
  margin-top: 1em;
  margin-bottom: 1em;

}

.input-container, .output-container {
  flex: 1;
  display: flex;
  flex-direction: column;
  margin-left: 10px;
  margin-right: 10px;
}

.input, .output {
  flex: 1;
  border: 1px solid #ccc;
  padding: 10px;
  overflow: auto;
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
  
  