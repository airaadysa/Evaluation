<script>
  // Script to manage the profile dropdown visibility
  let showProfileDropdown = false;
  const toggleProfileDropdown = () => {
    showProfileDropdown = !showProfileDropdown;
  };
</script>

<style>
  /* Resetting default margins and padding */
html, body {
  margin: 0; /* Remove default margin */
  padding: 0; /* Remove default padding */
  box-sizing: border-box; /* Consistent box-sizing */
}

/* Styling for the top bar */
.top-bar {
  position: fixed;
  display: flex;
  justify-content: center; /* Center content */
  align-items: center; /* Align items vertically */
  width: 100vw; /* Full width of the viewport */
  height: 60px; /* Fixed height */
  background-color: #ffffff; /* White background */
  color: #004085; /* Blue text color */
  position: fixed; /* Fixed at the top */
  top: 0; /* Align to the top */
  left: 0; /* Start at the left edge */
  z-index: 10; /* Layer on top of other content */
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.4); /* Subtle shadow */
}

/* Profile section styling */
.profile-section {
  position: absolute; /* Positioned absolutely */
  right: 20px; /* Keep alignment to the right */
  cursor: pointer; /* Indicates it's clickable */
}

/* Profile dropdown styling */
.profile-dropdown {
  position: absolute;
  top: 60px; /* Positioned below the top bar */
  right: 20px; /* Align with the profile section */
  background: rgb(255, 255, 255);
  color: #1a1b1d; /* Matching sidebar color */
  padding: 10px; /* Padding inside the dropdown */
  border-radius: 8px; /* Rounded corners */
  box-shadow: 0px 6px 20px rgba(0, 0, 0, 0.3); /* Enhanced shadow */
  display: none; /* Hidden by default */
  transition: all 0.3s ease-in-out; /* Smooth transition */
}

/* Display profile dropdown when toggled */
.profile-dropdown.show {
  display: block; /* Show when the 'show' class is present */
}

/* Dropdown list and item styling */
.profile-dropdown ul {
  list-style: none;
  padding: 0; /* Remove default padding */
  margin: 0; /* Remove default margin */
}

.profile-dropdown li {
  padding: 10px; /* Padding for list items */
  transition: background 0.3s; /* Smooth background transition */
}

.profile-dropdown li a {
  color: #1e3a8a; /* Matching sidebar color */
  text-decoration: none; /* No underline */
}

.profile-dropdown li:hover {
  background: #f1f5f9; /* Light background on hover */
}

</style>

<div class="top-bar">
  <!-- Logo centered in the top bar -->
  <div>Logo</div>

  <!-- Profile icon triggers the dropdown, positioned to the far right -->
  <div class="profile-section" on:click={toggleProfileDropdown}>
    <img src="/path/to/profile-pic.jpg" alt="Profile Picture" width="30" height="30" />
  </div>

  <!-- Profile dropdown menu -->
  <div class={`profile-dropdown ${showProfileDropdown ? 'show' : ''}`}>
    <ul>
      <li><a href="/account-settings">Account Settings</a></li>
      <li><a href="/logout">Log Out</a></li>
    </ul>
  </div>
</div>
