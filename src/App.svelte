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

<div class="page-wrapper">
  <h1>The Decider</h1>
  <select
    bind:value={selectedOption}
    on:change={() => (selectedRandomOption = "")}
  >
    <option>-- Choose an Option --</option>
    {#each RANDOMIZER_OPTIONS as randomOption}
      <option value={randomOption}>
        {randomOption.displayText}
      </option>
    {/each}
  </select>

  <button on:click={handleRandomize}> Randomize! </button>

  <div class="selected-option">
    {#if selectedRandomOption}
      {selectedRandomOption}
    {/if}
  </div>
</div>

<style>
  .page-wrapper {
    text-align: center;
  }
  button {
    cursor: pointer;
  }
  .selected-option {
    margin-top: 2rem;
    font-size: 1.5rem;
  }
</style>
