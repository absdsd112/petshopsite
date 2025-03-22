<script>
  
 

  let products = [
    { id: 1, name: 'Premium Dog Food', price: 39.99, image: 'premium-dog-food.jpg' },
    { id: 2, name: 'Organic Dog Treats', price: 19.99, image: 'organic-dog-treats.jpg' }
    // Add more products as needed
  ];
</script>

<nav>
    <a href="/">Home</a>
  </nav>

<h1>Woof Shop</h1>

<section class="product-list">
  <h2>Products for Dogs</h2>
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
