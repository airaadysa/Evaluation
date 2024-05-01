<script>
  let adminSidebarVisible = false;

  const toggleAdminSidebar = () => {
    adminSidebarVisible = !adminSidebarVisible;
  };
</script>
<style>
  .sidebar {
    position: fixed;
    top: 60px;
    left: 0;
    height: calc(100% - 60px);
    width: 260px;
    background: #0050ac;
    color: #ffffff;
    padding: 15px;
    transition: transform 0.5s ease;
    transform: translateX(-300px);
    z-index: 100;
  }
  
  .sidebar.visible {
    transform: translateX(0);
  }
  
  .hamburger-container {
    position: fixed;
    top: 9px;
    left: 20px;
    z-index: 100;
    cursor: pointer;
    padding: 12px;
    background: rgb(255, 255, 255);
    border-radius: 50%;
  }
  
  .hamburger-container.white {
    background: #01418a;
  }
  
  .hamburger {
    position: relative;
    width: 20px;
    height: 17px;
    display: inline-block;
  }
  
  .hamburger span {
    display: block;
    width: 20px;
    height: 2px;
    background: #0c3762;
    margin-bottom: 6px;
    transition: background 0.3s ease;
  }
  
  .hamburger span:last-child {
    margin-bottom: 0;
  }
  
  .hamburger-container.white .hamburger span {
    background: #f8fafc;
  }
  
  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  li {
    background: #01418a;
    margin: 20px 4px;
    padding: 6px;
    padding-left: 15px;
    border-radius: 5px;
    transition: all 0.3s ease;
    border: 2px solid transparent;
  }
  
  li:hover {
    border: 2px solid #f59e0b;
  }
  
  a {
    color: inherit;
    text-decoration: none;
    display: flex;
    align-items: center;
  }
  
  .icon {
    margin-right: 8px;
  }
  </style>

<div>
  <div
    class={`hamburger-container ${adminSidebarVisible ? 'white' : ''}`}
    on:click="{toggleAdminSidebar}"
  >
    <div class="hamburger">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>

  <div class={`sidebar ${adminSidebarVisible ? 'visible' : ''}`}>
    <ul>
      <li>
        <a href="/admin/home">
          <span class="icon">🏠</span> Dashboard
        </a>
      </li>
      <li>
        <a href="/admin/faculty">
          <span class="icon">👨‍🏫</span> Faculty Management
        </a>
      </li>
      <li>
        <a href="/admin/evaluation">
          <span class="icon">📝</span> Evaluation Management
        </a>
      </li>
      <li>
        <a href="/admin/reports">
          <span class="icon">📊</span> Reports
        </a>
      </li>
    </ul>
  </div>
</div>
