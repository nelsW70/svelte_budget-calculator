<script>
  // modules
  import { getContext } from "svelte";
  import { blur, slide, scale, fade, fly } from "svelte/transition";
  import { quintOut } from "svelte/easing";
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
      <!-- basic options -->
      <!-- <h4 transition:blur>amount: ${amount}</h4>
        <h4 transition:scale>amount: ${amount}</h4>
        <h4 transition:slide>amount: ${amount}</h4> -->
      <!-- <h4 transition:fade>amount: ${amount}</h4> -->
      <!-- <h4
          in:fly={{ x: -20, y: -20, duration: 500, delay: 500, easing: quintOut }}
          out:slide>
          amount: ${amount}
        </h4> -->
      <!-- basic options -->
      <h4 transition:slide>amount: ${amount}</h4>
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
