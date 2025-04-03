<script lang="ts">
  let maxDate = new Date(2025, 11, 31);
  let timeLeft = maxDate.getTime() - Date.now() ;
  let timeLeftString = parseMs(timeLeft);

  let updateTimeInterval = setInterval(updateTimer);

  if(timeLeft <= 0) {
    timeLeftString = parseMs(0);
    clearInterval(updateTimeInterval);
  }

  function updateTimer() {
    timeLeft = maxDate.getTime() - Date.now();
    timeLeftString = parseMs(timeLeft);
  }

  function addZero(number: number) {
    return number < 10 ? `0${number}` : number;
  }

  function parseMs(time: number) {
    let days = Math.floor(time / (24*60*60*1000));
    let hours = Math.floor((time % (24*60*60*1000)) / (60*60*1000));
    let minutes = Math.floor((time % (60*60*1000)) / (60*1000));
    let seconds = Math.floor((time % (60*1000)) / 1000);
    
    return `${days} days ${addZero(hours)}h ${addZero(minutes)}m ${addZero(seconds)}s`
  }
</script>

<div class="content">
  <div>
    <h2>Hollow Knight: Silksong <span style="white-space: nowrap;">will be out in at least</span></h2>
    <div class="divisor"></div>
    <h1>{timeLeftString}</h1>
  </div>
</div>

<style>
  .content {
    display: grid;
    place-items: center;
    min-height: 100vh;
    font-family: 'Roboto', 'sans-serif';
    background-color: rgba(0, 0, 0, 0.9);
  }

  .content div {
    text-align: center;
  }

  .divisor {
    height: 1px;
    background-color: white;
    opacity: 0.1;
    margin: 10px 0;
  }

  h1 {
    font-size: 4rem;
  }

  @media(max-width: 700px) {
    h1 {
      font-size: 3rem;
    }
    h2 {
      font-size: 1.5rem;
    }
  }

</style>
