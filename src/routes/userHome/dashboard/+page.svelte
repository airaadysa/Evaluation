<script>
	import Topbar from '$lib/components/common/Topbar.svelte';
	import Sidebar from '$lib/components/student/Sidebar.svelte';
	import { goto } from '$app/navigation'; // Use goto for internal navigation
	import './studDash.css';
  
	let userName = "Aira";
  
	function evaluateTeacher() {
	  goto('/userHome/evaluation'); // Use goto for routing
	}
  </script>
  
  <svelte:head>
	<title>Student Dashboard</title>
  </svelte:head>
  
  <Topbar />
  <Sidebar />
  
  <div class="dashboard-wrapper">
	<h1 class="greeting">Welcome back, {userName}! 👋</h1>
	
	<p class="quote">"Education is the most powerful weapon which you can use to change the world." - Nelson Mandela</p>
	
	<div class="evaluation-box">
	  <p>Evaluate your teacher for this semester</p>
	  <button on:click={evaluateTeacher} class="evaluate-button" aria-label="Start teacher evaluation">Start Evaluation</button>
	</div>
  </div>
  <style>
  .dashboard-wrapper {
	padding: 20px;
	font-family: Arial, sans-serif;
  }
  
  .greeting {
	font-size: 2rem;
	color: #333;
  }
  
  .quote {
	font-size: 1.2rem;
	color: #555;
	margin-top: 10px;
  }
  
  .evaluation-box {
	margin-top: 20px;
  }
  
  .evaluate-button {
	background-color: #007bff;
	color: white;
	border: none;
	border-radius: 5px;
	padding: 10px 20px;
	font-size: 1rem;
	cursor: pointer;
	transition: background-color 0.3s ease;
  }
  
  .evaluate-button:hover {
	background-color: #0056b3;
  }
</style>