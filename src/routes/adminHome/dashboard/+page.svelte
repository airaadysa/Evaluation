<script>
    import Topbar from "$lib/components/Topbar.svelte";
    import Sidebar from "$lib/components/admin/Sidebar.svelte";
    // Sample data for analytics (replace this with your actual data)
    let numStudentsEvaluated = 120;
    let numTeachers = 20;
    let totalStudents = 500;
  
    // Function to format large numbers with commas
    function formatNumber(num) {
      return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    }
  
    // Function to draw the charts (using a simple placeholder chart for demonstration)
    function drawCharts() {
      // Replace this with your actual chart drawing code (e.g., using libraries like Chart.js or D3.js)
      console.log("Charts drawn");
    }
  </script>
  
  <style>
    /* Styles for the Topbar component */
    /* Add your styles for the Topbar component here */
  
    .container {
      max-width: 800px;
      margin: 20px auto;
      padding: 20px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      grid-gap: 20px;
    }
  
    .card {
      background-color: #fff;
      border-radius: 10px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      transition: box-shadow 0.3s ease;
    }
  
    .card:hover {
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
    }
  
    .card-title {
      font-size: 1.5rem;
      font-weight: bold;
      margin-bottom: 10px;
      color: #333;
    }
  
    .card-content {
      color: #555;
      text-align: center;
    }
  
    .button {
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      padding: 10px 20px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
      text-decoration: none;
      display: inline-block;
      margin-top: auto;
    }
  
    .button:hover {
      background-color: #0056b3;
    }
  
    .icon {
      font-size: 3rem;
      margin-bottom: 10px;
    }
  
    .statistics {
      display: flex;
      justify-content: space-around;
      margin-top: auto;
    }
  
    .statistic {
      text-align: center;
      padding: 10px 0;
    }
  
    .statistic-number {
      font-size: 1.5rem;
      font-weight: bold;
      color: #333;
    }
  
    .statistic-label {
      color: #555;
    }
  </style>
  
  <!-- Topbar component -->
  <Topbar />
  <Sidebar/>
  
  <div class="container">
    <div class="card">
      <i class="icon fas fa-users"></i>
      <h2 class="card-title">Students</h2>
      <div class="statistics">
        <div class="statistic">
          <p class="statistic-number">{formatNumber(totalStudents)}</p>
          <p class="statistic-label">Total Students</p>
        </div>
        <div class="statistic">
          <p class="statistic-number">{formatNumber(numStudentsEvaluated)}</p>
          <p class="statistic-label">Students Evaluated</p>
        </div>
      </div>
      <a href="/admin/manageStudents" class="button">Manage Students</a>
    </div>
  
    <div class="card">
      <i class="icon fas fa-chart-bar"></i>
      <h2 class="card-title">Analytics</h2>
      <p class="card-content">View key statistics and insights about evaluations:</p>
      <!-- Placeholder for chart -->
      <canvas id="evaluationChart" width="200" height="200"></canvas>
    </div>
  
    <div class="card">
      <i class="icon fas fa-bell"></i>
      <h2 class="card-title">Notifications</h2>
      <p class="card-content">View recent notifications and updates.</p>
      <a href="/admin/notifications" class="button">View Notifications</a>
    </div>
  
    <div class="card">
      <i class="icon fas fa-history"></i>
      <h2 class="card-title">Recent Activity</h2>
      <p class="card-content">View recent activities and events.</p>
      <a href="/admin/recentActivity" class="button">View Activity Log</a>
    </div>
  
    <div class="card">
      <i class="icon fas fa-server"></i>
      <h2 class="card-title">System Status</h2>
      <p class="card-content">Check the status of system components.</p>
      <a href="/admin/systemStatus" class="button">View System Status</a>
    </div>
  
    <div class="card">
      <i class="icon fas fa-cog"></i>
      <h2 class="card-title">Settings</h2>
      <p class="card-content">Configure system settings and preferences.</p>
      <a href="/admin/settings" class="button">System Settings</a>
    </div>
  </div>
  
 
  