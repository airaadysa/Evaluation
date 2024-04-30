<script>
  let sidebarVisible = false;

  const toggleSidebar = () => {
    sidebarVisible = !sidebarVisible;
  };
</script>

<style>
  /* Sidebar styling */
  .sidebar {
    position: fixed;
    top: 60px; /* Start below the top bar */
    left: 0;
    height: calc(100% - 60px);
    width: 260px;
    background:#0050ac;
    color: #ffffff;
    padding: 15px;
    transition: transform 0.5s ease;
    transform: translateX(-300px); /* Sidebar hidden initially */
    z-index: 100; /* Below the top bar */
  }

  /* Sidebar visible state */
  .sidebar.visible {
    transform: translateX(0); /* Sidebar slides in */
  }

  /* Hamburger styling */
  .hamburger-container {
    position: fixed;
    top: 9px; /* Adjusted for better visibility */
    left: 20px;
    z-index: 100; /* Above the sidebar and the top bar */
    cursor: pointer;
    padding: 12px; /* Padding for the clickable area */
    background: rgb(255, 255, 255); /* Default background */
    border-radius: 50%; /* Circular shape */
  }

  .hamburger-container.white {
    background: #01418a; /* Dark blue when sidebar is visible */
  }

  .hamburger {
    position: relative;
    width: 20px; /* Width of the hamburger */
    height: 17px; /* Total height for 3 lines */
    display: inline-block;
  }

  .hamburger span {
    display: block; /* Ensure block display for visibility */
    width: 20px; /* Width of each line */
    height: 2px; /* Height of each line */
    background: #0c3762; /* Default line color */
    margin-bottom: 6px; /* Margin between lines */
    transition: background 0.3s ease; /* Transition for line color */
  }

  .hamburger span:last-child {
    margin-bottom: 0; /* No extra space after the last line */
  }

  .hamburger-container.white .hamburger span {
    background: #f8fafc; /* White lines when sidebar is visible */
  }

  /* Sidebar item styling */
  /* Sidebar item styling */
  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  li {
    background: #01418a;
    margin: 20px 4px; /* Reduced margin */
    padding: 6px; /* Reduced padding */
    padding-left: 15px; /* Reduced padding on the left */
    border-radius: 5px; /* Border-radius for softer edges */
    transition: all 0.3s ease;
    border: 2px solid transparent; /* Transparent border to maintain layout */
  }

  a {
    color: inherit;
    text-decoration: none;
    display: flex;
    align-items: center;
  }

  /* Border effect on hover */
  li:hover {
    border: 2px solid #f59e0b; /* Border on all sides when hovering */
  }

  /* Icon styles */
  .icon {
    margin-right: 8px; /* Reduced margin between icon and text */
  }

</style>

<div>
  <div
    class={`hamburger-container ${sidebarVisible ? 'white' : ''}`}
    on:click={toggleSidebar}
  >
    <div class="hamburger">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>

  <div class={`sidebar ${sidebarVisible ? 'visible' : ''}`}>
    <ul>
      <li>
        <a href="/home">
          <span class="icon">🏠</span> Home
        </a>
      </li>
      <li>
        <a href="/evaluation">
          <span class="icon">📝</span> Evaluation
        </a>
      </li>
      <li>
        <a href="/reports">
          <span class="icon">📊</span> Reports
        </a>
      </li>
      <li>
        <a href="/settings">
          <span class="icon">⚙️</span> Settings
        </a>
      </li>
    
      <li>
        <a href="/contact">
          <span class="icon">📞</span> Contact
        </a>
      </li>
    </ul>
  </div>
</div>
