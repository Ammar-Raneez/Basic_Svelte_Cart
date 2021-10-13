<script>
  export let items;

  // dynamic statements (labelled statement in JS)
  // whenever items changes, it re-renders this
  $: cartTotal = items.reduce((sum, currValue) => {
    return sum + currValue.price;
  }, 0);
</script>

{#if !items.length}
  <p>No Items In Cart Yet</p>
  {:else}
  <ul>
    {#each items as item}
      <li>{item.title} - ${item.price}</li>
    {/each}
  </ul>
{/if}

<h1>TOTAL: ${cartTotal}</h1>

<style>
  ul {
    list-style: none;
    margin: 1rem;
    padding: 0;
  }

  li {
    margin: 0.5rem 0;
    padding: 0.5rem;
    border: 1px solid #ccc;
  }

  h1 {
    font-size: 1.5rem;
    margin: 1rem;
  }
</style>