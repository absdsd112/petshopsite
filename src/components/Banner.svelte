<style>
  .banner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #A67B5B;
    padding: 3rem;
  }

  .logo {
    width: 80px; /* Adjusted width */
    height: auto;
  }

  .search {
    font-family: 'Indie Flower';
    font-size: 20px;
    color: #000000;
    
    margin-left: 1rem;
    
    transform: translate(1100px,0px);
  }


  .buttons {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  .button {
    font-family: 'Indie Flower';
    font-size: 20px;
    color: #000000;
    cursor: pointer;
  }
</style>

<div class="banner">
  <img src="src\components\LOGO.svg" alt="Logo" class="logo" />
  <input type="text" placeholder="Search" class="search" />
  <div class="buttons">
    <div class="button" on:click="{() => window.location.href = '/log-in'}">Log In</div>
    <div class="button" on:click="{() => window.location.href = '/sign-in'}">Sign Up</div>
    <div class="button">Cart</div>
  </div>
</div>