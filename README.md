<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Education Point - NCERT Solutions</title>

<meta name="theme-color" content="#007bb5"> 

<style>
/* New Sky Blue Deep Theme */
:root {
  --sky: #f0f8ff; 
  --sky-strong: #007bb5; 
  --card: #ffffff; 
  --muted: #444; 
  --shadow: 0 4px 12px rgba(0, 0, 0, 0.1); 
  --accent: #00bcd4; 
}

body { 
  margin: 0; 
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
  background: var(--sky); 
  color: #1a1a1a; 
}

header { 
  background: var(--sky-strong); 
  color: white; 
  padding: 16px 20px; 
  text-align: center; 
  box-shadow: var(--shadow); 
}

main { 
  padding: 20px; 
  max-width: 1200px; 
  margin: 0 auto; 
}

.subjects { 
  display: flex; 
  flex-wrap: wrap; 
  gap: 10px; 
  margin-bottom: 25px; 
  justify-content: center; 
}

.subject-btn { 
  background: #e1f5fe; 
  color: var(--sky-strong);
  border-radius: 20px; 
  padding: 10px 18px; 
  cursor: pointer; 
  border: 1px solid rgba(0, 123, 181, 0.2); 
  transition: all 0.2s ease;
  font-weight: 600;
}

.subject-btn:hover, .subject-btn.active { 
  background: var(--accent); 
  color: white; 
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 123, 181, 0.3);
}

.search-container {
  margin-bottom: 25px;
  text-align: center;
}
#searchInput {
  width: 100%;
  max-width: 600px;
  padding: 12px 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 16px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
  transition: border-color 0.3s;
}
#searchInput:focus {
  border-color: var(--sky-strong);
  outline: none;
}

.content { 
  background: var(--card); 
  padding: 20px; 
  border-radius: 12px; 
  box-shadow: var(--shadow); 
}

#subjectTitle {
  color: var(--sky-strong);
  margin-top: 0;
  border-bottom: 2px solid var(--accent);
  padding-bottom: 10px;
}

.tabs { 
  display: flex; 
  gap: 12px; 
  margin: 15px 0; 
  border-bottom: 1px solid #ddd;
}
.tabs button { 
  padding: 10px 15px; 
  border-radius: 8px 8px 0 0; 
  border: none;
  background: transparent;
  cursor: pointer; 
  font-weight: 500;
  color: var(--muted);
  transition: all 0.3s;
}
.tabs button.active { 
  background: var(--sky-strong); 
  color: white; 
  border-color: var(--sky-strong); 
  transform: translateY(1px);
}

.card { 
  background: #f7fcff; 
  padding: 15px; 
  border-radius: 8px; 
  margin-bottom: 15px; 
  border-left: 5px solid var(--accent); 
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
  transition: transform 0.2s;
}
.card:hover {
    transform: translateY(-2px);
}
.card h3 {
    margin-top: 0;
    color: var(--sky-strong);
    font-size: 1.1em;
}
.card p {
    color: var(--muted);
}


.download-row { 
  margin-top: 20px; 
  padding-top: 15px;
  border-top: 1px dashed #eee;
  display: flex; 
  gap: 10px; 
  flex-wrap: wrap; 
}

button { 
  cursor: pointer; 
  padding: 10px 15px;
  border-radius: 6px;
  border: none;
  background: var(--accent);
  color: white;
  font-weight: 600;
  transition: background 0.2s;
}
button:hover {
    background: #0097a7; 
}

footer { 
  margin-top: 30px; 
  padding: 15px; 
  color: #777; 
  font-size: 13px; 
  text-align: center; 
  background: white;
  border-top: 1px solid #eee;
}
</style>
</head>
<body>
<header>
  <h1>Education Point</h1>
  <p>Class 10 NCERT Notes & Solutions - Hindi</p>
</header>
<main>
  <div class="subjects" id="subjectsContainer"></div>
  
  <div class="search-container">
    <input type="text" id="searchInput" placeholder="Search Notes or Solutions..." onkeyup="filterContent()">
  </div>
  
  <div class="content">
    <h2 id="subjectTitle">Select a subject</h2>
    <div class="tabs">
      <button id="tabNotesBtn" class="active">Notes</button>
      <button id="tabSolutionsBtn">Solutions</button>
    </div>
    <div id="contentArea"></div>
    <div class="download-row">
      <button id="downloadNotesBtn">Download Notes (JSON)</button>
      <button id="downloadSolutionsBtn">Download Solutions (JSON)</button>
    </div>
  </div>
</main>
<footer>
  Education Point - Sky Blue Theme - Single File Version
</footer>

