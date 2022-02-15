<script>
  import Word from "./word.svelte"
  import { paragraphs, completedSteps } from "../stores"

  import { onMount } from "svelte"
  import { dndzone } from "svelte-dnd-action"
  import { flip } from "svelte/animate"
  let dndOpts = {
    flipDurationMs: 200,
    dropFromOthersDisabled: true,
    dragDisabled: false,
    dropTargetStyle: { outline: "rgba(255, 255, 255, 0.5) solid 2px" },
  }

  export let id
  export let words
  export let solution

  $paragraphs[id] = words.map((e, i) => ({ id: i, value: e }))

  function handleSort(e) {
    $paragraphs[id] = e.detail.items
  }

  let pdom
  onMount(() => {
    const observer = new MutationObserver(() => checkResult())
    observer.observe(pdom, {
      subtree: true,
      characterDataOldValue: true,
    })
  })

  function checkResult() {
    const attempt = $paragraphs[id]
      .map(({ value: v }) => (Array.isArray(v) ? v[0] : v))
      .join(" ")
    $completedSteps[id] = attempt === solution
    dndOpts.dragDisabled = $completedSteps[id]
  }
</script>

<div>
  <p
    class="flex flex-row flex-wrap text-3xl rounded"
    use:dndzone={{ items: $paragraphs[id], ...dndOpts }}
    on:consider={handleSort}
    on:finalize={handleSort}
    on:finalize={checkResult}
    bind:this={pdom}
  >
    {#each $paragraphs[id] as word (word.id)}
      <div
        class="px-1 transition ease-in-out hover:bg-slate-400/20 rounded-md"
        animate:flip={{ duration: dndOpts.flipDurationMs }}
      >
        {#if Array.isArray(word.value)}
          <Word stepId={id} wordId={word.id} />
        {:else}
          {word.value}
        {/if}
      </div>
    {/each}
  </p>
</div>
