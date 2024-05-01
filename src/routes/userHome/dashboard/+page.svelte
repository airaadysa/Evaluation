<script>
	import Topbar from '$lib/components/Topbar.svelte';
	import Sidebar from '$lib/components/student/Sidebar.svelte';
	import './studDash.css';
  
	let userName = "Aira";
	
	function evaluateTeacher() {
	  window.location.href = '/userHome/evaluation';
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
	  <button on:click={evaluateTeacher} class="evaluate-button">Start Evaluation</button>
	</div>
</div>
