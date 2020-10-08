<script>
  import { fade } from "svelte/transition";

  export let name = "Rooney";
  export let animal = "Monkey";
  export let number = 12;
  export let transportation = "Lebaron";
  export let state = "New Mexico";

  function randomSmallNumber() {
    return (Math.floor(Math.random() * 10) % 7) + 2;
  }
  const moneyFromParents = randomSmallNumber();
  const moneyFromCAndZ = randomSmallNumber();
  const moneyForWater = randomSmallNumber();

  const moneyLeftOver =
    number + moneyFromParents + moneyFromCAndZ - moneyForWater;

  let moneyLeftOverAnswer = "";
  let answeredCorrectly = false;
  let displayError = false;
  function submitAnswer() {
    if (moneyLeftOverAnswer == moneyLeftOver) {
      answeredCorrectly = true;
    } else {
      displayError = true;
    }
  }
</script>

<style>
  section {
    text-align: left;
  }
  p {
    font-size: 2em;
    text-indent: 2em;
    margin-bottom: 0.25em;
  }
  .answer {
    color: #00d1b2;
  }
  .money-added {
    color: #00a100;
  }
  .money-removed {
    color: red;
  }
  .wrong-text {
    color: #f14668;
    font-size: 0.75em;
  }
</style>

<section in:fade={{ delay: 2000 }}>
  <p>
    Emryk was searching everywhere for the third number to unlock the treasure
    chest. Recently, he heard of a
    <span class="answer">{animal}</span>
    named
    <span class="answer">{name}</span>
    who told everyone that they knew the third number.
    <span class="answer">{name}</span>
    announced that they would share the third number in exchange for gold coins.
  </p>
  <p>
    Emryk wanted to meet
    <span class="answer">{name}</span>
    but
    <span class="answer">{name}</span>
    lived in
    <span class="answer">{state}</span>. So Emryk asked Asher if he could borrow
    his
    <span class="answer">{transportation}</span>
    to get there. Asher happily agreed to help and let Emryk borrow his
    <span class="answer">{transportation}</span>. Before he left, Mom and Dad
    packed him some food, water, and gave him
    <span class="money-added">{moneyFromParents}</span>
    more coins. Emryk had already saved
    <span class="answer">{number}</span>
    gold coins himself.
  </p>
  <p>
    Emryk had a long way to get to
    <span class="answer">{state}</span>. First, he had to trek though a deep
    jungle. Luckily while he was there, he came across Nana and Pops who gave
    him food and bug spray. Next, he used his
    <span class="answer">{transportation}</span>
    to cross the cold ice fields. Along the way, he saw Auntie Cole and Uncle
    Zach who gave him a blanket and
    <span class="money-added">{moneyFromCAndZ}</span>
    gold coins. After the ice fields, he had to cross a dry desert. He ran out
    of water, so he had to spend
    <span class="money-removed">{moneyForWater}</span>
    gold coins for more water.
  </p>
  <p>
    Emryk finally reached
    <span class="answer">{state}</span>
    and went to see
    <span class="answer">{name}</span>
    in
    <span class="answer">{animal}</span>
    Town.
  </p>
  <p>
    <strong><span class="answer">{name}</span></strong>
    said: "Hello Emryk. I’ve heard that you seek the third number. How many gold
    coins have you brought me in exchange?"
  </p>
  <p>
    <strong>Emryk</strong>
    said:
    {#if answeredCorrectly}
      "{moneyLeftOverAnswer}
      gold coins."
    {:else}
      <input
        class:is-danger={displayError === true}
        type="number"
        min="0"
        max="50"
        bind:value={moneyLeftOverAnswer} /><button
        on:click={submitAnswer}>Speak</button>
      {#if displayError}
        <span class="wrong-text">Hmmm I don't think that's right</span>
      {/if}
    {/if}
  </p>
  {#if answeredCorrectly}
    <p>
      <strong><span class="answer">{name}</span></strong>
      said: "You're right 🎉! The third number is
      <strong>3</strong>."
    </p>
  {/if}
</section>
