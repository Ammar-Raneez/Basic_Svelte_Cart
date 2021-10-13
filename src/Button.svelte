<!-- by not specifying the listener, it forwards the responsibility to the parent component -->
<button on:click>
  <!-- this is a placeholder tag, which will take any text that we place instead -->
  <slot />
</button>

<style>
  button {
    font: inherit;
    padding: 0.15rem 0.5rem;
    background-color: #d10057;
    border: 1px solid #d10057;
    color: white;
  }

  button:hover,
  button:active {
    box-shadow: 1px 1px 6px rgba(0, 0, 0, 0.25);
  }
</style>