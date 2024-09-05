// eslint-disable-next-line @typescript-eslint/ban-ts-comment
// @ts-ignore
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
  let transitionDirection = 'left';
  let isSubmitting = false;
  let alertMessage = '';

  function setActiveTab(tab) {
    transitionDirection = tabs.indexOf(tab) > tabs.indexOf(activeTab) ? 'left' : 'right';
    activeTab = tab;
  }

  function goToNextTab() {
    const currentIndex = tabs.indexOf(activeTab);
    if (currentIndex < tabs.length - 1) {
      setActiveTab(tabs[currentIndex + 1]);
    }
  }

  function goToPreviousTab() {
    const currentIndex = tabs.indexOf(activeTab);
    if (currentIndex > 0) {
      setActiveTab(tabs[currentIndex - 1]);
    }
  }

  function isLastTab() {
    return activeTab === tabs[tabs.length - 1];
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
  <div
    class="tab {activeTab === tab ? 'active' : ''}"
    on:click={() => setActiveTab(tab)}
  >
    {tab}
  </div>
  {/each}
  <div class="tab-glider" style="transform: translateX({tabs.indexOf(activeTab) * 100}%)"></div>
</div>

<div class="content-container">
  {#if activeTab}
    <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
      <h2>{activeTab}</h2>
      <table class="evaluation-table">
        <thead>
          <tr>
            <th>Question</th>
            {#each [1, 2, 3] as teacher (teacher)}
              <th>Teacher {teacher}</th>
            {/each}
          </tr>
        </thead>
        <tbody>
          {#each questions[activeTab] as question, index (question)}
            <tr>
              <td>{index + 1}. {question}</td>
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
  {/if}

  {#if alertMessage}
    <div class="confirmation-message">{alertMessage}</div>
  {/if}

  {#if activeTab !== 'Class Administration'}
    <button class="back-button" on:click={goToPreviousTab}>Back</button>
  {/if}
  
  {#if activeTab !== 'Other Information'}
    <button class="next-button" on:click={goToNextTab}>Next</button>
  {/if}

  {#if isLastTab() && activeTab === 'Other Information'}
    <button on:click={submitForm} class="submit-button">Submit</button>
  {/if}
</div>

{#if isSubmitting}
  <div class="loading-overlay">
    <div class="spinner"></div>
  </div>
{/if}

<style>
  /* General Styles */
  .tabs {
    display: flex;
    overflow: hidden;
    position: relative;
  }

  .tab {
    cursor: pointer;
    padding: 10px 20px;
    margin-right: 5px;
    background: #f0f0f0;
    border-radius: 5px;
  }

  .tab.active {
    background: #007bff;
    color: white;
  }

  .tab-glider {
    position: absolute;
    bottom: 0;
    left: 0;
    height: 2px;
    background: #007bff;
    transition: transform 0.3s ease;
  }

  .section {
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-top: 10px;
  }

  .slide-left {
    animation: slideInLeft 0.5s forwards;
  }

  .slide-right {
    animation: slideInRight 0.5s forwards;
  }

  @keyframes slideInLeft {
    from { transform: translateX(100%); }
    to { transform: translateX(0); }
  }

  @keyframes slideInRight {
    from { transform: translateX(-100%); }
    to { transform: translateX(0); }
  }

  .evaluation-table {
    width: 100%;
    border-collapse: collapse;
  }

  .evaluation-table th,
  .evaluation-table td {
    padding: 10px;
    border: 1px solid #ddd;
    text-align: center;
  }

  .evaluation-table thead th {
    background: #f0f0f0;
  }

  .radio-label {
    display: flex;
    align-items: center;
  }

  .radio-text {
    margin-left: 5px;
  }

  .comment-input {
    width: 100%;
    box-sizing: border-box;
  }

  .back-button,
  .next-button,
  .submit-button {
    margin: 10px 5px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    color: white;
    cursor: pointer;
  }

  .back-button {
    background: #6c757d;
  }

  .next-button {
    background: #007bff;
  }

  .submit-button {
    background: #28a745;
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
    to { transform: rotate(360deg); }
  }

  .confirmation-message {
    color: #008000;
    font-size: 1rem;
    text-align: center;
    margin-top: 20px;
  }

  .form-help-text {
    color: red;
    font-size: 0.875rem;
  }

  .question-container {
    margin-bottom: 15px;
  }

  .question {
    font-weight: bold;
  }

  .radio-group {
    display: flex;
    gap: 10px;
    margin-top: 5px;
  }

  .question-number {
    font-weight: bold;
    margin-right: 5px;
  }

  .question-content {
    display: inline;
  }
</style>
