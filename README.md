
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Election Insights — Data Collection</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#6ee7b7;--accent-2:#60a5fa;--muted:#94a3b8}
    *{box-sizing:border-box;font-family:Inter,system-ui,Arial;color:#e6eef8}
    body{margin:0;background:linear-gradient(180deg,#071029 0%,#07172f 100%);min-height:100vh;padding:28px}
    .container{max-width:1000px;margin:0 auto}
    header{display:flex;align-items:center;justify-content:space-between;margin-bottom:18px}
    h1{font-size:20px;margin:0}
    p.lead{color:var(--muted);margin:4px 0 0}
    .card{background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.03);padding:18px;border-radius:12px;margin-bottom:16px}
    form .grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
    label{display:block;font-size:13px;color:var(--muted);margin-bottom:6px}
    input[type=text],input[type=number],select,textarea{width:100%;padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:inherit}
    textarea{min-height:90px}
    .full{grid-column:1/3}
    .row{display:flex;gap:8px}
    .btn{background:linear-gradient(90deg,var(--accent),var(--accent-2));padding:10px 14px;border-radius:10px;border:none;color:#021124;font-weight:700;cursor:pointer}
    .muted{color:var(--muted);font-size:13px}
    .actions{display:flex;gap:8px;align-items:center}
    .small{font-size:13px;padding:8px 10px;border-radius:8px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03)}
    footer{color:var(--muted);text-align:center;margin-top:12px;font-size:13px}
    /* dashboard */
    .charts{display:grid;grid-template-columns:1fr 1fr;gap:12px}
    @media(max-width:820px){.charts{grid-template-columns:1fr}.grid{grid-template-columns:1fr}.full{grid-column:1/2}}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div>
        <h1>Election Insights</h1>
        <p class="lead">Collecting community data for ethical insights and research</p>
      </div>
      <div class="actions">
        <button id="adminBtn" class="small">Admin Dashboard</button>
        <button id="exportBtn" class="small">Export CSV</button>
      </div>
    </header>

    <main>
      <section class="card" id="formCard">
        <h3>Participate — quick survey</h3>
        <p class="muted">Your response is anonymous unless you choose otherwise. Please answer honestly.</p>
        <form id="surveyForm">
          <div class="grid">
            <div>
              <label>Age</label>
              <input type="number" id="age" min="15" max="120" required />
            </div>
            <div>
              <label>Gender</label>
              <select id="gender">
                <option value="Prefer not to say">Prefer not to say</option>
                <option>Male</option>
                <option>Female</option>
                <option>Other</option>
              </select>
            </div>

            <div>
              <label>Tribal affiliation (optional)</label>
              <input type="text" id="tribe" placeholder="e.g., Kikuyu" />
            </div>
            <div>
              <label>Education level</label>
              <select id="education">
                <option>Secondary</option>
                <option>Diploma/Certificate</option>
                <option>Undergraduate</option>
                <option>Postgraduate</option>
                <option>Other</option>
              </select>
            </div>

            <div>
              <label>Voter registration status</label>
              <select id="vreg">
                <option>Registered</option>
                <option>Not registered</option>
                <option>Prefer not to say</option>
              </select>
            </div>
            <div>
              <label>Voter county</label>
              <input type="text" id="county" placeholder="e.g., Nairobi" />
            </div>

            <div>
              <label>Political affiliation (optional)</label>
              <input type="text" id="party" placeholder="e.g., Party name or Independent" />
            </div>
            <div>
              <label>Preferred candidate</label>
              <select id="preferred">
                <option>Odinga</option>
                <option>Ruto</option>
                <option>Matiangi</option>
                <option>Waihiga</option>
                <option>Wajackoyah</option>
                <option>Other</option>
              </select>
            </div>

            <div>
              <label>Voting intention</label>
              <select id="vint">
                <option>Will vote</option>
                <option>Undecided</option>
                <option>Will not vote</option>
              </select>
            </div>
            <div>
              <label>Income level</label>
              <select id="income">
                <option>Low</option>
                <option>Lower-middle</option>
                <option>Middle</option>
                <option>Upper-middle</option>
                <option>High</option>
              </select>
            </div>

            <div>
              <label>Employment status</label>
              <select id="employment">
                <option>Student</option>
                <option>Employed</option>
                <option>Self-employed</option>
                <option>Unemployed</option>
                <option>Other</option>
              </select>
            </div>
            <div>
              <label>Occupation (optional)</label>
              <input type="text" id="occupation" />
            </div>

            <div>
              <label>Religion (optional)</label>
              <input type="text" id="religion" />
            </div>
            <div>
              <label>Social media usage</label>
              <select id="sm">
                <option>Daily</option>
                <option>Weekly</option>
                <option>Rarely</option>
              </select>
            </div>

            <div class="full">
              <label>Popularity (0–10) — Rate these candidates:</label>
              <div style="display:grid;grid-template-columns:repeat(5,1fr);gap:8px;margin-top:8px">
                <div><label class="muted">Odinga</label><input type="number" min="0" max="10" id="pop_odinga" value="5"></div>
                <div><label class="muted">Ruto</label><input type="number" min="0" max="10" id="pop_ruto" value="5"></div>
                <div><label class="muted">Matiangi</label><input type="number" min="0" max="10" id="pop_matiangi" value="5"></div>
                <div><label class="muted">Waihiga</label><input type="number" min="0" max="10" id="pop_waihiga" value="5"></div>
                <div><label class="muted">Wajackoyah</label><input type="number" min="0" max="10" id="pop_wajackoyah" value="5"></div>
              </div>
            </div>

            <div class="full">
              <label>Any additional comments (optional)</label>
              <textarea id="comments" placeholder="Share context, reasons, or anything else..."></textarea>
            </div>

          </div>

          <div style="margin-top:12px;display:flex;gap:8px;align-items:center">
            <button type="submit" class="btn">Submit Response</button>
            <button id="clearBtn" type="button" class="small">Clear Form</button>
            <span class="muted">Responses are stored locally for demo & can be exported by admin.</span>
          </div>
        </form>
      </section>

      <section class="card" id="dashboard" style="display:none">
        <h3>Admin Dashboard</h3>
        <p class="muted">Overview of collected responses (local demo). Use export to download CSV.</p>
        <div class="charts">
          <canvas id="chartPref"></canvas>
          <canvas id="chartAge"></canvas>
        </div>
        <div style="margin-top:12px;display:flex;gap:8px;flex-wrap:wrap">
          <button id="refreshBtn" class="small">Refresh</button>
          <button id="clearDataBtn" class="small">Clear All Data</button>
        </div>
      </section>

    </main>

    <footer class="muted">Built for Election Insights — demo app. Respect privacy and use ethically.</footer>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    // simple data storage in localStorage for demo
    const KEY = 'election_insights_responses_v1'
    const adminBtn = document.getElementById('adminBtn')
    const dashboard = document.getElementById('dashboard')
    const formCard = document.getElementById('formCard')
    const exportBtn = document.getElementById('exportBtn')

    function loadResponses(){
      const raw = localStorage.getItem(KEY)
      return raw ? JSON.parse(raw) : []
    }
    function saveResponse(r){
      const arr = loadResponses()
      arr.push(r)
      localStorage.setItem(KEY, JSON.stringify(arr))
    }

    document.getElementById('surveyForm').addEventListener('submit', e=>{
      e.preventDefault()
      const data = {
        ts: new Date().toISOString(),
        age: Number(document.getElementById('age').value||0),
        gender: document.getElementById('gender').value,
        tribe: document.getElementById('tribe').value,
        education: document.getElementById('education').value,
        vreg: document.getElementById('vreg').value,
        county: document.getElementById('county').value,
        party: document.getElementById('party').value,
        preferred: document.getElementById('preferred').value,
        vint: document.getElementById('vint').value,
        income: document.getElementById('income').value,
        employment: document.getElementById('employment').value,
        occupation: document.getElementById('occupation').value,
        religion: document.getElementById('religion').value,
        sm: document.getElementById('sm').value,
        pop: {
          odinga: Number(document.getElementById('pop_odinga').value||0),
          ruto: Number(document.getElementById('pop_ruto').value||0),
          matiangi: Number(document.getElementById('pop_matiangi').value||0),
          waihiga: Number(document.getElementById('pop_waihiga').value||0),
          wajackoyah: Number(document.getElementById('pop_wajackoyah').value||0)
        },
        comments: document.getElementById('comments').value
      }
      saveResponse(data)
      alert('Thanks — your response has been recorded.')
      document.getElementById('surveyForm').reset()
    })

    document.getElementById('clearBtn').addEventListener('click', ()=>document.getElementById('surveyForm').reset())

    adminBtn.addEventListener('click', ()=>{
      const pass = prompt('Enter admin code (demo):')
      if(pass === 'admin123'){
        dashboard.style.display = 'block'
        formCard.style.display = 'none'
        renderCharts()
      } else if(pass === null){
        // canceled
      } else {
        alert('Wrong code')
      }
    })

    function aggregate(responses){
      const pref = {}
      const ages = { '<20':0, '20-29':0, '30-44':0, '45+':0 }
      responses.forEach(r=>{
        pref[r.preferred] = (pref[r.preferred]||0)+1
        const a = r.age
        if(a<20) ages['<20']++
        else if(a<30) ages['20-29']++
        else if(a<45) ages['30-44']++
        else ages['45+']++
      })
      return {pref, ages}
    }

    let chartPref=null, chartAge=null
    function renderCharts(){
      const data = loadResponses()
      const agg = aggregate(data)
      const ctx1 = document.getElementById('chartPref').getContext('2d')
      const ctx2 = document.getElementById('chartAge').getContext('2d')
      if(chartPref) chartPref.destroy()
      if(chartAge) chartAge.destroy()
      chartPref = new Chart(ctx1,{
        type:'bar',
        data:{labels:Object.keys(agg.pref),datasets:[{label:'Responses',data:Object.values(agg.pref),backgroundColor:['#60a5fa','#6ee7b7','#fca5a5','#f6d365','#c7b3ff']}]},
        options:{responsive:true,plugins:{legend:{display:false}}}
      })
      chartAge = new Chart(ctx2,{
        type:'pie',
        data:{labels:Object.keys(agg.ages),datasets:[{data:Object.values(agg.ages),backgroundColor:['#60a5fa','#6ee7b7','#fca5a5','#c7b3ff']}]},
        options:{responsive:true}
      })
    }

    document.getElementById('refreshBtn').addEventListener('click', renderCharts)
    document.getElementById('clearDataBtn').addEventListener('click', ()=>{
      if(confirm('Clear all stored responses?')){localStorage.removeItem(KEY);renderCharts();alert('Cleared')}
    })

    function convertToCSV(objArray) {
      const array = typeof objArray !== 'object' ? JSON.parse(objArray) : objArray
      if(array.length===0) return ''
      const keys = Object.keys(array[0])
      const lines = []
      lines.push(keys.join(','))
      for(const item of array){
        const row = keys.map(k=>{
          let val = item[k]
          if(typeof val === 'object') val = JSON.stringify(val)
          return '"'+String(val).replace(/"/g,'""')+'"'
        })
        lines.push(row.join(','))
      }
      return lines.join('\n')
    }

    exportBtn.addEventListener('click', ()=>{
      const arr = loadResponses()
      if(arr.length===0){alert('No data to export');return}
      const csv = convertToCSV(arr)
      const blob = new Blob([csv],{type:'text/csv;charset=utf-8;'});
      const url = URL.createObjectURL(blob)
      const a = document.createElement('a'); a.href=url; a.download='election_insights_responses.csv'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url)
    })

    // initial demo: hide admin if no data
    if(loadResponses().length>0){ /* show export */ }
  </script>
</body>
</html>

