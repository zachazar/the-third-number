<script>
  import { fade } from "svelte/transition";

  export let name = "Zach";
  export let animal = "Monkey";
  export let number = 12;
  export let transportation = "Lebaron";
  export let state = "NM";
</script>

<style>
  section {
    text-align: left;
  }
  p {
    font-size: 2em;
    text-indent: 2em;
  }
  .the-third-number {
    color: gold;
  }
  .answer {
    color: #00d1b2;
  }
</style>

<section in:fade={{ delay: 2000 }}>
  <p>
    There once was a <span class="answer">{animal}</span> named <span
      class="answer">{name}</span>. He was on a quest to seek <span
      class="the-third-number">the third number</span>. he searched all around
    for it. From the hills of France to the islands of Greece, to the mountains
    of Canada, <span class="answer">{name}</span> searched everywhere but couldn't
    find <span class="the-third-number">the third number</span>
  </p>
</section>
