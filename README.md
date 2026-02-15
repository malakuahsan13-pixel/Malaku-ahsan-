# Malaku-ahsan-
Belajar EAC 
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta charset="UTF-8">
<title>Kelas Realistis</title>

<style>
body{
margin:0;
font-family:Arial;
background:#dbeafe;
}

/* Header */
header{
background:#1e293b;
color:blue;
padding:15px;
text-align:center;
font-size:20px;
}

/* Ruang kelas */
.classroom{
padding:20px;
}

/* Papan tulis */
.board{
background:#14532d;
color:yellow;
padding:20px;
border-radius:10px;
margin-bottom:20px;
box-shadow:0 5px 15px rgba(0,0,0,0.3);
}

/* Meja kursi */
.desks{
display:grid;
grid-template-columns:repeat(4,1fr);
gap:10px;
margin-bottom:20px;
}

.desk{
background:#92400e;
height:60px;
border-radius:5px;
position:relative;
}

.desk:after{
content:"";
position:absolute;
bottom:-10px;
left:20%;
width:60%;
height:10px;
background:#78350f;
}

/* Section */
.section{
background:white;
padding:15px;
border-radius:10px;
margin-bottom:20px;
}

input{
width:100%;
padding:8px;
margin-bottom:8px;
}

button{
padding:8px;
border:none;
border-radius:6px;
background:#0ea5e9;
color:white;
width:100%;
margin-top:5px;
cursor:pointer;
}

ul{
list-style:none;
padding:0;
}

li{
background:#f1f5f9;
padding:8px;
margin-top:5px;
border-radius:6px;
display:flex;
justify-content:space-between;
align-items:center;
}

.rekap{
background:#e0f2fe;
padding:10px;
border-radius:8px;
margin-top:10px;
}
</style>
</head>

<body>

<header>🏫 RUANG KELAS REALISTIS</header>

<div class="classroom">

<div class="board">
<h3>📋 Papan Tulis</h3>
<p id="papan">Hari ini belajar JavaScript!</p>
<input id="inputPapan" placeholder="Tulis di papan...">
<button onclick="ubahPapan()">Ubah Tulisan</button>
</div>

<!-- Meja kursi -->
<div class="desks">
<div class="desk"></div>
<div class="desk"></div>
<div class="desk"></div>
<div class="desk"></div>
<div class="desk"></div>
<div class="desk"></div>
<div class="desk"></div>
<div class="desk"></div>
</div>

<div class="section">
<h3>👨‍🏫 Absen Guru</h3>
<input id="guruInput" placeholder="Nama Guru">
<button onclick="tambahGuru()">Tambah Guru</button>
<ul id="guruList"></ul>
<div class="rekap">
Total Guru Hadir: <span id="rekapGuru">0</span>
</div>
</div>

<div class="section">
<h3>👨‍🎓 Absen Murid</h3>
<input id="muridInput" placeholder="Nama Murid">
<button onclick="tambahMurid()">Tambah Murid</button>
<ul id="muridList"></ul>
<div class="rekap">
Total Murid Hadir: <span id="rekapMurid">0</span>
</div>
</div>

</div>

<script>
let guru=[];
let murid=[];

/* PAPAN */
function ubahPapan(){
let text=document.getElementById("inputPapan").value;
if(text!=""){
document.getElementById("papan").innerText=text;
document.getElementById("inputPapan").value="";
}
}

/* TAMBAH */
function tambahGuru(){
let nama=document.getElementById("guruInput").value;
if(nama!=""){
guru.push({nama:nama,hadir:false});
document.getElementById("guruInput").value="";
render();
}
}

function tambahMurid(){
let nama=document.getElementById("muridInput").value;
if(nama!=""){
murid.push({nama:nama,hadir:false});
document.getElementById("muridInput").value="";
render();
}
}

/* TOGGLE */
function toggleGuru(i){
guru[i].hadir=!guru[i].hadir;
render();
}

function toggleMurid(i){
murid[i].hadir=!murid[i].hadir;
render();
}

/* RENDER */
function render(){
let gList=document.getElementById("guruList");
gList.innerHTML="";
let hadirGuru=0;

guru.forEach((g,i)=>{
if(g.hadir) hadirGuru++;
gList.innerHTML+=`
<li>${g.nama}
<button onclick="toggleGuru(${i})">
${g.hadir?"Hadir ✅":"Tidak ❌"}
</button></li>`;
});

document.getElementById("rekapGuru").innerText=hadirGuru;

let mList=document.getElementById("muridList");
mList.innerHTML="";
let hadirMurid=0;

murid.forEach((m,i)=>{
if(m.hadir) hadirMurid++;
mList.innerHTML+=`
<li>${m.nama}
<button onclick="toggleMurid(${i})">
${m.hadir?"Hadir ✅":"Tidak ❌"}
</button></li>`;
});

document.getElementById("rekapMurid").innerText=hadirMurid;
}

render();
</script>

</body>
</html>