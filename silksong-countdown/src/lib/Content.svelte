<script>
  let maxDate = new Date(2023, 5, 12);
  let timeLeft = maxDate.getTime() - Date.now() 
  let timeLeftString = parseMs(timeLeft);

  let updateTimeInterval = setInterval(updateTimer);

  if(timeLeft <= 0) {
    clearInterval(updateTimeInterval);
  }

  function updateTimer() {
    timeLeft = maxDate.getTime() - Date.now() 
    timeLeftString = parseMs(timeLeft);
  }

  function parseMs(time) {
    let days = Math.floor(time / (24*60*60*1000));
    let daysms = time % (24*60*60*1000);
    let hours = Math.floor(daysms / (60*60*1000));
    let hoursms = time % (60*60*1000);
    let minutes = Math.floor(hoursms / (60*1000));
    let minutesms = time % (60*1000);
    let seconds = Math.floor(minutesms / 1000);
    
    return `${days} days ${hours}h\xa0${minutes}m\xa0${seconds}s`
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
