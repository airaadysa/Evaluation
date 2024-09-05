<script>
    import './login.css';
	import Sidebar from '$lib/components/common/Topbar.svelte';
	import Topbar from '$lib/components/common/Topbar.svelte';

  </script>
  
	
  
  <svelte:head>
    <title>STAR Performance Evaluation - Login</title>
  </svelte:head>
  
  <div class="login-wrapper">
    <div class="login-box">
      <h1>Login</h1>
      <form action="" method="post">
        <div class="form-group">
          <label for="email">Email Address</label>
          <input type="email" name="email" id="email" placeholder="Email" />
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input type="password" name="password" id="password" placeholder="Password" />
        </div>
        <a href="/userHome/dashboard">
        <button type="submit">Login</button>
        </a>
      </form>
      <p>
        Don't have an account yet? <a href="/studentAuth/register">Sign up</a>
      </p>
    </div>
  </div>
  