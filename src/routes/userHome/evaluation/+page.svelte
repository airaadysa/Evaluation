<script>
    import './eval.css'
    // Define the available tabs
    let tabs = [
      'Class Administration',
      'Character Building',
      'Subject Preparation',
      'Instructional Enrichment',
      'Test and Measurement',
      'Other Information'
    ];
  
    // Track the active tab
    let activeTab = 'Class Administration';
  
    // A variable to control the transition
    let transitionDirection = 'left';
  
    // Function to set active tab and determine transition direction
    function setActiveTab(tab) {
      transitionDirection = tabs.indexOf(tab) > tabs.indexOf(activeTab) ? 'left' : 'right';
      activeTab = tab;
    }
  </script>
  
 
  
  <div class="container">
    <!-- Tab Navigation -->
    <div class="tabs">
      {#each tabs as tab}
        <div
          class="tab {activeTab === tab ? 'active' : ''}"
          on:click={() => setActiveTab(tab)}
        >
          {tab}
        </div>
      {/each}
    </div>
  
    <!-- Class Administration Section -->
    {#if activeTab === 'Class Administration'}
      <div class="section {transitionDirection === 'left' ? 'slide-left' : 'slide-right'}">
        <h2>Class Administration</h2>
        <div class="question">
          <p>1. Provides integrated syllabus and properly explains policies and course content.</p>
          <div class="radio-group">
            <input type="radio" name="class_admin_1" id="always_1" />
            <label class="radio-label radio-label-default" for="always_1">Always Evident</label>
  
            <input type="radio" name="class_admin_1" id="sometimes_1" />
            <label class="radio-label radio-label-default" for="sometimes_1">Sometimes Evident</label>
  
            <input type="radio" name="class_admin_1" id="never_1" />
            <label class="radio-label radio-label-default" for="never_1">Not Evident</label>
          </div>
        </div>
        <!-- Additional questions here -->
      </div>
    {/if}
  
    <!-- Other sections, add more questions as needed -->
  </div>
  