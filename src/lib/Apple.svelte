<script>
  import { appleSharePrice } from "./stores.js";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  const totalShares = 1000;

  let sharePrice = 100;
  appleSharePrice.set(sharePrice);

  let sharesPurchasedPending;

  function purchase() {
    const purchaseInfo = {
      sharePrice,
      sharesPurchasedPending,
    };
    dispatch("purchaseShares", purchaseInfo);
    sharesPurchasedPending = 0;
  }

  function handleEnter(event) {
    if (event.key === "Enter") {
      event.preventDefault();
    }
  }
  function updateSharePrice() {
    appleSharePrice.update(() => sharePrice);
  }
</script>

<div class="stock-cards">
  <h1>Apple</h1>
  <h2>AAPL</h2>
  <p>Total Shares: {totalShares}</p>
  <p>Price: ${sharePrice}</p>
  <form on:submit|preventDefault={purchase}>
    <label for="purchase">Purchase:</label>
    <input
      id="purchase"
      type="number"
      bind:value={sharesPurchasedPending}
      on:keydown={handleEnter}
    />
    <button>Purchase</button>
  </form>
</div>

<style>
  div {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>
