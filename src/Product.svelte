<script>
  import Button from './Button.svelte';

  // specifying props that can be inputted to this component
  export let productTitle;
  export let productPrice;
  export let productDescription;
</script>


<div>
  <h1>{productTitle}</h1>
  <h2>{productPrice}</h2>
  <p>{productDescription}</p>
  <Button>Add To Cart</Button>
</div>

<!-- Svelte styles are automatically component scoped -->
<style>
  div {
    margin: 1rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
    padding: 1rem;
    border-radius: 5px;
    background-color: white;
  }

  h1 {
    font-size: 1.25rem;
    margin: 0.25rem 0;
  }

  h2 {
    font-size: 1rem;
    margin: 0.25rem 0;
    color: #4b4b4b;
  }

  p {
    margin: 0.25rem 0;
  }
</style>