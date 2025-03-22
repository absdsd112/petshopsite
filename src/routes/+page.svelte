<script>
  

  let products = [
    { id: 1, name: 'Dog Food', price: 29.99, image: 'dog-food.jpg' },
    { id: 2, name: 'Cat Food', price: 24.99, image: 'cat-food.jpg' }
    // Add more products as needed
  ];

  let currentSection = 'home';
</script>



<nav>
    <a href="/">Home</a>
    <a href="/woof-shop">Woof Shop</a>
    <a href="/meow-shop">Meow Shop</a>
    <a href="/about">About Us</a>
    <a href="/cart">Cart</a>
</nav>

{#if currentSection === 'home'}
  <div class='home-banner'>
    <div class="banner-text">
      <div class="text-background">
        <h1>Love Starts with Fresh, Healthy Food</h1>
        <h1>And Grows with Every Moment Together...</h1>
      </div>
    </div>
  </div>

  <section class='why-choose-us'>
    <h2>The Reasons for Choosing Us</h2>
    <ul>
      <li>🥩 Meat as the #1 Ingredient</li>
      <li>🍖 Better Flavor for Pets</li>
      <li>🏭 Locally Produced</li>
      <li>🌱 Organic Products</li>
    </ul>
  </section>

  <section class='daily-menu'>
    <h2>Daily Menu for Dogs & Cats</h2>
    <div class='menu-container'>
      <div>
        <h3>Dogs</h3>
        <p>
          
          Senior 
          <img src="src\image 4@2x.png" alt="Logo" />
           
        </p>
        <p>
          Adult 
          <img src="src\image 4@2x.png" alt="Logo" />
        </p>
        <p>
          Puppy
          <img src="src\image 4@2x.png" alt="Logo" />
        </p>
      </div>
      <div>
        <h3>Cats</h3>
        <p>
        
          Senior 
          <img src="src\image 4@2x.png" alt="Logo" />
        </p>
          <p>
          Adult 
          <img src="src\image 4@2x.png" alt="Logo" />
        </p>
          <p>
          Kitten
          <img src="src\image 4@2x.png" alt="Logo" />
        </p>
      </div>
    </div>
  </section>
{/if}

{#if currentSection === 'woof-shop'}
  <section class="product-list">
    <h2>Woof Shop Products</h2>
    <div class="products">
      {#each products.filter(product => product.name.includes('Dog')) as product}
        <div class="product-card">
          <img src={product.image} alt={product.name} />
          <h3>{product.name}</h3>
          <p>${product.price}</p>
          
        </div>
      {/each}
    </div>
  </section>
{/if}

<!-- Add similar sections for 'meow-shop', 'pet-club', and 'about' -->





