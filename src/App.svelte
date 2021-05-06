<script>
  import HowTo from "./components/HowTo.svelte";
  import Timer from "./components/Timer.svelte";
  export let audio;

  function timerEnd(e) {
    audio.play();
  }
</script>

<h1>Hand Washing App</h1>
<Timer on:end={timerEnd} />
<HowTo />

<footer>
  <h5>
    &copy; <a href="https://yarnwebdesign-ninjas.com">Ninjatech design</a> ||
    <a href="https://www.who.int/gpsc/clean_hands_protection/en/">
      Picture Sources</a
    >
    -
    <a href="https://freesound.org/people/metrostock99/sounds/345086"
      >Sound Source</a
    >
  </h5>
</footer>

<!-- svelte-ignore a11y-media-has-caption -->
<audio bind:this={audio}>
  <source src="sound.wav" />
</audio>

<style>
  h1 {
    text-align: center;
    color: rgb(63, 182, 237);
  }

  footer {
    text-align: center;
  }
</style>
