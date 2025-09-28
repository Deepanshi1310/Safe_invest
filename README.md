
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Fraud Shield AI — Demo</title>

  <!-- Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg:#f4f7ff;
      --card:#ffffff;
      --accent:#3b82f6;
      --accent-2:#7c5cff;
      --muted:#6b7280;
      --danger:#ef4444;
      --success:#10b981;
      --radius:14px;
      font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      background: linear-gradient(180deg,var(--bg), #ffffff 60%);
      color:#0f172a;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      padding:28px;
    }

    .wrap{max-width:1100px;margin:0 auto;display:grid;grid-template-columns:1fr;gap:18px}
    header.site{
      display:flex;align-items:center;gap:16px;padding:14px;border-radius:12px;
      background:linear-gradient(90deg,var(--accent),var(--accent-2));color:white;box-shadow:0 10px 30px rgba(59,130,246,0.12);
    }
    .logo{
      width:64px;height:64px;border-radius:50%;overflow:hidden;flex:0 0 64px;border:3px solid rgba(255,255,255,0.18);display:flex;align-items:center;justify-content:center;background:rgba(255,255,255,0.07)
    }
    .logo img{width:100%;height:100%;object-fit:cover;display:block}
    .brand h1{font-size:20px;margin:0 0 4px 0;font-weight:700}
    .brand p{margin:0;font-size:13px;opacity:0.95}

    /* Tabs */
    .tabs{display:flex;gap:8px;margin-top:8px}
    .tab{padding:8px 14px;border-radius:999px;background:rgba(255,255,255,0.08);color:white;cursor:pointer;font-weight:600;font-size:14px}
    .tab.active{background:white;color:var(--accent);box-shadow:0 6px 20px rgba(59,130,246,0.12)}

    /* content */
    .main-grid{display:grid;grid-template-columns:1fr 380px;gap:18px;margin-top:12px}
    @media (max-width:1000px){.main-grid{grid-template-columns:1fr}}

    .card{background:var(--card);border-radius:var(--radius);padding:18px;box-shadow:0 8px 30px rgba(15,23,42,0.06)}
    .h2{font-size:18px;margin:0 0 8px 0;font-weight:700;color:var(--accent)}
    .muted{color:var(--muted);font-size:13px}

    .form-row{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin-bottom:12px}
    @media (max-width:700px){.form-row{grid-template-columns:1fr}}

    label{font-weight:600;font-size:13px;color:#0f172a;display:block;margin-bottom:6px}
    .input, select, textarea{width:100%;padding:10px 12px;border-radius:10px;border:1px solid #e6e9ef;font-size:14px;background:transparent}
    textarea{min-height:96px;resize:vertical}
    .small{font-size:12px;color:var(--muted)}

    .chips{display:flex;flex-wrap:wrap;gap:8px}
    .chip{padding:8px 10px;border-radius:10px;border:1px solid #eef2ff;background:#fbfdff;cursor:pointer;font-size:13px}
    .chip.active{background:linear-gradient(90deg,var(--accent),var(--accent-2));color:white;border:0;box-shadow:0 8px 22px rgba(124,92,255,0.12)}

    .actions{display:flex;gap:10px;margin-top:12px;align-items:center;flex-wrap:wrap}
    .btn{padding:10px 14px;border-radius:10px;border:0;cursor:pointer;font-weight:700}
    .btn.primary{background:linear-gradient(90deg,var(--accent),var(--accent-2));color:white;box-shadow:0 8px 24px rgba(59,130,246,0.12)}
    .btn.ghost{background:transparent;border:1px solid #e6e9ef;padding:9px 12px}
    .btn.warn{background:#fff4e6;border:1px solid #ffddbb;color:#7a4a00}

    /* right column specifics */
    .result-title{font-weight:700;color:#0f172a;margin-bottom:8px}
    .risk-high{color:var(--danger);font-weight:800}
    .risk-med{color:#b45309;font-weight:800}
    .risk-low{color:var(--success);font-weight:800}

    .video-list{display:grid;gap:12px}
    .video-embed iframe{width:100%;height:200px;border-radius:10px;border:0}

    .footer-note{font-size:13px;color:var(--muted);text-align:center;margin-top:10px}
    .link{color:var(--accent);font-weight:700;text-decoration:none}

    /* simulation styles */
    .sim-card{background:linear-gradient(180deg,#ffffff,#fbfdff);padding:18px;border-radius:12px;box-shadow:0 10px 30px rgba(15,23,42,0.06)}
    .sim-question{font-weight:700;margin-bottom:8px}
    .sim-option{display:block;padding:10px;border-radius:10px;border:1px solid #eef2ff;margin-bottom:8px;cursor:pointer;background:white}
    .sim-option.selected{border-color:var(--accent);background:linear-gradient(90deg,rgba(59,130,246,0.06),rgba(124,92,255,0.03))}
    .sim-feedback{margin-top:8px;padding:10px;border-radius:8px;background:#f8fafc;border:1px solid #eef2ff;color:var(--muted)}

    /* subtle hover */
    .chip:hover{transform:translateY(-2px);transition:all .12s ease}
    .btn.primary:hover{transform:translateY(-2px);transition:all .12s ease}
  </style>
</head>
<body>
  <div class="wrap">
    <header class="site">
      <div class="logo" title="Fraud Shield AI logo">
        <!-- absolute path on user's machine as provided -->
        <img src="C:\Users\DELL\Downloads\WhatsApp Image 2025-09-27 at 19.51.23_b11252d7.jpg" alt="Fraud Shield Logo" onerror="this.style.display='block'"/>
      </div>
      <div class="brand">
        <h1>Fraud Shield AI</h1>
        <p class="muted">Rapid, privacy-first call risk check — UI demo (no model/backend)</p>
        <div class="tabs" style="margin-top:8px">
          <div class="tab active" id="tab-check" onclick="showTab('check')">Check Call</div>
          <div class="tab" id="tab-videos" onclick="showTab('videos')">Awareness Videos</div>
          <div class="tab" id="tab-sim" onclick="showTab('simulation')">Fraud Simulation</div>
        </div>
      </div>
    </header>

    <!-- MAIN GRID (hidden when Simulation opens full width) -->
    <div class="main-grid" id="mainGrid">
      <!-- LEFT: Check Call form -->
      <section class="card" id="panel-check">
        <div class="h2">Describe the call</div>
        <p class="muted">Fill the details below. This is a UI demo — results are mock and for guidance only.</p>

        <form id="callForm" onsubmit="return onSubmitForm(event)" style="margin-top:14px">
          <div class="form-row">
            <div>
              <label for="callerName">Caller name</label>
              <input id="callerName" class="input" type="text" placeholder="Company / Unknown" />
            </div>
            <div>
              <label for="phone">Phone (optional)</label>
              <input id="phone" class="input" type="tel" placeholder="+91-XXXXXXXXXX" />
              <div class="small">We recommend not entering full PII — optional</div>
            </div>
          </div>

          <div class="form-row">
            <div>
              <label for="datetime">Date & time</label>
              <input id="datetime" class="input" type="datetime-local" max="" />
            </div>
            <div>
              <label for="duration">Call length (seconds)</label>
              <input id="duration" class="input" type="number" min="0" placeholder="e.g. 45" />
            </div>
          </div>

          <div style="margin-bottom:12px">
            <label for="reason">Call reason</label>
            <select id="reason" class="input">
              <option>Banking / Payment request</option>
              <option>Government / Tax / Penalty</option>
              <option>Tech support</option>
              <option>Prize / Lottery</option>
              <option>Investment / Trading offer</option>
              <option>Job / Employment offer</option>
              <option>Loan / EMI assistance</option>
              <option>Other</option>
            </select>
          </div>

          <div style="margin-bottom:12px">
            <label>Did they ask for money, OTP, or bank details?</label>
            <div class="chips" role="radiogroup" aria-label="Asked sensitive">
              <div class="chip" id="asked-no" onclick="setToggle('asked','No')">No</div>
              <div class="chip" id="asked-yes" onclick="setToggle('asked','Yes')">Yes</div>
              <div class="chip" id="asked-unsure" onclick="setToggle('asked','Unsure')">Unsure</div>
            </div>
            <div style="margin-top:8px" class="small">If yes, choose specific details:</div>
            <div class="chips" style="margin-top:8px">
              <label class="chip"><input type="checkbox" id="d-otp" /> OTP</label>
              <label class="chip"><input type="checkbox" id="d-bank" /> Bank account</label>
              <label class="chip"><input type="checkbox" id="d-upi" /> UPI</label>
              <label class="chip"><input type="checkbox" id="d-card" /> Card details</label>
            </div>
          </div>

          <div style="margin-bottom:12px">
            <label>Asked to install app / click link?</label>
            <div class="chips">
              <div class="chip" id="app-no" onclick="setToggle('app','No')">No</div>
              <div class="chip" id="app-yes" onclick="setToggle('app','Yes')">Yes</div>
            </div>
          </div>

          <div style="margin-bottom:12px">
            <label for="validated">Was caller able to validate info about you?</label>
            <select id="validated" class="input">
              <option>No</option>
              <option>Only basic (name)</option>
              <option>Sensitive (DOB / account)</option>
            </select>
          </div>

          <div style="margin-bottom:12px">
            <label>Suspicious audio cues</label>
            <div class="chips">
              <label class="chip"><input type="checkbox" id="a-script" /> Scripted</label>
              <label class="chip"><input type="checkbox" id="a-robot" /> Robotic / TTS</label>
              <label class="chip"><input type="checkbox" id="a-silence" /> Long silence</label>
              <label class="chip"><input type="checkbox" id="a-bg" /> Background noise</label>
            </div>
          </div>

          <div style="margin-bottom:12px">
            <label>Did caller claim to be from</label>
            <div class="chips">
              <label class="chip"><input type="checkbox" id="c-bank" /> Bank</label>
              <label class="chip"><input type="checkbox" id="c-gov" /> Government / Police</label>
              <label class="chip"><input type="checkbox" id="c-pay" /> Payment platform</label>
              <label class="chip"><input type="checkbox" id="c-emp" /> Employer</label>
            </div>
          </div>

          <div style="margin-bottom:12px">
            <label for="notes">Short notes (do NOT enter OTPs/cards)</label>
            <textarea id="notes" class="input" placeholder="Any brief context — tone, exact ask, links..."></textarea>
          </div>

          <!-- NEW: File upload and Attach Link -->
          <div style="margin-bottom:12px">
            <label for="attachments">Attach files (audio / pdf / images / video) — optional</label>
            <input id="attachments" class="input" type="file" multiple accept="audio/*,application/pdf,image/*,video/*" onchange="displayFiles()" />
            <div id="fileList" class="small" style="margin-top:8px;color:var(--muted)">No files attached.</div>
          </div>

          <div style="margin-bottom:12px">
            <label for="attachLink">Attach a link (e.g., the link the caller sent)</label>
            <input id="attachLink" class="input" type="url" placeholder="https://example.com/..." />
            <div class="small">Provide any suspicious link you received (optional). This demo does not open or validate links remotely.</div>
          </div>

          <div style="display:flex;gap:10px;align-items:center;flex-wrap:wrap">
            <button class="btn primary" type="submit">Check Risk</button>
            <button type="button" class="btn ghost" onclick="resetForm()">Reset</button>

            <div style="margin-left:auto;min-width:240px">
              <label style="display:block;font-weight:700;margin-bottom:6px">Select your State / UT</label>
              <select id="stateSelect" class="input">
                <option value="">-- Select state / UT --</option>
                <option>Andhra Pradesh</option>
                <option>Arunachal Pradesh</option>
                <option>Assam</option>
                <option>Bihar</option>
                <option>Chhattisgarh</option>
                <option>Goa</option>
                <option>Gujarat</option>
                <option>Haryana</option>
                <option>Himachal Pradesh</option>
                <option>Jharkhand</option>
                <option>Karnataka</option>
                <option>Kerala</option>
                <option>Madhya Pradesh</option>
                <option>Maharashtra</option>
                <option>Manipur</option>
                <option>Meghalaya</option>
                <option>Mizoram</option>
                <option>Nagaland</option>
                <option>Odisha</option>
                <option>Punjab</option>
                <option>Rajasthan</option>
                <option>Sikkim</option>
                <option>Tamil Nadu</option>
                <option>Telangana</option>
                <option>Tripura</option>
                <option>Uttar Pradesh</option>
                <option>Uttarakhand</option>
                <option>West Bengal</option>
                <option>Andaman & Nicobar</option>
                <option>Chandigarh</option>
                <option>Dadra and Nagar Haveli and Daman and Diu</option>
                <option>Delhi</option>
                <option>Jammu & Kashmir</option>
                <option>Ladakh</option>
                <option>Puducherry</option>
              </select>
              <div style="margin-top:8px;display:flex;gap:8px">
                <button type="button" class="btn ghost" onclick="showStateContact()">Get Cyber Cell Contact</button>
                <button type="button" class="btn warn" onclick="reportDemo()">Report (demo)</button>
              </div>
              <div id="stateContact" style="margin-top:10px;font-size:13px;color:var(--muted)"></div>
            </div>
          </div>
        </form>
      </section>

      <!-- RIGHT: Results and videos tab -->
      <aside>
        <div class="card" id="resultCard">
          <div class="result-title">Result</div>
          <div id="resultBlock" style="min-height:160px">
            <div class="muted">Submit the form to see a demo risk estimate here. This is a UI-only mock result.</div>
          </div>
        </div>

        <div class="card" id="videosCard" style="margin-top:12px;display:none">
          <div class="result-title">Awareness Videos</div>
          <div class="muted" style="margin-bottom:10px">Selected RBI / Government / National Cyber Crime Portal videos to learn about frauds and reporting.</div>

          <div class="video-list">
            <div class="video-embed">
              <iframe src="https://www.youtube.com/embed/nJeIGHLiLdA" title="RBI Advisory" allowfullscreen></iframe>
            </div>
            <div class="video-embed">
              <iframe src="https://www.youtube.com/embed/HI7SLTfMpBY" title="National Cybercrime Portal — How to report" allowfullscreen></iframe>
            </div>
            <div class="video-embed">
              <iframe src="https://www.youtube.com/embed/dSwQ-v2m_f0" title="RBI Deepfake Caution" allowfullscreen></iframe>
            </div>
          </div>

          <div style="margin-top:12px;font-size:13px" class="muted">
            Sources: National Cyber Crime Reporting Portal; I4C (MHA); RBI advisories. For official reporting use the portal or helpline below.
          </div>
        </div>
      </aside>
    </div>

    <!-- FRAUD SIMULATION PANEL (full width; hidden by default) -->
    <section id="panel-sim" style="display:none">
      <div class="sim-card card">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div>
            <div class="h2">Fraud Simulation</div>
            <div class="muted">5 scenario-based exercises to test and improve your response to common online financial frauds.</div>
          </div>
          <div style="display:flex;gap:8px">
            <button class="btn ghost" onclick="resetSimulation()">Reset Simulation</button>
            <button class="btn primary" onclick="startSimulation()">Start / Continue</button>
          </div>
        </div>

        <hr style="margin:12px 0;border:none;border-top:1px solid #f1f5f9" />

        <div id="simContent" style="margin-top:12px">
          <div class="muted">Click <strong>Start</strong> to begin the scenarios. For each scenario, choose the best response and click <strong>Submit</strong> to see explanation.</div>
        </div>
      </div>
    </section>

    <div class="footer-note">
      This demo is UI-only. For official reporting, go to the National Cyber Crime Reporting Portal (or call 1930).
    </div>
  </div>

  <script>
    // set datetime default to now (and max)
    (function setNow(){
      const dt = new Date();
      function pad(n){return n<10? '0'+n : n}
      const s = dt.getFullYear()+'-'+pad(dt.getMonth()+1)+'-'+pad(dt.getDate())+'T'+pad(dt.getHours())+':'+pad(dt.getMinutes());
      const el = document.getElementById('datetime');
      if(el){ el.max = s; el.value = s;}
    })();

    // tabs
    function showTab(name){
      // set active tab
      ['check','videos','simulation'].forEach(n => {
        const t = document.getElementById('tab-'+n);
        if(t) t.classList.remove('active');
      });
      if(name === 'check') document.getElementById('tab-check').classList.add('active');
      if(name === 'videos') document.getElementById('tab-videos').classList.add('active');
      if(name === 'simulation') document.getElementById('tab-sim').classList.add('active');

      // toggle main grid and panels
      if(name === 'simulation') {
        document.getElementById('mainGrid').style.display = 'none';
        document.getElementById('panel-sim').style.display = 'block';
      } else {
        document.getElementById('mainGrid').style.display = 'grid';
        document.getElementById('panel-sim').style.display = 'none';
        document.getElementById('videosCard').style.display = (name === 'videos') ? 'block' : 'none';
      }
      // ensure result card visible when in check tab
      if(name === 'check') {
        document.getElementById('resultCard').scrollIntoView({behavior:'smooth'});
      }
      window.scrollTo({top:0, behavior:'smooth'});
    }

    // toggles (asked, app)
    const toggleState = {asked:'No', app:'No'};
    function setToggle(key,val){
      toggleState[key]=val;
      if(key==='asked'){
        ['asked-no','asked-yes','asked-unsure'].forEach(id=>{const el=document.getElementById(id); if(el) el.classList.remove('active')});
        const id = val==='Yes' ? 'asked-yes' : val==='Unsure' ? 'asked-unsure' : 'asked-no';
        const el = document.getElementById(id); if(el) el.classList.add('active');
      }
      if(key==='app'){
        ['app-no','app-yes'].forEach(id=>{const el=document.getElementById(id); if(el) el.classList.remove('active')});
        const id = val==='Yes' ? 'app-yes' : 'app-no';
        const el = document.getElementById(id); if(el) el.classList.add('active');
      }
    }
    // init toggles
    setToggle('asked','No'); setToggle('app','No');

    // reset
    function resetForm(){
      document.getElementById('callForm').reset();
      setToggle('asked','No'); setToggle('app','No');
      document.getElementById('resultBlock').innerHTML = '<div class="muted">Submit the form to see a demo risk estimate here. This is a UI-only mock result.</div>';
      document.getElementById('stateContact').innerHTML = '';
      document.getElementById('fileList').textContent = 'No files attached.';
    }

    // demo report
    function reportDemo(){ alert('Report submitted (demo). In a real app this would send an anonymized record to your backend for human review.'); }

    // display files
    function displayFiles(){
      const input = document.getElementById('attachments');
      const list = document.getElementById('fileList');
      if(!input.files || input.files.length === 0){
        list.textContent = 'No files attached.';
        return;
      }
      const names = Array.from(input.files).map(f => `${f.name} (${Math.round(f.size/1024)} KB)`);
      list.innerHTML = names.join('<br/>');
      // Note: files remain local in browser until you implement upload to a server.
    }

    // mock predictor (no 'press' references)
    function mockPredict(payload){
      let score=10;
      if(payload.asked==='Yes') score+=30;
      if(payload.details.includes('OTP')) score+=30;
      if(payload.app==='Yes') score+=15;
      if(payload.validated==='Sensitive (DOB / account)') score+=20;
      if(payload.claims.includes('Bank')) score+=10;
      score += payload.audioCues.length * 4;
      if(payload.duration && Number(payload.duration) < 12 && payload.asked==='Yes') score+=10;
      const prob = Math.min(98, Math.max(6, score));
      const label = prob>=75 ? 'High Risk' : (prob>=50 ? 'Medium Risk' : 'Low Risk');
      const reasons=[];
      if(payload.details.includes('OTP')) reasons.push('Caller asked for OTP');
      if(payload.details.includes('Bank account')) reasons.push('Requested bank account details');
      if(payload.app==='Yes') reasons.push('Asked to install app / click link');
      if(payload.validated==='Sensitive (DOB / account)') reasons.push('Claimed validated sensitive info');
      if(reasons.length===0) reasons.push('No clear red flags captured');
      return {label,prob,reasons};
    }

    // submit handler
    function onSubmitForm(e){
      e.preventDefault();
      const payload = {
        caller: document.getElementById('callerName').value.trim(),
        phone: document.getElementById('phone').value.trim(),
        datetime: document.getElementById('datetime').value,
        duration: document.getElementById('duration').value,
        reason: document.getElementById('reason').value,
        asked: toggleState.asked,
        details: [
          document.getElementById('d-otp').checked ? 'OTP' : null,
          document.getElementById('d-bank').checked ? 'Bank account' : null,
          document.getElementById('d-upi').checked ? 'UPI' : null,
          document.getElementById('d-card').checked ? 'Card details' : null
        ].filter(Boolean),
        app: toggleState.app,
        validated: document.getElementById('validated').value,
        audioCues: [
          document.getElementById('a-script').checked ? 'Scripted' : null,
          document.getElementById('a-robot').checked ? 'Robotic' : null,
          document.getElementById('a-silence').checked ? 'Long silence' : null,
          document.getElementById('a-bg').checked ? 'Background' : null
        ].filter(Boolean),
        claims: [
          document.getElementById('c-bank').checked ? 'Bank' : null,
          document.getElementById('c-gov').checked ? 'Government / Police' : null,
          document.getElementById('c-pay').checked ? 'Payment platform' : null,
          document.getElementById('c-emp').checked ? 'Employer' : null
        ].filter(Boolean),
        notes: document.getElementById('notes').value.trim(),
        attachments: document.getElementById('attachments').files ? Array.from(document.getElementById('attachments').files).map(f=>f.name) : [],
        attachLink: document.getElementById('attachLink').value.trim()
      };

      const out = mockPredict(payload);
      const className = out.label === 'High Risk' ? 'risk-high' : out.label === 'Medium Risk' ? 'risk-med' : 'risk-low';
      let html = `<div style="display:flex;justify-content:space-between;align-items:center">
                    <div><div class="${className}" style="font-size:18px">${out.label}</div>
                      <div class="small" style="margin-top:6px">Confidence: <strong>${out.prob}%</strong></div></div>
                    <div style="text-align:right" class="small muted">${payload.reason} • ${payload.duration ? payload.duration+'s' : 'duration N/A'}</div>
                  </div>
                  <hr style="margin:12px 0;border:none;border-top:1px solid #f1f5f9" />
                  <div><strong>Top reasons</strong><ul style="margin:8px 0 0 18px;color:var(--muted)">${out.reasons.map(r=>'<li>'+r+'</li>').join('')}</ul></div>
                  <div style="margin-top:10px"><strong>Suggested actions</strong>`;
      if(out.label === 'High Risk'){
        html += '<ul style="margin-left:18px;color:var(--muted)"><li>Hang up immediately — do not share OTP or bank details.</li><li>Contact your bank using official contact numbers.</li><li>Report to the National Cyber Crime Portal or your state cyber cell.</li></ul>';
      } else if(out.label === 'Medium Risk'){
        html += '<ul style="margin-left:18px;color:var(--muted)"><li>Verify independently via official numbers.</li><li>Do not share codes or login details.</li></ul>';
      } else {
        html += '<ul style="margin-left:18px;color:var(--muted)"><li>Proceed with caution. Cross-check any requests.</li></ul>';
      }
      // attach info display
      if(payload.attachments.length){
        html += `<div style="margin-top:10px"><strong>Attached files (local):</strong><div class="small" style="margin-top:6px;color:var(--muted)">${payload.attachments.join('<br/>')}</div></div>`;
      }
      if(payload.attachLink){
        html += `<div style="margin-top:10px"><strong>Attached link:</strong><div class="small" style="margin-top:6px;color:var(--muted)"><a href="${payload.attachLink}" target="_blank" rel="noopener">${payload.attachLink}</a></div></div>`;
      }
      html += `<div style="margin-top:12px;display:flex;gap:8px;justify-content:flex-end"><button class="btn ghost" onclick="saveDemo()">Save (demo)</button><button class="btn" onclick="resetForm()">New check</button></div></div>`;

      document.getElementById('resultBlock').innerHTML = html;
      document.getElementById('resultCard').scrollIntoView({behavior:'smooth'});
      return false;
    }

    function saveDemo(){ alert('Saved (demo). In a real app, this would store an anonymized report for review.'); }

    // STATE CONTACT: Option B - link out to official portal and I4C nodal officers
    function showStateContact(){
      const state = document.getElementById('stateSelect').value;
      if(!state){
        document.getElementById('stateContact').innerHTML = '<span style="color:#b45309;font-weight:700">Please select your state / UT first.</span>';
        return;
      }
      // Show link to national portal and I4C nodal officer page (official sources)
      const national = 'https://cybercrime.gov.in/';
      const i4c = 'https://i4c.mha.gov.in/nodal-officer.aspx';
      const meity = 'https://www.meity.gov.in/static/uploads/2024/12/3671943d58fed3caa285dcdeb52403b6.pdf';
      const html = `
        <div><strong>Official reporting & contacts</strong></div>
        <div class="small" style="margin-top:8px;color:var(--muted)">
          • For filing complaints, use the National Cyber Crime Reporting Portal or call <strong>1930</strong>. <br/>
          • For state-level nodal officers and cyber cell contacts, consult the I4C (MHA) nodal officer list or the state police/existing cyber cell page.
        </div>
        <div style="margin-top:10px;display:flex;flex-direction:column;gap:8px">
          <a class="link" href="${national}" target="_blank" rel="noopener">Open National Cyber Crime Reporting Portal (cybercrime.gov.in)</a>
          <a class="link" href="${i4c}" target="_blank" rel="noopener">I4C (MHA) — State/UT Nodal Officers listing</a>
          <a class="link" href="${meity}" target="_blank" rel="noopener">MEITY nodal officers PDF (official)</a>
        </div>
        <div style="margin-top:8px;font-size:12px;color:var(--muted)">Note: We link to the official portals to ensure you see the latest contact details. For quick reporting, you can also call helpline <strong>1930</strong> or emergency <strong>112</strong>.</div>
      `;
      document.getElementById('stateContact').innerHTML = html;
      document.getElementById('stateContact').scrollIntoView({behavior:'smooth'});
    }

    // -----------------------------
    // FRAUD SIMULATION LOGIC
    // -----------------------------
    const scenarios = [
      {
        id: 1,
        title: 'OTP Scam — “Bank blocked your account”',
        text: `You receive a call from someone claiming to be from your bank. They say your account is blocked and ask you to share the OTP sent to your phone to 'unblock' it immediately.`,
        options: [
          { key: 'A', text: 'Share the OTP — you must help them verify.' },
          { key: 'B', text: 'Hang up and call your bank using the official number on the back of your card or bank website.' },
          { key: 'C', text: 'Follow caller instructions and log in to your internet banking from the provided link.' }
        ],
        correct: 'B',
        explanation: 'Banks never ask for OTPs or passwords over phone. If in doubt, hang up and call the bank using an official number from their website or your bank card.'
      },
      {
        id: 2,
        title: 'Investment Scam — “Guaranteed 30% per month”',
        text: `A caller (or message) promises unusually high returns (e.g., 30% per month) and asks you to transfer money to a personal UPI/ bank account to join a 'high-return program.'`,
        options: [
          { key: 'A', text: 'Transfer a small amount first to test the system.' },
          { key: 'B', text: 'Research the offer, check regulatory registration, and avoid sending money to unknown personal accounts.' },
          { key: 'C', text: 'Install the recommended trading app immediately and provide KYC details.' }
        ],
        correct: 'B',
        explanation: 'Unrealistic returns and pressure to pay into personal accounts are classic red flags. Verify regulation, reviews, and never transfer to unknown personal accounts.'
      },
      {
        id: 3,
        title: 'Tech Support Scam — remote access request',
        text: `Caller claims to be from 'Microsoft support' and says your computer is infected. They ask you to install remote-access software and share the access code so they can 'fix' it.`,
        options: [
          { key: 'A', text: 'Install the tool and share the code so they can fix it.' },
          { key: 'B', text: 'Refuse remote access, hang up, and contact official support channels if needed.' },
          { key: 'C', text: 'Give them your username and password instead for faster help.' }
        ],
        correct: 'B',
        explanation: 'Never give remote access or credentials to unknown callers. Use official vendor support pages and contact them directly if you suspect a problem.'
      },
      {
        id: 4,
        title: 'Job Offer / Fee Scam',
        text: `You get a call offering a high-paying job but they ask for an upfront 'processing fee' to be paid to secure the position.`,
        options: [
          { key: 'A', text: 'Pay the fee to secure the job quickly.' },
          { key: 'B', text: 'Ask for a written offer, company email, and verify via the company’s official HR contacts.' },
          { key: 'C', text: 'Share your bank details to receive salary advance.' }
        ],
        correct: 'B',
        explanation: 'Legitimate employers do not ask for upfront fees. Always request written offers and verify via official company channels before paying anything.'
      },
      {
        id: 5,
        title: 'Prize / Lottery — tax fee asked via link',
        text: `You receive a message saying you won a prize and to claim it you need to pay a small 'tax' via the link provided or share your bank details.`,
        options: [
          { key: 'A', text: 'Click the link and pay the fee to claim the prize.' },
          { key: 'B', text: 'Ignore the message and verify with the official organization or the National Consumer helpline.' },
          { key: 'C', text: 'Call the number in the message and negotiate lower fee.' }
        ],
        correct: 'B',
        explanation: 'Unexpected prize messages asking for money are scams. Do not click links or pay. Verify through official channels or ignore.'
      }
    ];

    let simIndex = 0;
    let simScore = 0;
    let simStarted = false;
    let selectedOption = null;

    function startSimulation(){
      if(!simStarted){
        simStarted = true;
        simIndex = 0;
        simScore = 0;
      }
      renderScenario(simIndex);
      // hide main grid and videos
      document.getElementById('mainGrid').style.display = 'none';
      document.getElementById('panel-sim').style.display = 'block';
      // show simulation tab active
      document.getElementById('tab-sim').classList.add('active');
      window.scrollTo({top:0, behavior:'smooth'});
    }

    function resetSimulation(){
      simStarted = false;
      simIndex = 0;
      simScore = 0;
      selectedOption = null;
      document.getElementById('simContent').innerHTML = `<div class="muted">Click <strong>Start</strong> to begin the scenarios. For each scenario, choose the best response and click <strong>Submit</strong> to see explanation.</div>`;
      // show check tab by default
      showTab('check');
    }

    function renderScenario(i){
      const s = scenarios[i];
      if(!s) return;
      selectedOption = null;
      let html = `<div style="display:flex;justify-content:space-between;align-items:center">
                    <div>
                      <div class="sim-question">Scenario ${i+1}: ${s.title}</div>
                      <div class="muted" style="margin-bottom:8px">${s.text}</div>
                    </div>
                    <div style="text-align:right"><div class="small">Progress: ${i+1}/${scenarios.length}</div><div style="margin-top:6px" class="small muted">Score: ${simScore}</div></div>
                  </div>
                  <div style="margin-top:12px">`;
      s.options.forEach(opt => {
        html += `<div class="sim-option" id="opt-${opt.key}" onclick="selectOption('${opt.key}')">
                   <strong style="margin-right:10px">${opt.key}.</strong> ${opt.text}
                 </div>`;
      });
      html += `</div>
               <div style="margin-top:12px;display:flex;gap:8px;align-items:center">
                 <button class="btn primary" onclick="submitAnswer()">Submit</button>
                 <button class="btn ghost" onclick="showExplanation()">Show Explanation</button>
                 <button class="btn" onclick="nextScenario()" style="margin-left:auto">Next</button>
               </div>
               <div id="simFeedback" style="margin-top:12px"></div>`;
      document.getElementById('simContent').innerHTML = html;
      document.getElementById('panel-sim').scrollIntoView({behavior:'smooth'});
    }

    function selectOption(key){
      // clear previous selected styling
      scenarios[simIndex].options.forEach(o => {
        const el = document.getElementById('opt-'+o.key);
        if(el) el.classList.remove('selected');
      });
      const el = document.getElementById('opt-'+key);
      if(el) el.classList.add('selected');
      selectedOption = key;
      // clear feedback
      document.getElementById('simFeedback').innerHTML = '';
    }

    function submitAnswer(){
      if(!selectedOption){
        document.getElementById('simFeedback').innerHTML = `<div class="sim-feedback" style="border-left:4px solid #f59e0b">Please select an option first.</div>`;
        return;
      }
      const s = scenarios[simIndex];
      const correct = s.correct;
      if(selectedOption === correct){
        simScore++;
        document.getElementById('simFeedback').innerHTML = `<div class="sim-feedback" style="border-left:4px solid var(--success)"><strong>Correct.</strong> ${s.explanation}</div>`;
      } else {
        document.getElementById('simFeedback').innerHTML = `<div class="sim-feedback" style="border-left:4px solid var(--danger)"><strong>Incorrect.</strong> ${s.explanation}</div>`;
      }
    }

    function showExplanation(){
      const s = scenarios[simIndex];
      document.getElementById('simFeedback').innerHTML = `<div class="sim-feedback"><strong>Explanation:</strong> ${s.explanation}</div>`;
    }

    function nextScenario(){
      if(simIndex < scenarios.length - 1){
        simIndex++;
        selectedOption = null;
        renderScenario(simIndex);
      } else {
        // finished
        document.getElementById('simContent').innerHTML = `<div style="text-align:center">
          <h3>Simulation complete</h3>
          <p class="muted">You scored <strong>${simScore}</strong> out of <strong>${scenarios.length}</strong>.</p>
          <p class="muted">Review scenarios again to improve your score, or click Reset to start over.</p>
          <div style="margin-top:12px;display:flex;gap:8px;justify-content:center">
            <button class="btn primary" onclick="resetSimulation()">Reset Simulation</button>
            <button class="btn ghost" onclick="renderScenario(0)">Review from start</button>
            <button class="btn" onclick="showTab('check')">Back to Check Call</button>
          </div>
        </div>`;
      }
    }

    // init: show check tab
    showTab('check');
  </script>
</body>
</html>
