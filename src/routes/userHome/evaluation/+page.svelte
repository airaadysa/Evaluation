<script>
  import Topbar from '$lib/components/common/Topbar.svelte';
  import Sidebar from '$lib/components/student/Sidebar.svelte';
  import { goto } from '$app/navigation';

  let teachers = [
    { id: 1, name: 'Teacher 1' },
    { id: 2, name: 'Teacher 2' },
    { id: 3, name: 'Teacher 3' }
  ];

  let selectedTeachers = [];

  function toggleTeacher(teacherId) {
    const index = selectedTeachers.indexOf(teacherId);
    if (index === -1) {
      selectedTeachers = [...selectedTeachers, teacherId];
    } else {
      selectedTeachers = selectedTeachers.filter(id => id !== teacherId);
    }
  }

  function proceedToEvaluation() {
    if (selectedTeachers.length === 0) {
      alert("Please select at least one teacher.");
      return;
    }
    goto('/userHome/evaluationForm', {
      state: { teachers: selectedTeachers }
    });
  }
</script>

<Topbar />
<Sidebar />

<div class="container">
  <h1>Select Teachers to Evaluate</h1>
  <ul>
    {#each teachers as teacher}
      <li>
        <label>
          <input
            type="checkbox"
            value={teacher.id}
            on:change={() => toggleTeacher(teacher.id)}
          />
          {teacher.name}
        </label>
      </li>
    {/each}
  </ul>
  <button on:click={proceedToEvaluation}>Proceed to Evaluation</button>
</div>

<style>
  .container {
    padding: 20px;
  }

  h1 {
    font-size: 1.5rem;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    margin: 10px 0;
  }

  button {
    padding: 10px 20px;
    font-size: 1rem;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  button:hover {
    background-color: #0056b3;
  }
</style>
