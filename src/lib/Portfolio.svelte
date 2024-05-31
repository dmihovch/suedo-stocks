<script>
  import { appleSharePrice } from "./stores.js";
  import Apple from "./Apple.svelte";
  import PortStockCard from "./PortStockCard.svelte";
  let userName = "Placeholder";
  let wallet = 9999;

  let sharesAppl = 0;

  let stockNames = ["apple", "nvidia", "netflix", "google"];

  function handleBuyEvent(event) {
    let purchaseInfo = event.detail;
    let totalPrice =
      purchaseInfo.sharesPurchasedPending * purchaseInfo.sharePrice;
    if (totalPrice <= wallet) {
      wallet -= totalPrice;
      sharesAppl += purchaseInfo.sharesPurchasedPending;
    }
  }
</script>

<div class="portfolio-container">
  <h1>{userName}'s Portfolio</h1>
  <p>Wallet: ${wallet}</p>
  <PortStockCard name="Apple (AAPL)" sharePrice={$appleSharePrice} />
</div>

<!-- <Apple on:purchaseShares={handleBuyEvent} /> -->

<style>
  .portfolio-container {
    position: absolute;
    padding: 10px;
    height: fit-content;
    width: fit-content;
    background-color: rgba(5, 5, 5, 0.5);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
