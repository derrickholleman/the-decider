<script>
  import { RANDOMIZER_OPTIONS } from "./randomizerOptions";
  let selectedOption;
  let selectedRandomOption;

  const handleRandomize = () => {
    if (selectedOption) {
      selectedRandomOption =
        selectedOption.options[
          Math.floor(Math.random() * selectedOption.options.length)
        ];
    }
  };
</script>

<svelte:head>
  <title>The Decider</title>
</svelte:head>

<div class="page-wrapper">
  <h1>The Decider</h1>
  <select
    bind:value={selectedOption}
    on:change={() => (selectedRandomOption = "")}
  >
    <option value="">-- Choose an Option --</option>
    {#each RANDOMIZER_OPTIONS as randomOption}
      <option value={randomOption}>
        {randomOption.displayText}
      </option>
    {/each}
  </select>

  <button on:click={handleRandomize} disabled={!selectedOption}>
    Randomize!
  </button>

  <div class="selected-option">
    {#if selectedRandomOption}
      {selectedRandomOption}
    {/if}
  </div>
</div>

<style>
  h1 {
    font-size: clamp(2rem, 5vw, 6rem);
    color: #08415c;
  }
  .page-wrapper {
    text-align: center;
  }
  button {
    cursor: pointer;
    margin-left: 1rem;
    padding: 0.5rem 1rem;
    color: white;
    background-color: #709255;
    border-color: #709255;
    border-radius: 5px;
    font-weight: bold;
  }
  button:disabled {
    pointer-events: none;
  }
  button:active {
    transform: scale(0.98);
  }
  button:hover {
    background-color: #81a762;
    border-color: #81a762;
  }
  .selected-option {
    margin-top: 1.5rem;
    font-size: 1.5rem;
    color: #08415c;
    font-weight: 600;
  }

  /* #08415c */
</style>
