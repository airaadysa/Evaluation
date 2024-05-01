<script>
  import Topbar from '$lib/components/Topbar.svelte';
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

  function setActiveTab(tab) {
    transitionDirection = tabs.indexOf(tab) > tabs.indexOf(activeTab) ? 'left' : 'right';
    activeTab = tab;
  }

  function goToNextTab() {
    const currentIndex = tabs.indexOf(activeTab);
    if (currentIndex < tabs.length - 1) {
      setActiveTab(tabs[currentIndex + 1]);
      window.location.href = '#';
    }
  }

  function goToPreviousTab() {
    const currentIndex = tabs.indexOf(activeTab);
    if (currentIndex > 0) {
      setActiveTab(tabs[currentIndex - 1]);
      window.location.href = '#';
    }
  }

  function isLastTab() {
    return activeTab === tabs[tabs.length - 1];
  }

  function submitForm() {
    console.log("Form submitted!");
  }
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
  {#if activeTab === 'Class Administration'}
    <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
      <h2>Class Administration</h2>
      {#each [
        "Provides integrated syllabus and properly explains policies and course content.",
        "Attends virtual and/or in-person classes as scheduled.",
        "Meets classes punctually.",
        "Informs students in advance of absence or change of schedule.",
        "Maintains a conducive learning environment.",
        "Encourages and maintains classroom cleanliness, and protects classroom furniture, equipment, and facilities from vandalism and misuse."
      ] as question, index (question)}
        <div class="question-container">
          <div class="question">
            <span class="question-number">{index + 1}.</span> <span class="question-content">{question}</span>
          </div>
          <div class="radio-group">
            {#each ['Always Evident', 'Sometimes Evident', 'Not Evident'] as label}
              <label class="radio-label">
                <input type="radio" name={`class_admin_{index}`} />
                <span class="radio-text">{label}</span>
              </label>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  {/if}

  {#if activeTab === 'Character Building'}
    <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
      <h2>Character Building</h2>
      {#each [
        "Well-groomed and properly attired even in virtual and/or in-person classes.",
        "Radiates optimism and self-confidence.",
        "Inspires students to achieve their goals and career ambitions.",
        "Encourages students to improve their own personality and character.",
        "Honest, transparent, and trustworthy in dealing with students.",
        "Integrates moral and spiritual teachings in the subject taught."
      ] as question, index (question)}
        <div class="question-container">
          <div class="question">
            <span class="question-number">{index + 1}.</span> <span class="question-content">{question}</span>
          </div>
          <div class="radio-group">
            {#each ['Always Evident', 'Sometimes Evident', 'Not Evident'] as label}
              <label class="radio-label">
                <input type="radio" name={`character_{index}`} />
                <span class="radio-text">{label}</span>
              </label>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  {/if}

  {#if activeTab === 'Subject Preparation and Analysis'}
    <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
      <h2>Subject Preparation and Analysis</h2>
      {#each [
        "Makes students feel at ease.",
        "Speaks in a clear and audible voice.",
        "Uses the language as a medium of instruction correctly.",
        "Presents the subject matter in a clear, logical, and orderly manner.",
        "Provides a holistic view of the subject matter by explaining its relationship to other academic disciplines and clarifying its significance with respect to human survival and development.",
        "Gives relevant and challenging activities, homework, and term papers that encourage student initiative and creativity."
      ] as question, index (question)}
        <div class="question-container">
          <div class="question">
            <span class="question-number">{index + 1}.</span> <span class="question-content">{question}</span>
          </div>
          <div class="radio-group">
            {#each ['Always Evident', 'Sometimes Evident', 'Not Evident'] as label}
              <label class="radio-label">
                <input type="radio" name={`subject_{index}`} />
                <span class="radio-text">{label}</span>
              </label>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  {/if}

  {#if activeTab === 'Instructional Enrichment'}
    <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
      <h2>Instructional Enrichment</h2>
      {#each [
        "Uses technology and other audio-visual materials suited for learning.",
        "Prepares and punctually distributes required course references and instructional materials to students.",
        "Uses up-to-date texts and reference books, magazines, journals, and other reading materials for lecture purposes.",
        "Integrates e-Learning methods for classroom instruction, research, and reporting."
      ] as question, index (question)}
        <div class="question-container">
          <div class="question">
            <span class="question-number">{index + 1}.</span> <span class="question-content">{question}</span>
          </div>
          <div class="radio-group">
            {#each ['Always Evident', 'Sometimes Evident', 'Not Evident'] as label}
              <label class="radio-label">
                <input type="radio" name={`instruction_{index}`} />
                <span class="radio-text">{label}</span>
              </label>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  {/if}

  {#if activeTab === 'Test and Measurement'}
    <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
      <h2>Test and Measurement</h2>
      {#each [
        "Uses and clearly explains the grading system.",
        "Gives test questions and instructions that can be easily understood.",
        "Gives test questions and coursework relevant to the syllabus.",
        "Promptly returns corrected test papers and other student outputs.",
        "Discusses the results of tests and advises students on how to improve their performance."
      ] as question, index (question)}
        <div class="question-container">
          <div class="question">
            <span class="question-number">{index + 1}.</span> <span class="question-content">{question}</span>
          </div>
          <div class="radio-group">
            {#each ['Always Evident', 'Sometimes Evident', 'Not Evident'] as label}
              <label class="radio-label">
                <input type="radio" name={`test_{index}`} />
                <span class="radio-text">{label}</span>
              </label>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  {/if}

  {#if activeTab === 'Other Information'}
    <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
      <h2>Other Information</h2>
      {#each [
        "Encourages student participation, initiative, and creativity in class activities.",
        "Individualizes instruction as needed.",
        "Uses innovative and effective teaching methods.",
        "Comments/Feedback"
      ] as question, index (question)}
        <div class="question-container">
          <div class="question">
            <span class="question-number">{index + 1}.</span> <span class="question-content">{question}</span>
          </div>
          <div class="radio-group">
            {#if index === 3}
              <textarea class="comment-input" rows="4" cols="50" placeholder="Enter your comments or feedback"></textarea>
            {:else}
              {#each ['Always Evident', 'Sometimes Evident', 'Not Evident'] as label}
                <label class="radio-label">
                  <input type="radio" name={`other_{index}`} />
                  <span class="radio-text">{label}</span>
                </label>
              {/each}
            {/if}
          </div>
        </div>
      {/each}
    </div>
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
