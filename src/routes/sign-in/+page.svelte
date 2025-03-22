<script>
    let username = '';
    let password = '';
  </script>
  
  <section class="login-page">
    <h2>Sign Up</h2>
    <form>
      <div>
        <label for="username">Username:</label>
        <input type="text" id="username" bind:value={username} />
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" bind:value={password} />
      </div>
      <div>
        <label for="password">Confirm Password:</label>
        <input type="password" id="password" bind:value={password} />
      </div>
      <button type="button" on:click="{() => alert('Login functionality not implemented yet')}">Login</button>
    </form>
  </section>
  