


<script>
  let username = '';
  let email = '';
  let password = '';
  let confirmPassword = '';
  let error = '';

  function register() {
    if (password !== confirmPassword) {
      error = "Passwords don't match!";
      return;
    }
    // You can add your registration logic here, like sending a request to your backend
    console.log('Registering user:', { username, email, password });

    // After successful registration, you can redirect the user to another page
    // window.location.href = '/dashboard'; // Example redirection
  }

  
</script>

<main>
    <div class="container">
        <img src="fortuna.png" alt="Fortuna" class="logo">
    </div>
    
    <div class="container2">
        <h2>You need an account to access the website</h2>
        <button><a href="/register" style="text-decoration: none; color: #fff;">Register</a></button>
    </div>
    <div class="register" style="display: none;">
        <form on:submit|preventDefault={register}>
            <div>
                <label for="username">Username:</label>
                <input type="text" id="username" bind:value={username} required />
            </div>
            <div>
                <label for="email">Email:</label>
                <input type="email" id="email" bind:value={email} required />
            </div>
            <div>
                <label for="password">Password:</label>
                <input type="password" id="password" bind:value={password} required />
            </div>
            <div>
                <label for="confirmPassword">Confirm Password:</label>
                <input type="password" id="confirmPassword" bind:value={confirmPassword} required />
            </div>
            {#if error}
              <div style="color: red;">{error}</div>
            {/if}
            <button type="submit">Register</button>
        </form>
    </div>
</main>

<style>
    main {
        margin-top: 5vh;
    }

    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100vw;
    }

    .container2 {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
        position: relative;
    }

    .register {
        display: flex;
        flex-direction: column; 
        justify-content: center;
        align-self: center;
        font-style: oblique;
        font-size: large;
        border-style: solid;
        border-color: #00ffb7; 
        border-width: 1px;
        padding: 20px;  
        max-width: 250px; 

    }



    button {
        padding: 10px 20px;
        font-size: larger;
        font-style: oblique;
        background-color: rgba(66, 66, 66, 0);
        border-style: solid;
        border-color: #00ffb7;
        border-width: 1px;
        border-radius: 5px;
        color: rgb(255, 255, 255);
        text-align: center;
        text-decoration: none;
        display: inline-block;
        margin: 4px 2px;
        cursor: pointer;
        width: 150px;
        height: 70px;
        margin-left: 26px;
        display: none;
    }
    
    button:hover {
        background-color: rgba(66, 66, 66, 0.2)
    }

    h2 {
        display: none;
    }
</style>
