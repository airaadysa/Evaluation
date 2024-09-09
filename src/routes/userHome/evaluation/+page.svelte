<script>
  import Topbar from '$lib/components/common/Topbar.svelte';
  import Sidebar from '$lib/components/student/Sidebar.svelte';
  import { goto } from '$app/navigation';

  let teachers = [
    { id: 1, name: 'Teacher 1', subject: 'Mathematics' },
    { id: 2, name: 'Teacher 2', subject: 'Science' },
    { id: 3, name: 'Teacher 3', subject: 'History' },
    { id: 4, name: 'Teacher 4', subject: 'English' },
    { id: 5, name: 'Teacher 5', subject: 'Art' }
  ];

  let selectedTeachers = [];

  function toggleTeacher(teacherId) {
    const index = selectedTeachers.indexOf(teacherId);

    if (index === -1) {
      if (selectedTeachers.length < 3) {
        selectedTeachers = [...selectedTeachers, teacherId];
      } else {
        alert("You can only select a maximum of 3 teachers.");
      }
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
  <div class="header">
    <h1>Select Teachers and Subjects to Evaluate</h1>
    <p>Please choose up to 3 teachers and their respective subjects you would like to evaluate.</p>
  </div>
  
  <div class="teacher-list">
    {#each teachers as teacher}
      <div class="teacher-item">
        <label class="teacher-label">
          <input
            type="checkbox"
            value={teacher.id}
            on:change={() => toggleTeacher(teacher.id)}
            disabled={selectedTeachers.length >= 3 && selectedTeachers.indexOf(teacher.id) === -1}
          />
          <span class="teacher-info">
            {teacher.name} - <span class="subject">{teacher.subject}</span>
          </span>
        </label>
      </div>
    {/each}
  </div>
  
  <div class="actions">
    <button on:click={proceedToEvaluation} class="proceed-btn">
      Proceed to Evaluation
    </button>
  </div>
</div>

<style>
  /* General Container */
  .container {
    padding: 20px;
    background-color: #f8f9fa;
    max-width: 800px;
    margin: 0 auto;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  /* Header */
  .header {
    text-align: center;
    margin-bottom: 20px;
  }

  h1 {
    font-size: 2rem;
    color: #343a40;
  }

  p {
    font-size: 1rem;
    color: #6c757d;
  }

  /* Teacher List */
  .teacher-list {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  .teacher-item {
    background-color: white;
    padding: 15px;
    border-radius: 6px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .teacher-item:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  .teacher-label {
    display: flex;
    align-items: center;
  }

  .teacher-info {
    margin-left: 10px;
    font-size: 1.2rem;
    color: #495057;
  }

  .subject {
    color: #007bff;
  }

  /* Actions */
  .actions {
    margin-top: 30px;
    text-align: center;
  }

  .proceed-btn {
    padding: 10px 20px;
    font-size: 1.2rem;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .proceed-btn:hover {
    background-color: #218838;
  }
</style>
