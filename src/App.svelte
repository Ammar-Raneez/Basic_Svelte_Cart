<script>
	import Product from './Product.svelte';
	import Button from './Button.svelte';
	import Cart from './Cart.svelte';

	let title = '';
	let price = 0;
	let description = '';
	let products = [];
	let cartItems = [];

	function createProduct() {
		const newProduct = {
			title,
			price,
			description,
		};

		// just pushing will not update the DOM
		// svelte listens to direct changes of the values assigned to variables
		// (any change in strings/numbers work therefore)
		// Since an array doesn't actually get reassigned a new array on-push
		// it doesn'nt update the DOM
		products = products.concat(newProduct);
	}

	function setTitle(e) {
		title = e.target.value;
	}

	function addToCart(event) {
		// console.log(event);
		const selectedTitle = event.detail;
		cartItems = cartItems.concat(
			// avoid any mutations
			{ ...products.find((prod) => prod.title === selectedTitle) }
		);

		// console.log(cartItems);
	}
</script>

<section>
	<Cart items={cartItems} />
</section>

<hr />

<section>
	<div>
		<label for="title">Title</label>
		<!-- regular listening to input to changing -->
		<input
			type="text"
			id="title"
			value={title}
			on:input={setTitle}
		/>
	</div>
	<div>
		<label for="price">Price</label>
		<!-- shortcut by svelte, for direct two-way binding (like [(ngModel)]) -->
		<input
			type="number"
			id="price"
			bind:value={price}
		/>
	</div>
	<div>
		<label for="description">Description</label>
		<textarea
			rows="3"
			id="description"
			bind:value={description}
		/>
	</div>
	<Button on:click={createProduct}>Add Product</Button>
</section>

<section>
	<!-- special block syntax -->
	{#if !products.length}
	<p>No Products were added yet</p>
	{:else}
	<!-- loop thru the products array -->
	{#each products as product}
		<Product
			productTitle={product.title}
			productPrice={product.price}
			productDescription={product.description}
			on:addCart={addToCart}
		/>
	{/each}
	{/if}
</section>

<style>
	section {
		width: 30rem;
		margin: auto;
	}

	label,
	input,
	textarea {
		width: 100%;
		outline: none;
	}
</style>