<script>
    import Sidebar from "$lib/components/student/Sidebar.svelte";
    import Topbar from "$lib/components/Topbar.svelte";
    let teacher = ['Teacher 1', 'Teacher 2', 'Teacher 3'];
    let courses = ['Subject 1', 'Subject 2', 'Subject 3'];
    let departments = ['Department 1', 'Department 2', 'Department 3'];
  
    let selectedTeacher= '';
    let selectedCourse = '';
    let selectedDepartment = '';
  
    function startEvaluation() {
     
      const evaluationURL = `/evaluation?person=${selectedTeacher}&course=${selectedCourse}&department=${selectedDepartment}`;
      window.location.href = '/userHome/evaluationForm';
    }
  </script>
  
  <style>
    .container {
      max-width: 500px;
      margin: 0 auto;
      padding: 20px;
      margin-top: 80px;
    
      border-radius: 10px;
      background-color: #ffffff;
      box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
    }
   
        
  
    h2 {
      margin-top: 0;
      margin-bottom: 20px;
      text-align: center;
      color: #333;
    }
  
    label {
      font-weight: bold;
      color: #555;
      display: block;
      margin-bottom: 5px;
    }
  
    select {
      width: 100%;
      padding: 12px;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-sizing: border-box;
      background-color: #f9f9f9;
      color: #333;
      margin-bottom: 15px;
    }
  
    button {
      width: 100%;
      padding: 12px;
      font-size: 1rem;
      border: none;
      border-radius: 5px;
      background-color: #007bff;
      color: white;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
  
    button:hover {
      background-color: #0056b3;
    }
  </style>
  <Sidebar/>
  <Topbar/>
  

  
  
    <div class="container">
      <h2></h2>
  
      <label for="teacher">Select Teacher to Evaluate:</label>
      <select id="teacher" bind:value={selectedTeacher}>
        <option value=""></option>
        {#each teacher as person}
          <option value={person}>{person}</option>
        {/each}
      </select>
  
      <label for="course">Select Course Subject:</label>
      <select id="course" bind:value={selectedCourse}>
        <option value=""></option>
        {#each courses as course}
          <option value={course}>{course}</option>
        {/each}
      </select>
  
      <label for="department">Select Department:</label>
      <select id="department" bind:value={selectedDepartment}>
        <option value=""></option>
        {#each departments as department}
          <option value={department}>{department}</option>
        {/each}
      </select>
  
      <button on:click={startEvaluation}>Start Evaluation</button>
    </div>
  
  