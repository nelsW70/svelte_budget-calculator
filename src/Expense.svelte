<script>
  // modules
  import { blur, slide, scale, fade, fly } from "svelte/transition";
  import { getContext } from "svelte";
  // variables
  export let id;
  export let name = "";
  export let amount = 0;
  let displayAmount = false;
  // functions
  function toggleAmount() {
    displayAmount = !displayAmount;
  }
  // context
  const removeExpense = getContext("remove");
  const setModifiedExpense = getContext("modify");
</script>

<article class="single-expense">
  <div class="expense-info">
    <h2>
      {name}
      <button on:click={toggleAmount} class="amount-btn">
        <i class="fas fa-caret-down" />
      </button>
    </h2>
    {#if displayAmount}
      <!-- <h4 transition:blur>amount: ${amount}</h4>
      <h4 transition:scale>amount: ${amount}</h4>
      <h4 transition:slide>amount: ${amount}</h4> -->
      <!-- <h4 transition:fade>amount: ${amount}</h4> -->
      <h4 transition:fly>amount: ${amount}</h4>
    {/if}
  </div>
  <div class="expense-buttons">
    <button
      class="expense-btn edit-btn"
      on:click={() => setModifiedExpense(id)}>
      <i class="fas fa-pen" />
    </button>
    <button on:click={() => removeExpense(id)} class="expense-btn delete-btn">
      <i class="fas fa-trash" />
    </button>
  </div>
</article>
