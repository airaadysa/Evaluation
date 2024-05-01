<script>
    import './login.css';
	import Sidebar from '$lib/components/student/Topbar.svelte';
	import Topbar from '$lib/components/student/Topbar.svelte';

  </script>
  <Topbar/>
	
  
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
        <button type="submit">Login</button>
      </form>
      <p>
        Don't have an account yet? <a href="/userHome/register">Sign up</a>
      </p>
    </div>
  </div>
  