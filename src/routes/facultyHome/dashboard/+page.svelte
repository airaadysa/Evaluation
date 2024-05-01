<script>
    import Topbar from "$lib/components/Topbar.svelte";
    import Sidebar from "$lib/components/admin/Sidebar.svelte";
    let evaluations = [
      {
        category: 'Class Administration',
        questions: [
          { question: "Provides integrated syllabus and properly explains policies and course content.", rating: 2.75, interpretation: "Always Evident" },
          { question: "Attends virtual and/or in-person classes as scheduled.", rating: 1.80, interpretation: "Sometimes Evident" },
          { question: "Meets classes punctually.", rating: 3.00, interpretation: "Always Evident" },
          { question: "Informs students in advance of absence or change of schedule.", rating: 1.25, interpretation: "Not Evident" },
          { question: "Maintains a conducive learning environment.", rating: 2.90, interpretation: "Always Evident" },
          { question: "Encourages and maintains classroom cleanliness, and protects classroom furniture, equipment, and facilities from vandalism and misuse.", rating: 1.50, interpretation: "Not Evident" }
        ]
      },
      {
        category: 'Character Building',
        questions: [
          { question: "Well-groomed and properly attired even in virtual and/or in-person classes.", rating: 2.40, interpretation: "Sometimes Evident" },
          { question: "Radiates optimism and self-confidence.", rating: 2.70, interpretation: "Always Evident" },
          { question: "Inspires students to achieve their goals and career ambitions.", rating: 1.90, interpretation: "Sometimes Evident" },
          { question: "Encourages students to improve their own personality and character.", rating: 2.80, interpretation: "Always Evident" },
          { question: "Honest, transparent, and trustworthy in dealing with students.", rating: 3.00, interpretation: "Always Evident" },
          { question: "Integrates moral and spiritual teachings in the subject taught.", rating: 1.20, interpretation: "Not Evident" }
        ]
      },
      {
        category: 'Subject Preparation and Analysis',
        questions: [
          { question: "Makes students feel at ease.", rating: 2.70, interpretation: "Always Evident" },
          { question: "Speaks in a clear and audible voice.", rating: 2.90, interpretation: "Always Evident" },
          { question: "Uses the language as a medium of instruction correctly.", rating: 2.80, interpretation: "Always Evident" },
          { question: "Presents the subject matter in a clear, logical, and orderly manner.", rating: 2.75, interpretation: "Always Evident" },
          { question: "Provides a holistic view of the subject matter by explaining its relationship to other academic disciplines and clarifying its significance with respect to human survival and development.", rating: 2.60, interpretation: "Always Evident" },
          { question: "Gives relevant and challenging activities, homework, and term papers that encourage student initiative and creativity.", rating: 2.95, interpretation: "Always Evident" }
        ]
      },
      {
        category: 'Instructional Enrichment',
        questions: [
          { question: "Uses technology and other audio-visual materials suited for learning.", rating: 2.85, interpretation: "Always Evident" },
          { question: "Prepares and punctually distributes required course references and instructional materials to students.", rating: 2.80, interpretation: "Always Evident" },
          { question: "Uses up-to-date texts and reference books, magazines, journals, and other reading materials for lecture purposes.", rating: 2.70, interpretation: "Always Evident" },
          { question: "Integrates e-Learning methods for classroom instruction, research, and reporting.", rating: 2.65, interpretation: "Always Evident" }
        ]
      },
      {
        category: 'Test and Measurement',
        questions: [
          { question: "Uses and clearly explains the grading system.", rating: 2.95, interpretation: "Always Evident" },
          { question: "Gives test questions and instructions that can be easily understood.", rating: 2.80, interpretation: "Always Evident" },
          { question: "Gives test questions and coursework relevant to the syllabus.", rating: 2.75, interpretation: "Always Evident" },
          { question: "Promptly returns corrected test papers and other student outputs.", rating: 2.85, interpretation: "Always Evident" },
          { question: "Discusses the results of tests and advises students on how to improve their performance.", rating: 2.90, interpretation: "Always Evident" }
        ]
      },
      {
        category: 'Other Information',
        questions: [
          { question: "Encourages student participation, initiative, and creativity in class activities.", rating: 2.70, interpretation: "Always Evident" },
          { question: "Individualizes instruction as needed.", rating: 2.85, interpretation: "Always Evident" },
          { question: "Uses innovative and effective teaching methods.", rating: 2.75, interpretation: "Always Evident" }
        ]
      }
    ];
  </script>
  
  <style>
    .dashboard {
      font-family: Arial, sans-serif;
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
    }
  
    h1 {
      text-align: center;
      margin-bottom: 20px;
    }
  
    h2 {
      margin-top: 30px;
      margin-bottom: 10px;
      font-size: 1.2rem;
    }
  
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 10px;
      border: 1px solid #3498db;
    }
  
    th, td {
      border: 1px solid #3498db;
      padding: 8px;
      text-align: left;
    }
  
    th {
      background-color: #3498db;
      color: white;
    }
  
    tr:nth-child(even) {
      background-color: #f2f2f2;
    }
  
    tr:hover {
      background-color: #ddd;
    }
  
    /* Add styles for interpretation text colors */
    .interpretation-red {
      color: rgb(183, 12, 12);
    }
  
    .interpretation-yellow {
      color: rgb(195, 195, 3);
    }
  
    .interpretation-green {
      color: rgb(0, 145, 0);
    }
  
    .info {
      margin-bottom: 20px;
      margin-top: 60px;
    }
  
    .info p {
      margin: 5px 0;
    }
  </style>
  <Topbar/>
  <Sidebar/>
  <div class="dashboard">
    
    
    <div class="info">
      <p><strong>Employment Status:</strong> Full-time</p>
      <p><strong>Area of Specialization:</strong> Computer Science</p>
      <p><strong>Department:</strong> Faculty of Science</p>
      <p><strong>School Year:</strong> 2023-2024</p>
    </div>
  
    {#each evaluations as { category, questions }}
      <h2>{category}</h2>
      <table>
        <thead>
          <tr>
            <th>Question</th>
            <th>Rating</th>
            <th>Interpretation</th>
          </tr>
        </thead>
        <tbody>
          {#each questions as { question, rating, interpretation }}
            <tr>
              <td>{question}</td>
              <td>{rating}</td>
              <td class="{interpretation === 'Not Evident' ? 'interpretation-red' : (interpretation === 'Sometimes Evident' ? 'interpretation-yellow' : 'interpretation-green')}">{interpretation}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    {/each}
  
    <div class="info">
      <h2>Overall Rating Interpretation</h2>
      <p>The overall rating interpretation goes here.</p>
    </div>
  </div>
  