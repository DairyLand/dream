<script>
  let meme = null;

  async function fetchRandomMeme() {
    try {
      const response = await fetch('https://meme-api.com/gimme');
      if (response.ok) {
        const data = await response.json();
        meme = data.url;
      } else {
        console.error('Failed to fetch a random meme.');
      }
    } catch (error) {
      console.error('An error occurred while fetching a meme:', error);
    }
  }
</script>

<main>
  <h1>Random Meme Generator</h1>

  <button on:click={fetchRandomMeme}>Get Random Meme</button>

  {#if meme}
    <img src={meme} alt="Random Meme" style="max-width: 100%;" />
  {/if}
</main>
