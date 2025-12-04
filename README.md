<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Months of the Year – Practice Games</title>
  <style>
    * { box-sizing: border-box; font-family: "Comic Sans MS", system-ui, sans-serif; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0; padding: 0;
      background: linear-gradient(135deg, #ffefd5, #e0f7fa);
      color: #333;
    }

    header { text-align: center; padding: 20px 10px 10px; }
    h1 { margin: 0; font-size: 2.4rem; color: #2e7d32; text-shadow: 1px 1px 0 #fff; }
    .subtitle { margin-top: 8px; font-size: 1.1rem; }

    .container { max-width: 900px; margin: 0 auto 40px; padding: 0 15px 30px; }

    .game-menu {
      margin: 15px auto 30px; padding: 15px;
      border-radius: 12px; background: rgba(255,255,255,0.9);
      display: flex; flex-wrap: wrap; justify-content: center; gap: 10px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.15);
    }
    .game-menu button {
      border: none; border-radius: 20px; padding: 8px 15px;
      font-size: 0.95rem; cursor: pointer; background: #ffb74d;
      transition: transform 0.1s, box-shadow 0.1s, background 0.2s;
    }
    .game-menu button:hover {
      transform: translateY(-1px); box-shadow: 0 3px 6px rgba(0,0,0,0.2);
      background: #ffa726;
    }

    .game-section {
      margin-bottom: 30px; padding: 20px;
      border-radius: 16px; background: rgba(255,255,255,0.95);
      box-shadow: 0 3px 8px rgba(0,0,0,0.18);
    }
    .game-section h2 { margin-top: 0; font-size: 1.5rem; color: #1565c0; }
    .game-description { margin-bottom: 15px; font-size: 0.98rem; }

    .btn {
      border: none; border-radius: 18px; padding: 8px 14px;
      font-size: 0.95rem; cursor: pointer; margin: 5px 4px;
      transition: transform 0.1s, box-shadow 0.1s, background 0.2s;
    }
    .btn-primary { background: #42a5f5; color: #fff; }
    .btn-primary:hover { background: #1e88e5; transform: translateY(-1px); }

    .btn-secondary { background: #ab47bc; color: #fff; }
    .btn-secondary:hover { background: #8e24aa; }

    .feedback { margin-top: 10px; min-height: 20px; font-weight: bold; }
    .correct { color: #2e7d32; }
    .incorrect { color: #c62828; }

    .g1-option-btn { background: #fff59d; }
    .g1-option-btn:hover { background: #fff176; }

    .g2-list { list-style: none; padding: 0; margin: 10px 0 15px; }
    .g2-list li {
      background: #bbdefb; margin-bottom: 6px; padding: 8px 10px;
      border-radius: 10px; cursor: pointer; border: 2px solid transparent;
      display: flex; align-items: center; justify-content: space-between;
    }
    .g2-list li.selected { border-color: #f9a825; background: #fff8e1; }
    .g2-list li.correct-order { border-color: #2e7d32; }
    .g2-list li.wrong-order { border-color: #c62828; }

    .g3-sentence { margin-bottom: 10px; padding: 8px; border-radius: 10px; background: #e1f5fe; }
    .g3-input {
      padding: 4px 6px; border-radius: 6px; border: 2px solid #90caf9;
      min-width: 120px; font-size: 0.95rem;
    }

    .g4-grid {
      display: grid; grid-template-columns: 1fr 1fr; gap: 6px 10px; margin-bottom: 10px;
    }
    .g4-select {
      width: 100%; padding: 4px 6px; border-radius: 8px;
      border: 2px solid #ce93d8; font-size: 0.95rem;
    }

    @media(max-width:600px){ .g4-grid{ grid-template-columns: 1fr; } }
  </style>
</head>
<body>

<a id="top"></a>
<header>
  <h1>Months of the Year – Practice Games</h1>
  <p class="subtitle">Click a game below and practice the months!</p>
</header>

<div class="container">
  <nav class="game-menu">
    <button onclick="document.getElementById('game1').scrollIntoView()">Game 1 – Italian to English</button>
    <button onclick="document.getElementById('game2').scrollIntoView()">Game 2 – Put in Order</button>
    <button onclick="document.getElementById('game3').scrollIntoView()">Game 3 – Fill in the Blanks</button>
    <button onclick="document.getElementById('game4').scrollIntoView()">Game 4 – Match Translations</button>
  </nav>

  <!-- GAME 1 -->
  <section id="game1" class="game-section">
    <h2>Game 1 – Multiple Choice from Italian to English</h2>
    <p class="game-description">Guarda il mese in italiano e scegli il mese giusto in inglese!</p>

    <div id="g1-question"></div>
    <div id="g1-options" class="g1-options"></div>
    <div id="g1-feedback" class="feedback"></div>
    <button class="btn btn-primary" id="g1-next">Next month ➜</button>

    <p class="back-top"><a href="#top">⬆ Back to top</a></p>
  </section>

  <!-- GAME 2 -->
  <section id="game2" class="game-section">
    <h2>Game 2 – Put the Months in Order</h2>
    <p class="game-description">Click two months to swap them. Put the months from January to December!</p>

    <ul id="g2-list" class="g2-list"></ul>
    <button class="btn btn-primary" id="g2-check">Check order</button>
    <button class="btn btn-secondary" id="g2-reset">Shuffle / Reset</button>
    <div id="g2-feedback" class="feedback"></div>

    <p class="back-top"><a href="#top">⬆ Back to top</a></p>
  </section>

  <!-- GAME 3 -->
  <section id="game3" class="game-section">
    <h2>Game 3 – Fill in the Blanks</h2>
    <p class="game-description">Write the correct month in each blank!</p>

    <div id="g3-area">
      <div class="g3-sentence">1) The first month of the year is <input class="g3-input" data-answer="January">.</div>
      <div class="g3-sentence">2) Ferragosto is in <input class="g3-input" data-answer="August">.</div>
      <div class="g3-sentence">3) Christmas is in <input class="g3-input" data-answer="December">.</div>
      <div class="g3-sentence">4) My birthday is in <input class="g3-input" data-answer="March">.</div>
      <div class="g3-sentence">5) The month after April is <input class="g3-input" data-answer="May">.</div>
      <div class="g3-sentence">6) The month before October is <input class="g3-input" data-answer="September">.</div>
      <div class="g3-sentence">7) Summer starts in <input class="g3-input" data-answer="June">.</div>
    </div>

    <button class="btn btn-primary" id="g3-check">Check answers</button>
    <button class="btn btn-secondary" id="g3-clear">Clear all</button>
    <div id="g3-feedback" class="feedback"></div>

    <p class="back-top"><a href="#top">⬆ Back to top</a></p>
  </section>

  <!-- GAME 4 -->
  <section id="game4" class="game-section">
    <h2>Game 4 – Match English to Italian</h2>
    <p class="game-description">Abbina ogni mese alla traduzione italiana corretta!</p>

    <div id="g4-grid" class="g4-grid"></div>

    <button class="btn btn-primary" id="g4-check">Check matches</button>
    <button class="btn btn-secondary" id="g4-reset">Reset choices</button>
    <div id="g4-feedback" class="feedback"></div>

    <p class="back-top"><a href="#top">⬆ Back to top</a></p>
  </section>
</div>

<script>
/* DATA */
const engMonths = [
  "January","February","March","April","May","June",
  "July","August","September","October","November","December"
];
const itaMonths = [
  "Gennaio","Febbraio","Marzo","Aprile","Maggio","Giugno",
  "Luglio","Agosto","Settembre","Ottobre","Novembre","Dicembre"
];

function shuffle(arr){
  const a = arr.slice();
  for(let i=a.length-1;i>0;i--){
    const j=Math.floor(Math.random()*(i+1));
    [a[i],a[j]]=[a[j],a[i]];
  }
  return a;
}

/* GAME 1 */
(function(){
  const q = document.getElementById("g1-question");
  const opts = document.getElementById("g1-options");
  const f = document.getElementById("g1-feedback");
  const next = document.getElementById("g1-next");

  let correct = null;

  function newQuestion(){
    f.textContent = "";
    opts.innerHTML = "";
    const index = Math.floor(Math.random()*12);
    const ita = itaMonths[index];
    correct = engMonths[index];
    q.innerHTML = `<strong>Italian:</strong> ${ita} ➜ ?`;

    let choices = shuffle(engMonths.filter(m=>m!=correct)).slice(0,3);
    choices.push(correct);
    choices = shuffle(choices);

    choices.forEach(choice=>{
      const b = document.createElement("button");
      b.className="btn g1-option-btn";
      b.textContent = choice;
      b.onclick = ()=>{
        if(choice===correct){
          f.textContent="Correct! 😊"; f.className="feedback correct";
        } else {
          f.textContent="Try again! 😅"; f.className="feedback incorrect";
        }
      };
      opts.appendChild(b);
    });
  }
  next.onclick = newQuestion;
  newQuestion();
})();

/* GAME 2 */
(function(){
  const listEl = document.getElementById("g2-list");
  const check = document.getElementById("g2-check");
  const reset = document.getElementById("g2-reset");
  const feedback = document.getElementById("g2-feedback");

  let selectedIndex = null;

  function build(){
    listEl.innerHTML = "";
    feedback.textContent = "";
    const shuffled = shuffle(engMonths);
    shuffled.forEach(m=>{
      const li=document.createElement("li");
      li.textContent=m;
      li.dataset.month = m;
      li.onclick=()=>select(li);
      listEl.appendChild(li);
    });
  }

  function select(li){
    const items = [...listEl.children];
    const index = items.indexOf(li);

    if(selectedIndex===null){
      selectedIndex=index;
      li.classList.add("selected");
    } else if(selectedIndex===index){
      li.classList.remove("selected");
      selectedIndex=null;
    } else {
      const first = items[selectedIndex];
      const temp = first.dataset.month;
      first.dataset.month = li.dataset.month;
      li.dataset.month = temp;
      first.textContent = first.dataset.month;
      li.textContent = li.dataset.month;
      first.classList.remove("selected");
      selectedIndex=null;
    }
  }

  check.onclick = ()=>{
    const items=[...listEl.children];
    let all=true;
    items.forEach((li,i)=>{
      li.classList.remove("correct-order","wrong-order","selected");
      if(li.dataset.month===engMonths[i]){
        li.classList.add("correct-order");
      } else {
        li.classList.add("wrong-order");
        all=false;
      }
    });
    if(all){
      feedback.textContent="Perfect order! 🎉"; feedback.className="feedback correct";
    } else {
      feedback.textContent="Not yet, try again!"; feedback.className="feedback incorrect";
    }
  };

  reset.onclick = build;
  build();
})();

/* GAME 3 */
(function(){
  const inputs = document.querySelectorAll(".g3-input");
  const check = document.getElementById("g3-check");
  const clear = document.getElementById("g3-clear");
  const feedback = document.getElementById("g3-feedback");

  check.onclick = ()=>{
    let correct=0;
    inputs.forEach(inp=>{
      const ans=inp.dataset.answer.toLowerCase();
      const val=inp.value.trim().toLowerCase();
      if(val===ans){
        inp.style.borderColor="#2e7d32";
        inp.style.background="#c8e6c9";
        correct++;
      } else {
        inp.style.borderColor="#c62828";
        inp.style.background="#ffcdd2";
      }
    });
    if(correct===inputs.length){
      feedback.textContent="All correct! 🎉"; feedback.className="feedback correct";
    } else {
      feedback.textContent=`You got ${correct}/${inputs.length}. Keep practicing!`;
      feedback.className="feedback incorrect";
    }
  };

  clear.onclick = ()=>{
    inputs.forEach(inp=>{
      inp.value="";
      inp.style.borderColor="#90caf9";
      inp.style.background="white";
    });
    feedback.textContent="";
  };
})();

/* GAME 4 */
(function(){
  const grid = document.getElementById("g4-grid");
  const check = document.getElementById("g4-check");
  const reset = document.getElementById("g4-reset");
  const fb = document.getElementById("g4-feedback");

  engMonths.forEach((m,i)=>{
    const div1=document.createElement("div");
    div1.textContent=m;

    const div2=document.createElement("div");
    const sel=document.createElement("select");
    sel.className="g4-select";
    sel.dataset.answer=itaMonths[i];

    sel.innerHTML = `<option value="">-- choose --</option>` +
      itaMonths.map(it=>`<option>${it}</option>`).join("");

    div2.appendChild(sel);
    grid.appendChild(div1);
    grid.appendChild(div2);
  });

  check.onclick=()=>{
    const selects=document.querySelectorAll(".g4-select");
    let correct=0;
    selects.forEach(s=>{
      if(s.value===s.dataset.answer){
        s.style.borderColor="#2e7d32";
        s.style.background="#c8e6c9";
        correct++;
      } else {
        s.style.borderColor="#c62828";
        s.style.background="#ffcdd2";
      }
    });
    if(correct===12){
      fb.textContent="All 12 correct! 🎉"; fb.className="feedback correct";
    } else {
      fb.textContent=`You matched ${correct}/12. Try again!`; fb.className="feedback incorrect";
    }
  };

  reset.onclick=()=>{
    document.querySelectorAll(".g4-select").forEach(s=>{
      s.value="";
      s.style.borderColor="#ce93d8";
      s.style.background="white";
    });
    fb.textContent="";
  };
})();
</script>

</body>
</html>
