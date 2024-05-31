<script>
  import { appleSharePrice } from "./stores.js";

  export let name = "default";
  export let sharePrice = 0;
  let sharesOwned = 0;
  let boughtPrice = 0;
</script>

<div class="portfolio-subcontainer">
  <h2>{name}</h2>
  <p>Shares: {sharesOwned}</p>
  <p>Unit Price: ${sharePrice}</p>
  <p>Total Value: ${sharesOwned * sharePrice}</p>
  <p>Bought At: ${boughtPrice} / Share</p>
</div>

<style>
  .portfolio-subcontainer {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
</style>
