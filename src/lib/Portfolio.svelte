<script>
  import { appleSharePrice } from "./stores.js";
  import Apple from "./Apple.svelte";
  let userName = "Placeholder";
  let wallet = 9999;

  let sharesAppl = 0;

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
  <h2 class="portfolio-subcontainer">
    Apple (AAPL):
    <p>Shares: {sharesAppl}</p>
    <p>Unit Price: {$appleSharePrice}</p>
    <p>Total Value: {sharesAppl * $appleSharePrice}</p>
  </h2>
</div>

<Apple on:purchaseShares={handleBuyEvent} />

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
  .portfolio-subcontainer {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
</style>
