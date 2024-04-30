<script>
  import './register.css'; // Custom CSS for the component

  // State variables for form fields
  let firstName = '';
  let lastName = '';
  let email = '';
  let password = '';

  /**
   * Handles form submission
   * @param {Event} event - The form submit event
   */
  const handleSubmit = (event) => {
      event.preventDefault(); // Prevent the default form submission

      // Basic validation
      if (!firstName || !lastName || !email || !password) {
          alert('All fields are required'); // Simple validation message
          return;
      }

      // Implement registration logic here
      console.log('User registered:', { firstName, lastName, email, password });
  };
</script>

<svelte:head>
  <title>Register - STAR Performance Evaluation</title> <!-- Page title -->
</svelte:head>

<!-- Main wrapper for the registration page -->
<div class="register-wrapper">
  <div class="register-box">
      <h1>Register</h1> <!-- Title for the form -->
      <form on:submit={handleSubmit}> <!-- Event handler for form submission -->
          <div class="form-group flex-row"> <!-- First name and last name input fields beside each other -->
              <div class="input-group">
                  <label for="first-name">First Name</label>
                  <input
                      type="text"
                      name="first-name"
                      id="first-name"
                      placeholder="First Name"
                      bind:value={firstName} 
                  />
              </div>
              <div class="input-group">
                  <label for="last-name">Last Name</label>
                  <input
                      type="text"
                      name="last-name"
                      id="last-name"
                      placeholder="Last Name"
                      bind:value={lastName}
                  />
              </div>
          </div>
          <div class="form-group"> <!-- Email input field -->
              <label for="email">Email Address</label>
              <input
                  type="email"
                  name="email"
                  id="email"
                  placeholder="Email"
                  bind:value={email}
              />
          </div>
          <div class="form-group"> <!-- Password input field -->
              <label for="password">Password</label>
              <input
                  type="password"
                  name="password"
                  id="password"
                  placeholder="Password"
                  bind:value={password}
              />
          </div>
          <button type="submit">Register</button> <!-- Submit button -->
      </form>

      <p> <!-- Link to the login page -->
          Already have an account? <a href="/userHome/login">Login</a>
      </p>
  </div>
</div>
