<script>
	import Topbar from '$lib/components/Topbar.svelte'; // Importing the topbar
	import Sidebar from '$lib/components/student/Sidebar.svelte'; // Importing the sidebar
	import './studDash.css'
  
	let userName = "Aira"; 

	
	function evaluateTeacher() {
	  window.location.href= '/userHome/evaluation';
	}
  </script>
  
  <svelte:head>
	<title>Student Dashboard</title> <!-- Page title -->
  </svelte:head>
  
  <Topbar /> <!-- Include topbar -->
  <Sidebar /> <!-- Include sidebar -->
  
  <div class="dashboard-wrapper"> <!-- Dashboard wrapper for overall structure -->
	<h1 class="greeting">Welcome back, {userName}! 👋</h1> <!-- Warm greeting -->
	
	<p class="quote">"Education is the most powerful weapon which you can use to change the world." - Nelson Mandela</p> <!-- Inspirational quote -->
  
	<!-- Evaluation Box -->
	<div class="evaluation-box">
	  <p>Evaluate your teacher for this semester</p> <!-- Instructions -->
	  <button on:click={evaluateTeacher} class="evaluate-button">Start Evaluation</button> <!-- Call to action -->
	</div>
	
	
	
	
  </div>
  
  