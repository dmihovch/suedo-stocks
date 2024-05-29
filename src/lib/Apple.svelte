<script>
  let shares = 1000;
  let sharePrice = 100;
</script>

<div class="stock-cards">
  <h1>Apple</h1>
  <h2>AAPL</h2>
  <p>Shares: {shares}</p>
  <p>Price: ${sharePrice}</p>
  <form>
    <label for="purchase">Purchase:</label>
    <input id="purchase" type="number" />
  </form>
</div>

<style>
  div {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>
