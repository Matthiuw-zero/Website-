<!doctype html>
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Galeri Gambar</title>

<style>
body{
    font-family:system-ui;
    padding:2rem;
    background:#f7f7fb;
    color:#222;
}

.card{
    background:#fff;
    padding:1.5rem;
    border-radius:12px;
    box-shadow:0 6px 18px rgba(33,33,33,.06);
    max-width:720px;
    margin:auto;
}

.controls{
    display:flex;
    gap:.5rem;
    margin-bottom:1rem;
}

button{
    background:#0366d6;
    color:white;
    border:0;
    padding:.6rem .9rem;
    border-radius:8px;
    cursor:pointer;
    font-weight:600;
}

button.secondary{
    background:#efefef;
    color:#111;
}

.hidden{
    display:none;
}

img{
    width:100%;
    border-radius:10px;
}

#tip{
    margin-top:15px;
    color:#666;
    font-size:.9rem;
}
</style>
</head>

<body>

<div class="card">

<h1>Selamat Datang</h1>

<p>
Tekan tombol biru untuk melihat gambar dan tombol abu-abu untuk menyalin nomor kontak.
</p>

<div class="controls">
    <button id="toggleBtn">Tampilkan Gambar</button>
    <button id="copyBtn" class="secondary">Salin Nomor</button>
</div>

<div id="imageBox" class="hidden">
    <img src="gambar.jpg" alt="Gambar">
</div>

<p id="tip"></p>

</div>

<script>
const toggleBtn = document.getElementById("toggleBtn");
const imageBox = document.getElementById("imageBox");
const copyBtn = document.getElementById("copyBtn");

toggleBtn.addEventListener("click", () => {
    const hidden = imageBox.classList.toggle("hidden");

    toggleBtn.textContent =
        hidden ? "Tampilkan Gambar" : "Sembunyikan Gambar";
});

copyBtn.addEventListener("click", async () => {
    try{
        await navigator.clipboard.writeText("081234567890");

        copyBtn.textContent = "Nomor Disalin!";

        setTimeout(()=>{
            copyBtn.textContent = "Salin Nomor";
        },1500);

    }catch{
        copyBtn.textContent = "Gagal";
    }
});

const tips = [
    "Terima kasih telah mengunjungi halaman ini.",
    "Jangan lupa simpan nomor kontak kami.",
    "Tekan tombol biru untuk melihat gambar.",
    "Semoga harimu menyenangkan.",
    "Website ini dibuat dengan GitHub Pages."
];

const tipElement = document.getElementById("tip");

function changeTip(){
    const random =
        tips[Math.floor(Math.random() * tips.length)];

    tipElement.textContent = random;
}

changeTip();
setInterval(changeTip, 60000);
</script>

</body>
</html>
