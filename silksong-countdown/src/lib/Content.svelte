<script>
  let maxDate = new Date(2023, 5, 12);
  let timeLeft = maxDate.getTime() - Date.now() 
  let timeLeftString = parseMs(timeLeft);

  setInterval(() => {
    timeLeft = maxDate.getTime() - Date.now() 
    timeLeftString = parseMs(timeLeft);
  })

  function parseMs(time) {
    let days = Math.floor(time / (24*60*60*1000));
    let daysms = time % (24*60*60*1000);
    let hours = Math.floor(daysms / (60*60*1000));
    let hoursms = time % (60*60*1000);
    let minutes = Math.floor(hoursms / (60*1000));
    let minutesms = time % (60*1000);
    let seconds = Math.floor(minutesms / 1000);
    return `${days} days ${hours}h ${minutes}m ${seconds}s`
  }
</script>

<div class="content">
  <div>
    <h2>Silksong is out in at least</h2>
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

  h1 {
    font-size: 4rem;
  }
</style>
