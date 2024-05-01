<script>
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
  
  <style>
    /* Styles for the page and tabs */
    body {
      font-family: "Arial", sans-serif;
      background-color: #f5f7fa;
      color: #333;
    }
  
    .container {
      max-width: 950px;
      margin: 0 auto;
      padding: 20px;
    }
  
    .tabs {
      display: flex;
      justify-content: space-between;
      background-color: #ffffff;
      box-shadow: 0 0 1px 0 rgba(0, 0, 0, 0.15), 0 6px 12px 0 rgba(0, 0, 0, 0.15);
      padding: 10px;
      border-radius: 30px;
      overflow: hidden;
    }
  
    .tab {
      flex: 1;
      text-align: center;
      padding: 10px;
      font-size: 1.25rem;
      font-weight: 500;
      border-radius: 30px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
  
    .tab:hover {
      background: #3498db;
      color: white;
    }
  
    .tab.active {
      background: #2980b9;
      color: white;
      font-size: 1.35rem;
      font-weight: 600;
    }
  
    /* Transition animations */
    .section {
      background: #ffffff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
      margin-top: 20px;
      transition: all 0.5s ease-in-out;
    }
  
    .slide-left {
      animation: slide-in-left 0.5s ease-in-out;
    }
  
    .slide-right {
      animation: slide-in-right 0.5s ease-in-out;
    }
  
    @keyframes slide-in-left {
      from {
        transform: translateX(100%);
      }
      to {
        transform: translateX(0);
      }
    }
  
    @keyframes slide-in-right {
      from {
        transform: translateX(-100%);
      }
      to {
        transform: translateX(0);
      }
    }
  
    /* Custom radio styles for questions */
    .question {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;
    }
  
    .radio-group {
      display: flex;
      gap: 15px;
    }
  
    input[type="radio"] {
      display: none; /* Hide the default radio button */
    }
  
    .radio-label {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 10px;
      font-size: 1rem;
      font-weight: 500;
      border-radius: 30px; /* Pill shape */
      cursor: pointer;
      transition: background 0.3s;
    }
  
    .radio-label-default {
      background: #e6eef9;
    }
  
    input[type="radio"]:checked + .radio-label {
      background: #185ee0; /* Primary color when checked */
      color: white; /* Text color when checked */
    }
  
    .submit-button {
      display: block;
      background: #3498db;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
      text-align: center;
      transition: background 0.3s;
      margin: 20px auto;
    }
  
    .submit-button:hover {
      background: #2980b9;
    }
  </style>
  
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
  