<script>
  import { cart, removeFromCart } from '$lib/stores/cart';
  import { get } from 'svelte/store';

  let cartItems = get(cart);

  $: cartItems = get(cart);
</script>

<nav>
    <a href="/">Home</a>
  </nav>
<section class="cart">
  <h2>Your Cart</h2>
  {#if cartItems.length === 0}
    <p>Your cart is empty.</p>
  {:else}
    <ul>
      {#each cartItems as item}
        <li>
          <img  alt={item.name} />
          <div>
            <h3>{item.name}</h3>
            <p>${item.price}</p>
            <button on:click={() => removeFromCart(item.id)}>Remove</button>
          </div>
        </li>
      {/each}
    </ul>
  {/if}
</section>

<style>
  .cart {
    padding: 2rem;
    text-align: center;
  }

  .cart ul {
    list-style: none;
    padding: 0;
  }

  .cart li {
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
  }

  .cart img {
    width: 100px;
    height: auto;
    margin-right: 1rem;
  }

  .cart button {
    background: #FF7043;
    color: white;
    padding: 0.5rem 1rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: 0.3s;
  }

  .cart button:hover {
    background: darken(#FF7043, 10%);
  }
</style>
