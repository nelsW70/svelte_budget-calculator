<script>
  import Title from "./Title.svelte";
  // variables
  let name = "";
  let amount = null;
  // reactive
  // $: console.log({ name, amount });
  $: isEmpty = !name || !amount;
  // functions
  function handleSubmit(e) {
    console.log({ name, amount });
    name = "";
    amount = null;
  }
</script>

<section class="form">
  <Title title="add expense" />
  <form class="expense-form" on:submit|preventDefault={handleSubmit}>
    <div class="form-control">
      <label for="name">name</label>
      <input type="text" id="name" bind:value={name} />
    </div>
    <div class="form-control">
      <label for="amount">amount</label>
      <input type="number" id="amount" bind:value={amount} />
    </div>
    {#if isEmpty}
      <p class="form-empty">please fill out all form fields</p>
    {/if}
    <button
      type="submit"
      class="btn btn-block"
      disabled={isEmpty}
      class:disabled={isEmpty}>
      add expense
    </button>
    <button type="button" class="close-btn">
      <i class="fas fa-times" />
      close
    </button>
  </form>
</section>
