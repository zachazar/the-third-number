<script>
  import { fade } from "svelte/transition";
  import Story from "./Story.svelte";

  // Application flow
  const availableSteps = {
    welcome: "welcome",
    started: "started",
    story: "story",
  };
  let step = availableSteps.welcome;

  // Story inputs
  const storyInputs = {
    name: undefined,
    animal: undefined,
    number: undefined,
    transportation: undefined,
    state: undefined,
  };

  function createStory() {
    step = availableSteps.story;
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
  form {
    text-align: left;
  }

  h1,
  h2 {
    color: black;
    font-size: 4em;
    font-weight: 200;
  }
  h1 {
    font-size: 4em;
  }
  h2 {
    font-size: 2em;
    font-weight: 300;
  }

  label {
    display: inline;
  }

  @media (min-width: 640px) {
    main {
      max-width: 1000px;
    }
  }
  .important-text {
    font-weight: 600;
  }
  .begin-button {
    background-color: #8dc848;
    color: white;
  }
  .begin-button:hover {
    background-color: blue;
    color: rgb(255, 152, 34);
  }
  input[type="number"] {
    max-width: 100px;
  }
</style>

<main>
  {#if step === availableSteps.welcome}
    <div transition:fade>
      <h1>Welcome, birthday boy 🍰</h1>
      <h2 class="mt-2">
        You're about to embark on a quest for the third lock number
      </h2>
      <h2 class="has-text-primary-dark important-text">
        but you'll need your family's help.
      </h2>
      <button
        in:fade={{ delay: 5000 }}
        class="button mt-6 is-large is-rounded begin-button"
        on:click={() => {
          step = availableSteps.started;
        }}>Click here once&nbsp;
        <strong>Emryk</strong>,&nbsp;
        <strong>Asher</strong>,&nbsp;
        <strong>Sarah</strong>,&nbsp;and&nbsp;
        <strong>Tristan</strong>
        &nbsp;are ready...</button>
    </div>
  {:else if step === availableSteps.started}
    <div out:fade in:fade={{ delay: 1000 }}>
      <h2>Before we can begin...</h2>
      <form class="mt-4">
        <div class="field">
          <label for="answer_name" class="label">Emryk, enter
            <span class="has-text-primary">a name</span>.</label>
          <div class="control">
            <input
              class="input"
              type="text"
              id="answer_name"
              bind:value={storyInputs.name}
              placeholder="e.g Heraldo" />
          </div>
          <p class="help">
            A name can be anything, like "Skipper", "Amanda", "Saber Tooth", or
            even "Dr. Cornbread".
          </p>
        </div>

        <div class="field mt-4">
          <label for="answer_animal" class="label">Ask Asher for
            <span class="has-text-primary">an animal</span>.</label>
          <div class="control">
            <input
              id="answer_animal"
              class="input"
              type="text"
              bind:value={storyInputs.animal}
              placeholder="e.g Gorilla" />
          </div>
          <p class="help">
            Any type of animal. Like "Monkey", "Cat", "Sloth", or even "Bumble
            Bee".
          </p>
        </div>
        <div class="field mt-4">
          <label for="answer_state" class="label">Ask Mom for
            <span class="has-text-primary">a state in the United States</span>.</label>
          <div class="control">
            <input
              id="answer_state"
              class="input"
              type="text"
              bind:value={storyInputs.state}
              placeholder="e.g Florida" />
          </div>
          <p class="help">
            Any of the states in the U.S.A. like "Alabama", "Maine",
            "Tennessee", or even "Colorado".
          </p>
        </div>
        <div class="field mt-4">
          <label for="animal_transportation" class="label">Ask Dad for
            <span class="has-text-primary">a mode of transportation</span>.</label>
          <div class="control">
            <input
              id="animal_transportation"
              class="input"
              type="text"
              bind:value={storyInputs.transportation}
              placeholder="e.g Bus" />
          </div>
          <p class="help">
            Any way to get from one place to another like "Boat", "Plane", or
            even "Scooter".
          </p>
        </div>
        <div class="field mt-4">
          <label for="answer_number" class="label">Finally, pick
            <span class="has-text-primary">a number</span>
            between 10-20.</label>
          <div class="control">
            <input
              id="answer_number"
              class="input"
              type="number"
              bind:value={storyInputs.number}
              min="10"
              max="20" />
          </div>
        </div>
        {#if storyInputs.name && storyInputs.animal && storyInputs.number && storyInputs.transportation && storyInputs.state}
          <button
            class="button mt-4"
            transition:fade
            on:click|preventDefault={createStory}>Ready for the quest 🚀</button>
        {/if}
      </form>
    </div>
  {/if}
  {#if step === availableSteps.story}
    <Story {...storyInputs} />
  {/if}
</main>
