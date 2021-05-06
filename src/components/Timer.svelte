<script>
  import ProgressBar from "./ProgressBar.svelte";
  import { createEventDispatcher } from "svelte";
  const totalSeconds = 3;
  let secondLeft = totalSeconds;
  let isRunning = false;

  const dispatch = createEventDispatcher();

  $: progress = ((totalSeconds - secondLeft) / totalSeconds) * 100;

  function myTimer() {
    isRunning = true;
    let timer = setInterval(() => {
      secondLeft -= 1;
      if (secondLeft == 0) {
        clearInterval(timer);
        isRunning = false;
        secondLeft = totalSeconds;
        dispatch("end", "end timer");
      }
    }, 1000);
  }

  // function myTimer() {
  //   while (secondLeft > 0) {
  //     setTimeout(() => {
  //       return (secondLeft -= 1);
  //     }, 100);
  //   }
  // }
</script>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondLeft}</h2>
</div>
<ProgressBar {progress} />
<div bp="grid">
  <div bp="offset-5@md 4@md 12@sm">
    <button disabled={isRunning} class="start" on:click={myTimer}>Start</button>
  </div>
</div>

<style>
  h2 {
    margin: 0;
    text-align: center;
  }

  .start {
    border-radius: 5%;
    width: 100%;
    box-shadow: 0px;
    margin-bottom: 10px;
    border: none;
  }
  .start[disabled] {
    background-color: rgb(194, 194, 194);
    cursor: not-allowed;
  }
</style>
