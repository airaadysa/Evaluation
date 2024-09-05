// @ts-nocheck
<script>
  import Topbar from "$lib/components/common/Topbar.svelte";
  import Sidebar from "$lib/components/admin/Sidebar.svelte";

  let numStudentsEvaluated = 120;
  let numTeachers = 20;
  let totalStudents = 500;

  // Reactive variables to store formatted numbers
  $: formattedTotalStudents = formatNumber(totalStudents);
  $: formattedNumStudentsEvaluated = formatNumber(numStudentsEvaluated);
 // @ts-nocheck
 function formatNumber(num) {
  return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}

  function drawCharts() {
    // Placeholder: replace with actual chart drawing code
    console.log("Charts drawn");
  }

  // Draw charts when the component is mounted
  import { onMount } from 'svelte';
  onMount(() => {
    drawCharts();
  });
</script>

<style>
  .container {
    max-width: 1000px;
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

<Topbar />
<Sidebar/>

<div class="container">
  <div class="card">
    <i class="icon fas fa-users" aria-hidden="true"></i>
    <h2 class="card-title">Students</h2>
    <div class="statistics">
      <div class="statistic">
        <p class="statistic-number">{formattedTotalStudents}</p>
        <p class="statistic-label">Total Students</p>
      </div>
      <div class="statistic">
        <p class="statistic-number">{formattedNumStudentsEvaluated}</p>
        <p class="statistic-label">Students Evaluated</p>
      </div>
    </div>
    <a href="/admin/manageStudents" class="button">Manage Students</a>
  </div>

  <div class="card">
    <i class="icon fas fa-chart-bar" aria-hidden="true"></i>
    <h2 class="card-title">Analytics</h2>
    <p class="card-content">View key statistics and insights about evaluations:</p>
    <canvas id="evaluationChart" width="200" height="200"></canvas>
  </div>

  <div class="card">
    <i class="icon fas fa-bell" aria-hidden="true"></i>
    <h2 class="card-title">Notifications</h2>
    <p class="card-content">View recent notifications and updates.</p>
    <a href="/admin/notifications" class="button">View Notifications</a>
  </div>

  <div class="card">
    <i class="icon fas fa-history" aria-hidden="true"></i>
    <h2 class="card-title">Recent Activity</h2>
    <p class="card-content">View recent activities and events.</p>
    <a href="/admin/recentActivity" class="button">View Activity Log</a>
  </div>

  <div class="card">
    <i class="icon fas fa-server" aria-hidden="true"></i>
    <h2 class="card-title">System Status</h2>
    <p class="card-content">Check the status of system components.</p>
    <a href="/admin/systemStatus" class="button">View System Status</a>
  </div>

  <div class="card">
    <i class="icon fas fa-cog" aria-hidden="true"></i>
    <h2 class="card-title">Settings</h2>
    <p class="card-content">Configure system settings and preferences.</p>
    <a href="/admin/settings" class="button">System Settings</a>
  </div>
</div>
