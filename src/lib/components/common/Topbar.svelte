<!-- src/lib/components/common/Topbar.svelte -->
<script>
  let showProfileDropdown = false;
  const toggleProfileDropdown = () => {
    showProfileDropdown = !showProfileDropdown;
  };
</script>

<div class="top-bar">
  <div>Logo</div>
  <div class="profile-section" on:click="{toggleProfileDropdown}" aria-haspopup="true" aria-expanded={showProfileDropdown}>
    <img src="/path/to/profile-pic.jpg" alt="Profile Picture" width="30" height="30" />
  </div>
  <div class={`profile-dropdown ${showProfileDropdown ? 'show' : ''}`} role="menu">
    <ul>
      <li><a href="/account-settings">Account Settings</a></li>
      <li><a href="/logout">Log Out</a></li>
    </ul>
  </div>
</div>

<style>
  html, body {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .top-bar {
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    height: 60px;
    background-color: #ffffff;
    color: #004085;
    top: 0;
    left: 0;
    z-index: 10;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.4);
  }

  .profile-section {
    position: absolute;
    right: 20px;
    cursor: pointer;
  }

  .profile-dropdown {
    position: absolute;
    top: 60px;
    right: 20px;
    background: rgb(255, 255, 255);
    color: #1a1b1d;
    padding: 10px;
    border-radius: 8px;
    box-shadow: 0px 6px 20px rgba(0, 0, 0, 0.3);
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s ease-in-out, visibility 0.3s ease-in-out;
  }

  .profile-dropdown.show {
    opacity: 1;
    visibility: visible;
  }

  .profile-dropdown ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .profile-dropdown li {
    padding: 10px;
    transition: background 0.3s;
  }

  .profile-dropdown li a {
    color: #1e3a8a;
    text-decoration: none;
  }

  .profile-dropdown li:hover {
    background: #f1f5f9;
  }
</style>
