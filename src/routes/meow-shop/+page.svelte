<script>
 


  let products = [
    { id: 4, name: 'Dry Cat Food', price: 27.99, image: 'dry-cat-food.jpg' },
    { id: 5, name: 'Wet Cat Food', price: 22.99, image: 'wet-cat-food.jpg' },
    { id: 6, name: 'Cat Treats', price: 8.99, image: 'cat-treats.jpg' }
    // Add more products as needed
  ];
</script>



<nav>
  <a href="/">Home</a>
</nav>
<h1>Meow Shop</h1>
<section class="product-list">
  <h2>Products for Cats</h2>
  <div class="products">
    {#each products as product}
      <div class="product-card">
        <img src={product.image} alt={product.name} />
        <h3>{product.name}</h3>
        <p>${product.price}</p>
       
      </div>
    {/each}
  </div>
</section>
