<script context="module">
  export const router = false
</script>

<script>
  import Paragraph from "../components/paragraph.svelte"
  import Info from "../components/info.svelte"
  import { completedSteps } from "../stores"
  import { fly } from "svelte/transition"

  function scrollToBottom() {
    window.scrollTo({
      top: document.body.scrollHeight,
      behavior: "smooth",
    })
  }
</script>

<Info />

<div class="px-4 sm:px-6 lg:px-8">
  <div class="min-h-screen flex flex-col justify-between">
    <div>
      <div class="mb-16 mt-8 special-font">
        <h1>How to make</h1>
        <h1 class="text-9xl font-black md:tracking-wider">CHILI CON CARNE</h1>
      </div>

      <div class="tracking-wide flex flex-col gap-2 max-w-7xl text-justify">
        <p>
          Willkommen auf meinem Blog! Für das beste Chili con Carne bist du hier
          genau richtg. Während meiner Reise druch Mexico habe ich das beste
          Rezept - oder so sagt man - allerzeiten aufgelesen. Damit wird jede
          Dinnereinladung zu einem Erfolg.
        </p>

        <p>
          Dieses Rezept erinnert mich immer besonders an die warmen Abende,
          welche ich vor dem Freuer sitztend mit diesem Rezept verbrachte. Nach
          einem langen Tag gab es nichts besseres. Die Zutaten fan ich dabei auf
          den jeweiligen Märkten, voller lokaler Waren. Chillis aller Art! Doch
          für den ungewohnten Leser habe ich das Rezept etwas angepasst. Auch
          ohne original mexikanischer Schoten ist dieses Rezept umwerfend - und
          einfach obendrein. Auf was wartest du? Los Kochen!
        </p>
      </div>
    </div>

    <p class="mt-8 text-xl text-red-300 italic">
      Ganz vergessen - ich hatte leider noch keine Zeit das Rezept richtig zu
      übersetzen. Aber du solltest das schon schaffen!
    </p>

    <div class="mb-8 flex max-w-7xl justify-between">
      <h1 class="font-bold special-font mt-8">Rezept</h1>
      <button
        on:click={() =>
          window.scrollTo({
            top: window.innerHeight,
            behavior: "smooth",
          })}
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          aria-hidden="true"
          role="img"
          width="64"
          height="64"
          preserveAspectRatio="xMidYMid meet"
          viewBox="0 0 24 24"
        >
          <path
            d="M11 4h2v12l5.5-5.5l1.42 1.42L12 19.84l-7.92-7.92L5.5 10.5L11 16V4z"
            fill="currentColor"
          />
        </svg>
      </button>
    </div>
  </div>

  <div class="max-w-4xl mx-auto min-h-screen pt-20 pb-36">
    <div class="grid cols gap-x-6 gap-y-24">
      <div class="flex flex-col justify-between">
        <h2 class="font-bold special-font">Schritt 1</h2>
        <Paragraph
          id="step1"
          words={[
            ["Topf", "Öl", "Zimmer"],
            "in grosser",
            ["Pfanne", "Feuer", "Anlage"],
            "erhitzen,",
            "geschnittener",
            ["Wasser", "Knoblauch", "Gewürz"],
            "und",
            ["Glas", "Zwiebeln", "Messer"],
            "hinzufügen,",
            "kochen bis",
            ["Ofen", "Zwiebeln", "Eigentum"],
            "glasig sind.",
          ]}
          solution="Öl in grosser Pfanne erhitzen, geschnittener Knoblauch und Zwiebeln hinzufügen, kochen bis Zwiebeln glasig sind."
        />
      </div>
      <img class="w-72" src="../static/images/richtig1.jpg" alt="" />

      {#if $completedSteps.step1}
        <div
          transition:fly={{ y: 200, duration: 900 }}
          class="flex flex-col justify-between"
        >
          <h2 class="font-bold special-font">Schritt 2</h2>
          <Paragraph
            id="step2"
            words={[
              ["Wasser", "Fleisch", "Papier"],
              "hinzugeben und",
              "auf hoher",
              ["Menge", "Hitze", "Pfanne"],
              "anbraten.",
            ]}
            solution="Fleisch hinzugeben und auf hoher Hitze anbraten."
          />
        </div>
        <img
          transition:fly={{ y: 200, duration: 900 }}
          class="w-72"
          src="../static/images/richtig2.jpg"
          alt=""
        />
      {/if}

      {#if $completedSteps.step2}
        <div
          transition:fly={{ y: 200, duration: 900 }}
          on:introstart={scrollToBottom}
          class="flex flex-col justify-between"
        >
          <h2 class="font-bold special-font">Schritt 3</h2>
          <Paragraph
            id="step3"
            words={[
              ["Anzahl", "Gewürze", "Feuer"],
              "und",
              ["unscharfe Dinge", "wage Menge", "milde Chili"],
              "hinzugeben,",
              "weiter kochen bis",
              ["der Topf", "das Fleisch", "die Menge"],
              "durch ist.",
            ]}
            solution="Gewürze und milde Chili hinzugeben, weiter kochen bis das Fleisch durch ist."
          />
        </div>
        <img
          transition:fly={{ y: 200, duration: 900 }}
          class="w-72"
          src="../static/images/richtig3.jpg"
          alt=""
        />
      {/if}

      {#if $completedSteps.step3}
        <div
          transition:fly={{ y: 200, duration: 900 }}
          on:introstart={scrollToBottom}
          class="flex flex-col justify-between"
        >
          <h2 class="font-bold special-font">Schritt 4</h2>
          <Paragraph
            id="step4"
            words={[
              "In neuen",
              "geben,",
              ["Glas", "Topf", "Gewürz"],
              ["Messer, Gabel", "Bohnen, Tomaten", "Nieren, Leber"],
              "und",
              ["Öl", "Abgas", "Wasser"],
              "hinzugeben,",
              "aufkochen.",
            ]}
            solution="In neuen Topf geben, Bohnen, Tomaten und Wasser hinzugeben, aufkochen."
          />
        </div>
        <img
          transition:fly={{ y: 200, duration: 900 }}
          class="w-72"
          src="../static/images/richtig4.jpg"
          alt=""
        />
      {/if}

      {#if $completedSteps.step4}
        <div
          transition:fly={{ y: 200, duration: 900 }}
          on:introstart={scrollToBottom}
          class="flex flex-col justify-between"
        >
          <h2 class="font-bold special-font">Schritt 5</h2>
          <Paragraph
            id="step5"
            words={[
              "Auf",
              ["kleiner Höhe", "grosser Bemühung", "niedriger Hitze"],
              "40 - 90",
              ["Distanz", "Gramm", "Minuten"],
              "köcheln lassen.",
            ]}
            solution="Auf niedriger Hitze 40 - 90 Minuten köcheln lassen."
          />
        </div>
        <img
          transition:fly={{ y: 200, duration: 900 }}
          class="w-72"
          src="../static/images/richtig5.jpg"
          alt=""
        />
      {/if}

      {#if $completedSteps.step5}
        <div
          transition:fly={{ y: 200, duration: 900 }}
          on:introstart={scrollToBottom}
          class="flex flex-col justify-between"
        >
          <h2 class="font-bold special-font">Schritt 6</h2>
          <Paragraph
            id="step6"
            words={[
              "Abschmecken",
              "und mit",
              ["Balast", "Pfanne", "Brot"],
              "oder",
              ["Teller", "mehreren", "Reis"],
              "servieren.",
            ]}
            solution="Abschmecken und mit Brot oder Reis servieren."
          />
        </div>
        <img
          transition:fly={{ y: 200, duration: 900 }}
          class="w-72"
          src="../static/images/richtig6.jpg"
          alt=""
        />
      {/if}

      {#if $completedSteps.step6}
        <div
          transition:fly={{ y: 200, duration: 900 }}
          on:introstart={scrollToBottom}
          class="flex flex-col justify-between"
        >
          <h2 class="font-bold special-font">Tipp</h2>
          <Paragraph
            id="tipp"
            words={[
              "etwas",
              ["Während dem Fahren", "Beim Servieren", "Zum Arbeiten"],
              "für einen",
              [
                "lustigen Zufall!",
                "komische Ausnahme!",
                "besonderen Geschmack!",
              ],
              "beigeben",
              ["Molasse und Karton", "Wasser und Teller", "Joghurt und Käse"],
            ]}
            solution="Beim Servieren etwas Joghurt und Käse beigeben für einen besonderen Geschmack!"
          />
        </div>
        <img
          transition:fly={{ y: 200, duration: 800 }}
          class="w-72"
          src="../static/images/richtigtipp.jpg"
          alt=""
        />
      {/if}
      {#if $completedSteps.tipp}
        <div
          transition:fly={{ y: 200, duration: 900 }}
          on:introstart={scrollToBottom}
          class="flex justify-between col-span-2"
        >
          <button
            on:click={() =>
              window.scrollTo({
                top: 0,
                left: 0,
                behavior: "smooth",
              })}
            class="text-6xl font-bold special-font hover:text-red-600 transition ease-in-out"
          >
            Top
          </button>
          <a
            href="/about"
            class="text-6xl font-bold special-font hover:text-red-600 transition ease-in-out"
          >
            About
          </a>
        </div>
      {/if}
    </div>
  </div>
</div>

<style>
  .cols {
    grid-template-columns: minmax(0, 1fr) max-content;
  }
</style>
