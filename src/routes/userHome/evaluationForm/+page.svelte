<script>
  import Topbar from '$lib/components/common/Topbar.svelte';
  import Sidebar from '$lib/components/student/Sidebar.svelte';
  import './eval.css';

  let tabs = [
    'Class Administration',
    'Character Building',
    'Subject Preparation and Analysis',
    'Instructional Enrichment',
    'Test and Measurement',
    'Other Information'
  ];

  let activeTab = 'Class Administration';
  let isSubmitting = false;
  let alertMessage = '';

  function setActiveTab(tab) {
    activeTab = tab;
  }

  function nextTab() {
    const currentIndex = tabs.indexOf(activeTab);
    if (currentIndex < tabs.length - 1) {
      activeTab = tabs[currentIndex + 1];
    }
  }

  function previousTab() {
    const currentIndex = tabs.indexOf(activeTab);
    if (currentIndex > 0) {
      activeTab = tabs[currentIndex - 1];
    }
  }

  function submitForm() {
    isSubmitting = true;
    setTimeout(() => {
      isSubmitting = false;
      alertMessage = "Form submitted successfully!";
    }, 2000);
  }

  const questions = {
    'Class Administration': [
      "Provides integrated syllabus and properly explains policies and course content.",
      "Attends virtual and/or in-person classes as scheduled.",
      "Meets classes punctually.",
      "Informs students in advance of absence or change of schedule.",
      "Maintains a conducive learning environment.",
      "Encourages and maintains classroom cleanliness, and protects classroom furniture, equipment, and facilities from vandalism and misuse."
    ],
    'Character Building': [
      "Well-groomed and properly attired even in virtual and/or in-person classes.",
      "Radiates optimism and self-confidence.",
      "Inspires students to achieve their goals and career ambitions.",
      "Encourages students to improve their own personality and character.",
      "Honest, transparent, and trustworthy in dealing with students.",
      "Integrates moral and spiritual teachings in the subject taught."
    ],
    'Subject Preparation and Analysis': [
      "Makes students feel at ease.",
      "Speaks in a clear and audible voice.",
      "Uses the language as a medium of instruction correctly.",
      "Presents the subject matter in a clear, logical, and orderly manner.",
      "Provides a holistic view of the subject matter by explaining its relationship to other academic disciplines and clarifying its significance with respect to human survival and development.",
      "Gives relevant and challenging activities, homework, and term papers that encourage student initiative and creativity."
    ],
    'Instructional Enrichment': [
      "Uses technology and other audio-visual materials suited for learning.",
      "Prepares and punctually distributes required course references and instructional materials to students.",
      "Uses up-to-date texts and reference books, magazines, journals, and other reading materials for lecture purposes.",
      "Integrates e-Learning methods for classroom instruction, research, and reporting."
    ],
    'Test and Measurement': [
      "Uses and clearly explains the grading system.",
      "Gives test questions and instructions that can be easily understood.",
      "Gives test questions and coursework relevant to the syllabus.",
      "Promptly returns corrected test papers and other student outputs.",
      "Discusses the results of tests and advises students on how to improve their performance."
    ],
    'Other Information': [
      "Encourages student participation, initiative, and creativity in class activities.",
      "Individualizes instruction as needed.",
      "Uses innovative and effective teaching methods.",
      "Comments/Feedback"
    ]
  };

  const labels = ['Always', 'Sometimes', 'Never'];
</script>

<Topbar />
<Sidebar />

<div class="tabs">
  {#each tabs as tab (tab)}
    <div class="tab {activeTab === tab ? 'active' : ''}" on:click={() => setActiveTab(tab)}>
      {tab}
    </div>
  {/each}
</div>

<div class="tables-container">
  <table class="questions-table">
    <thead>
      <tr>
        <th>Question</th>
      </tr>
    </thead>
    <tbody>
      {#each questions[activeTab] as question, index (question)}
        <tr>
          <td>{index + 1}. {question}</td>
        </tr>
      {/each}
    </tbody>
  </table>

  <table class="teachers-table">
    <thead>
      <tr>
        {#each [1, 2, 3] as teacher (teacher)}
          <th>Teacher {teacher}</th>
        {/each}
      </tr>
    </thead>
    <tbody>
      {#each questions[activeTab] as question, index (question)}
        <tr>
          {#each [1, 2, 3] as teacher (teacher)}
            <td>
              {#if activeTab === 'Other Information' && index === 3}
                <textarea class="comment-input" rows="4" cols="50" placeholder="Enter your comments or feedback"></textarea>
              {:else}
                {#each labels as label (label)}
                  <label class="radio-label">
                    <input type="radio" name={`question_${index}_teacher_${teacher}`} value={label} />
                    <span class="radio-text">{label}</span>
                  </label>
                {/each}
              {/if}
            </td>
          {/each}
        </tr>
      {/each}
    </tbody>
  </table>
</div>

{#if alertMessage}
  <div class="confirmation-message">{alertMessage}</div>
{/if}

{#if tabs.indexOf(activeTab) > 0}
  <button class="back-button" on:click={previousTab}>Back</button>
{/if}

{#if tabs.indexOf(activeTab) < tabs.length - 1}
  <button class="next-button" on:click={nextTab}>Next</button>
{/if}

{#if activeTab === 'Other Information'}
  <button on:click={submitForm} class="submit-button">Submit</button>
{/if}

{#if isSubmitting}
  <div class="loading-overlay">
    <div class="spinner"></div>
  </div>
{/if}

<style>
  .tabs {
    display: flex;
    overflow: hidden;
    position: sticky;
    top: 60px; 
    z-index: 999; 
    background-color: white; 
    padding: 10px 0;
    border-bottom: 1px solid #ddd;
  }

  .tab {
    cursor: pointer;
    padding: 5px 10px;
    margin-right: 1px;
    background: #f0f0f0;
    border-radius: 5px;
    margin-bottom: 20px;
  }

  .tab.active {
    background: #007bff;
    color: white;
  }

  .tables-container {
    display: flex;
    gap: 10px;
    margin-top: 10890px;
    margin-left: 200px;
    width: 80%;
   
  }

  table {
    width: 50%; 
    border-collapse: collapse;
    margin: 0 auto;
  }

  th, td {
    border: 1px solid #ddd;
    padding: 5px;
    text-align: left;
    vertical-align: middle;
  }

  th {
    background-color: #f8f8f8;
  }

  .radio-label {
    display: block;
    margin: 5px 0;
  }

  .comment-input {
    width: 100%;
    box-sizing: border-box;
  }

  .submit-button {
    margin-top: 20px;
    padding: 10px 20px;
    background: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  .loading-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .spinner {
    border: 4px solid rgba(0, 0, 0, 0.1);
    border-left-color: #007bff;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    animation: spin 1s linear infinite;
  }

  @keyframes spin {
    to {
      transform: rotate(360deg);
    }
  }

  .confirmation-message {
    margin-top: 10px;
    color: #28a745;
  }

  td, th {
    height: 100px; 
  }

  .back-button, .next-button {
    margin-top: 20px;
    padding: 10px 20px;
    background: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  .back-button {
    margin-right: 10px;
  }
</style>