[Звёздный квиз_ Математика созвездий.html](https://github.com/user-attachments/files/33251644/_.html)
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Звёздный квиз: Математика созвездий</title>
<style>
:root{--bg:#0b0e2a;--card:#171b4a;--text:#f2f3ff;--muted:#a9adde;--accent:#ffd34d;--ok:#3ecf8e;--bad:#ff6b7a;--line:#343a86;--star:#fff;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:light){:root:not([data-theme="dark"]){--bg:#e9ecff;--card:#fff;--text:#1a1d4d;--muted:#5b5f99;--accent:#c98a00;--ok:#169b62;--bad:#d6334a;--line:#c9ccf0;--star:#9aa0e0}}
:root[data-theme="light"]{--bg:#e9ecff;--card:#fff;--text:#1a1d4d;--muted:#5b5f99;--accent:#c98a00;--ok:#169b62;--bad:#d6334a;--line:#c9ccf0;--star:#9aa0e0}
:root[data-theme="dark"]{--bg:#0b0e2a;--card:#171b4a;--text:#f2f3ff;--muted:#a9adde;--accent:#ffd34d;--ok:#3ecf8e;--bad:#ff6b7a;--line:#343a86;--star:#fff}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;min-height:100vh;display:flex;justify-content:center;align-items:flex-start;padding:16px;color:var(--text);font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;background-color:var(--bg);
background-image:radial-gradient(1.5px 1.5px at 20% 30%,var(--star),transparent),radial-gradient(1px 1px at 70% 20%,var(--star),transparent),radial-gradient(1.5px 1.5px at 85% 70%,var(--star),transparent),radial-gradient(1px 1px at 35% 80%,var(--star),transparent),radial-gradient(1px 1px at 55% 55%,var(--star),transparent),radial-gradient(1.5px 1.5px at 10% 90%,var(--star),transparent);background-size:300px 300px}
.wrap{width:100%;max-width:580px;margin-top:8px}
.card{background:var(--card);border:1px solid var(--line);border-radius:18px;padding:22px;text-align:center}
.logo{font-size:3.2rem;line-height:1}
h1{font-size:1.5rem;margin:8px 0 6px}
p{margin:6px 0}
.muted{color:var(--muted);font-size:.9rem}
.rules{text-align:left;margin:16px 0;padding:14px 16px;border:1px dashed var(--line);border-radius:12px;font-size:.95rem;line-height:1.6}
.btn{background:var(--accent);color:#1a1530;border:0;border-radius:12px;padding:14px 20px;font-size:1.05rem;font-weight:800;cursor:pointer;width:100%;font-family:inherit;margin-top:8px}
.btn.alt{background:transparent;color:var(--text);border:2px solid var(--line)}
.hud{display:flex;justify-content:space-between;align-items:center;font-weight:700;margin-bottom:10px;font-size:1rem}
.hud span{min-width:0}
.timer{height:8px;background:var(--line);border-radius:4px;overflow:hidden;margin-bottom:16px}
.timer i{display:block;height:100%;width:100%;background:var(--ok);transform-origin:left;transition:background .3s}
.q{font-size:1.15rem;font-weight:700;line-height:1.35;margin:4px 0 16px;text-align:left}
.opt{display:block;width:100%;text-align:left;background:transparent;color:var(--text);border:2px solid var(--line);border-radius:12px;padding:13px 14px;margin-bottom:10px;font-size:1rem;cursor:pointer;font-family:inherit}
.opt:hover:not(:disabled){border-color:var(--accent)}
.opt.ok{border-color:var(--ok);background:color-mix(in srgb,var(--ok) 20%,transparent)}
.opt.bad{border-color:var(--bad);background:color-mix(in srgb,var(--bad) 20%,transparent)}
.fb{text-align:left;min-height:1.4em;margin:4px 0 8px;font-size:.95rem;color:var(--muted)}
.big{font-size:3rem;font-weight:800;color:var(--accent);margin:4px 0}
.hide{display:none}
</style>
</head>
<body>
<div class="wrap">

<div class="card" id="start">
  <div class="logo">🌌</div>
  <h1>Звёздный квиз</h1>
  <p class="muted">Математика созвездий: знаки зодиака на координатной плоскости</p>
  <div class="rules">
    ❤️ 3 жизни: ошибка или конец времени — минус одна<br>
    ⏱ 15 секунд на вопрос: чем быстрее, тем больше очков<br>
    🔥 Серия верных ответов даёт бонус<br>
    🏆 Сыграй 10 вопросов и побей свой рекорд
  </div>
  <div class="muted" id="best"></div>
  <button class="btn" id="go">Играть</button>
  <p class="muted" style="margin-top:14px">По проекту Дияра Әбілхана, 4 «В» класс, Гимназия «БЭСТ»</p>
</div>

<div class="card hide" id="game">
  <div class="hud"><span id="lives"></span><span id="cnt"></span><span id="score"></span></div>
  <div class="timer"><i id="tb"></i></div>
  <p class="q" id="q"></p>
  <div id="opts"></div>
  <div class="fb" id="fb"></div>
  <button class="btn hide" id="next">Дальше</button>
</div>

<div class="card hide" id="end">
  <div class="logo" id="eIcon"></div>
  <h1 id="eTitle"></h1>
  <div class="big" id="eScore"></div>
  <p id="eRank"></p>
  <p class="muted" id="eInfo"></p>
  <p class="muted" id="eBest"></p>
  <button class="btn" id="again">Играть снова</button>
</div>

</div>
<script>
const Q=[
["Кто в 1637 году создал свою систему координат?",["Рене Декарт","Пифагор","Ньютон","Евклид"],0,"Система названа «декартовой» в его честь."],
["Какой буквой по традиции Декарта обозначается «широта» точки?",["y","x","z","a"],1,"Первая координата точки — x."],
["Какой буквой обозначается «долгота» точки?",["x","n","y","k"],2,"Вторая координата точки — y."],
["В каком классе по математике изучают координатную плоскость?",["2 классе","4 классе","6 классе","9 классе"],2,"Эта тема изучается в 6 классе."],
["Сколько всего созвездий украшает ночное небо?",["12","44","88","100"],2,"На небе 88 созвездий."],
["Сколько зодиакальных созвездий лежит на пути Солнца?",["8","12","15","20"],1,"Их двенадцать: от Овна до Рыб."],
["Что по-гречески означает «зодиакос»?",["Небесный путь","Звёздная река","Звериный круг","Круг света"],2,"Большинство названий созвездий — животные."],
["Какой знак связан с золотым руном и страной Колхида?",["Телец","Овен","Козерог","Лев"],1,"Волшебный баран спас Фрикса и Геллу."],
["Какого зверя победил Геракл возле города Немея?",["Рака","Быка","Скорпиона","Льва"],3,"Это Немейский лев — созвездие Лев."],
["Что держит в руках богиня Астрея (созвездие Дева)?",["Весы","Лук","Кувшин","Венок"],0,"Весы — символ правосудия и равенства."],
["В память о каком событии Зевс зажёг созвездие Водолей?",["О войне богов","О Великом потопе","О солнцестоянии","О Немейских играх"],1,"Водолей — человек, льющий воду."],
["Во что превратились Афродита и Эрот, спасаясь от Тифона?",["В птиц","В дельфинов","В рыб","В змей"],2,"Так засияло созвездие Рыбы."],
["Что такое созвездие?",["Одна очень яркая звезда","Скопление ярких звёзд, образующих фигуру","Планета Солнечной системы","След кометы"],1,"Яркие звёзды образуют на небе характерные фигуры."],
["Кто по легенде поместил Скорпиона на небо?",["Афина","Гера","Деметра","Артемида"],1,"Скорпион умертвил охотника Ориона."],
["В какого зверя превратился Зевс, похищая царевну Европу?",["В льва","В орла","В быка","В барана"],2,"Это легенда о созвездии Телец."],
["Кто вскормил молоком маленького Зевса на Крите?",["Коза Амальтея","Корова Ио","Волчица","Львица"],0,"Амальтея стала созвездием Козерог."],
["Как звали братьев из легенды о созвездии Близнецы?",["Кастор и Полидевк","Фрикс и Геракл","Орион и Эет","Несс и Зевс"],0,"Они делят бессмертие: день на Олимпе, день у мёртвых."]
];
const $=id=>document.getElementById(id),TIME=15,N=10;
let qs=[],i=0,score=0,lives=3,streak=0,right=0,locked=false,t0=0,raf=0;
function shuffle(a){a=a.slice();for(let k=a.length-1;k>0;k--){const j=Math.floor(Math.random()*(k+1));[a[k],a[j]]=[a[j],a[k]];}return a;}
function getBest(){try{return +localStorage.getItem("zq_best")||0}catch(e){return 0}}
function setBest(v){try{localStorage.setItem("zq_best",String(v))}catch(e){}}
function show(id){["start","game","end"].forEach(x=>$(x).classList.toggle("hide",x!==id));}
function showBest(){const b=getBest();$("best").textContent=b?"🏆 Твой рекорд: "+b+" очков":"";}
function hud(){$("lives").textContent="❤️".repeat(lives)+"🖤".repeat(3-lives);$("cnt").textContent=(i+1)+" / "+N;$("score").textContent="⭐ "+score;}
function start(){qs=shuffle(Q).slice(0,N);i=0;score=0;lives=3;streak=0;right=0;show("game");render();}
function render(){
  locked=false;const [t,o,c]=qs[i];hud();
  $("q").textContent=t;$("fb").textContent="";$("next").classList.add("hide");$("opts").innerHTML="";
  shuffle(o.map((v,idx)=>({v,idx}))).forEach(({v,idx})=>{
    const b=document.createElement("button");b.className="opt";b.textContent=v;b.dataset.right=idx===c?"1":"";
    b.onclick=()=>answer(b,idx===c);$("opts").appendChild(b);
  });
  t0=performance.now();cancelAnimationFrame(raf);tick();
}
function tick(){
  const left=Math.max(0,TIME-(performance.now()-t0)/1000),bar=$("tb");
  bar.style.transform="scaleX("+(left/TIME)+")";
  bar.style.background=left>8?"var(--ok)":left>4?"var(--accent)":"var(--bad)";
  if(left<=0){answer(null,false,true);return;}
  raf=requestAnimationFrame(tick);
}
function answer(btn,ok,timeout){
  if(locked)return;locked=true;cancelAnimationFrame(raf);
  const left=Math.max(0,TIME-(performance.now()-t0)/1000);
  document.querySelectorAll(".opt").forEach(x=>{x.disabled=true;if(x.dataset.right)x.classList.add("ok");});
  let msg;
  if(ok){
    streak++;right++;const bonus=Math.round(left/TIME*50),sb=(streak-1)*20;
    score+=100+bonus+sb;
    msg="✅ Верно! +"+(100+bonus+sb)+(streak>1?" · серия 🔥"+streak:"")+". "+qs[i][3];
  }else{
    streak=0;lives--;if(btn)btn.classList.add("bad");
    msg=(timeout?"⏱ Время вышло. ":"❌ Неверно. ")+qs[i][3];
  }
  $("fb").textContent=msg;hud();
  $("next").textContent=(lives<=0||i===N-1)?"Результат":"Дальше";
  $("next").classList.remove("hide");
}
function next(){i++;if(lives<=0||i>=N)finish();else render();}
function finish(){
  const win=lives>0&&i>=N,best=getBest(),isNew=score>best;
  if(isNew)setBest(score);
  show("end");
  $("eIcon").textContent=win?"🏆":"💫";
  $("eTitle").textContent=win?"Игра пройдена!":"Жизни закончились";
  $("eScore").textContent=score;
  const rank=right>=9?"Звёздный командир 🚀":right>=7?"Астроном 🔭":right>=4?"Юный звездочёт ⭐":"Начинающий наблюдатель 🌙";
  $("eRank").textContent="Звание: "+rank;
  $("eInfo").textContent="Верных ответов: "+right+" из "+Math.min(i+(win?0:1),N);
  $("eBest").textContent=isNew?"🎉 Новый рекорд!":"🏆 Рекорд: "+best;
}
$("go").onclick=start;$("next").onclick=next;$("again").onclick=()=>{showBest();start();};
showBest();
</script>
</body>
</html>