<script>
  // DATA (Your application's data structure)
  const DATA = {
    Math: {
      notes:[
        {chapter:"अध्याय 1 – वास्तविक संख्याएँ", notes:"HCF, LCM, आदि नोट्स"},
        {chapter:"अध्याय 2 – बहुपद", notes:"Factorization, remainder theorem"}
      ],
      solutions:[
        {title:"अध्याय 1 – प्रश्न 1", solution:"Step by step हल"},
        {title:"अध्याय 2 – प्रश्न 1", solution:"Step by step हल"}
      ]
    },
    Science:{
      notes:[{chapter:"अध्याय 1 – रासायनिक अभिक्रियाएँ", notes:"प्रकार और balancing"}],
      solutions:[{title:"अध्याय 1 – प्रश्न 1", solution:"Step by step हल"}]
    },
    SocialScience:{
      notes:[{chapter:"अध्याय 1 – इतिहास", notes:"Nationalism notes"}],
      solutions:[{title:"अध्याय 1 – प्रश्न 1", solution:"Step by step हल"}]
    },
    Hindi:{
      notes:[{chapter:"अध्याय 1 – कविता", notes:"नोट्स"}],
      solutions:[{title:"अध्याय 1 – प्रश्न 1", solution:"Step by step हल"}]
    },
    English:{
      notes:[{chapter:"Chapter 1 – Prose", notes:"Notes"}],
      solutions:[{title:"Chapter 1 – Question 1", solution:"Step by step"}]
    },
    Sanskrit:{
      notes:[{chapter:"अध्याय 1 – काव्य", notes:"नोट्स"}],
      solutions:[{title:"अध्याय 1 – प्रश्न 1", solution:"Step by step हल"}]
    }
  };


  // App Logic (Original app.js content)
  const subjectsContainer = document.getElementById('subjectsContainer');
  const contentArea = document.getElementById('contentArea');
  const subjectTitle = document.getElementById('subjectTitle');
  const searchInput = document.getElementById('searchInput');

  let currentSubject = null;
  let activeTab = 'notes';

  function renderSubjects(){
    subjectsContainer.innerHTML='';
    Object.keys(DATA).forEach(key=>{
      const btn=document.createElement('button');
      btn.className='subject-btn';
      if (key === currentSubject) {
          btn.classList.add('active');
      }
      btn.textContent=key;
      btn.onclick=()=>selectSubject(key);
      subjectsContainer.appendChild(btn);
    });
  }

  function selectSubject(key){
    currentSubject=key;
    subjectTitle.textContent=key;
    searchInput.value = '';
    renderSubjects(); 
    renderContent();
  }

  function renderContent(searchTerm=''){
    if(!currentSubject){ 
      contentArea.innerHTML='<div>Select a subject to view content.</div>'; 
      return; 
    }

    const list = DATA[currentSubject][activeTab];
    contentArea.innerHTML='';
    
    const lowerCaseSearchTerm = searchTerm.toLowerCase();

    const filteredList = list.filter(item => {
      // Check for chapter or title key
      const chapterTitle = (item.chapter || item.title || '').toLowerCase();
      // Check for notes or solution key
      const contentText = (item.notes || item.solution || '').toLowerCase();
      
      return chapterTitle.includes(lowerCaseSearchTerm) || contentText.includes(lowerCaseSearchTerm);
    });

    if (filteredList.length === 0 && searchTerm) {
        contentArea.innerHTML = `<div class="card">No results found for "${searchTerm}" in ${currentSubject} ${activeTab}.</div>`;
        return;
    }

    filteredList.forEach(item=>{
      const div=document.createElement('div');
      div.className='card';
      const title=document.createElement('h3');
      title.textContent=item.chapter || item.title;
      const p=document.createElement('p');
      p.textContent=item.notes || item.solution;
      div.appendChild(title);
      div.appendChild(p);
      contentArea.appendChild(div);
    });
  }

  // Global function called by onkeyup in index.html
  window.filterContent = function() {
      if (!currentSubject) {
          // Prevent search before subject is selected
          searchInput.value = '';
          return alert('Please select a subject first!');
      }
      renderContent(searchInput.value);
  };


  document.getElementById('tabNotesBtn').addEventListener('click',()=>{
    activeTab='notes';
    document.getElementById('tabNotesBtn').classList.add('active');
    document.getElementById('tabSolutionsBtn').classList.remove('active');
    searchInput.value = '';
    renderContent();
  });
  document.getElementById('tabSolutionsBtn').addEventListener('click',()=>{
    activeTab='solutions';
    document.getElementById('tabSolutionsBtn').classList.add('active');
    document.getElementById('tabNotesBtn').classList.remove('active');
    searchInput.value = '';
    renderContent();
  });

  document.getElementById('downloadNotesBtn').addEventListener('click',()=>{
    if(!currentSubject) return alert('Select a subject first');
    downloadBlob(JSON.stringify(DATA[currentSubject].notes,null,2),currentSubject+'_notes.json','application/json');
  });
  document.getElementById('downloadSolutionsBtn').addEventListener('click',()=>{
    if(!currentSubject) return alert('Select a subject first');
    downloadBlob(JSON.stringify(DATA[currentSubject].solutions,null,2),currentSubject+'_solutions.json','application/json');
  });

  function downloadBlob(content,filename,mime){
    const blob=new Blob([content],{type:mime+';charset=utf-8'});
    const url=URL.createObjectURL(blob);
    const a=document.createElement('a');
    a.href=url;
    a.download=filename;
    a.click();
    URL.revokeObjectURL(url);
  }

  renderSubjects();
</script>
</body>
</html>
