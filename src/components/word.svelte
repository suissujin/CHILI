<script>
  import { slide } from "svelte/transition"
  import { paragraphs, completedSteps } from "../stores"
  import { clickOutside } from "../helpers"

  export let stepId
  export let wordId

  let words = $paragraphs[stepId].find((elem) => elem.id === wordId).value

  function selectWord(e) {
    if ($completedSteps[stepId]) {
      return
    }

    const word = e.target.value
    // find index of selected word
    const index = words.findIndex((elem) => elem === word)
    // delete the word from the words array by using the found index
    words.splice(index, 1)
    // prepend the word to the list of remaining words
    words = [word, ...words]
    const wordIndex = $paragraphs[stepId].findIndex(
      (elem) => elem.id === wordId
    )
    $paragraphs[stepId][wordIndex] = { id: wordId, value: words }
  }

  let tooltip = false
  function openTooltip() {
    if (!$completedSteps[stepId]) {
      tooltip = !tooltip
    }
  }
</script>

<div class="relative group">
  <div
    class:clickable={!$completedSteps[stepId]}
    class:open={tooltip}
    on:click={openTooltip}
  >
    {words[0]}
  </div>
  {#if tooltip}
    <div
      role="tooltip"
      class="z-20 absolute cursor-default shadow-lg bg-white p-4 mt-2 rounded whitespace-nowrap"
      use:clickOutside
      on:outclick={() => (tooltip = false)}
      in:slide={{ duration: 200 }}
    >
      <svg
        class="absolute text-white fill-current -mt-2 ml-1 left-0 top-0"
        width="16px"
        height="9px"
        viewBox="0 0 16 9"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
      >
        <polygon id="triangle" points="8,0 16,9 0,9" />
      </svg>
      <h3 class="text-2xl text-black font-bold pb-1">{words[0]}</h3>
      <ul>
        {#each words.slice(1) as word}
          <li>
            <button
              class="text-lg leading-4 text-gray-600"
              on:click={selectWord}
              value={word}
            >
              {word}
            </button>
          </li>
        {/each}
      </ul>
    </div>
  {/if}
</div>

<style>
  .clickable {
    @apply cursor-pointer font-bold transition ease-in-out hover:text-red-600;
  }

  .open {
    @apply text-black font-black hover:text-black;
    -webkit-text-stroke: 1px white;
  }
</style>
