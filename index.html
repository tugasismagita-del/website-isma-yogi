<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tabungan Harian Sederhana</title>
<style>
  body { font-family: Arial, sans-serif; margin: 20px; background: #f5f5f5; }
  h1 { text-align: center; }
  .container { background: white; padding: 20px; border-radius: 8px; max-width: 500px; margin: auto; }
  label, input, button { display: block; width: 100%; margin-bottom: 10px; }
  input, button { padding: 8px; }
  table { width: 100%; border-collapse: collapse; margin-top: 10px; }
  th, td { border: 1px solid #ccc; padding: 6px; text-align: left; }
  th { background: #eee; }
</style>
</head>
<body>
<div class="container">
  <h1>Tabungan Harian</h1>
  <label for="tanggal">Tanggal:</label>
  <input type="date" id="tanggal">

  <label for="jumlah">Jumlah (Rp):</label>
  <input type="number" id="jumlah" placeholder="Masukkan jumlah tabungan">

  <button onclick="tambahTabungan()">Tambah</button>

  <h3>Daftar Tabungan</h3>
  <table id="tabel">
    <tr><th>Tanggal</th><th>Jumlah (Rp)</th></tr>
  </table>

  <h3>Total: <span id="total">0</span></h3>
</div>

<script>
  let data = JSON.parse(localStorage.getItem('tabungan')) || [];
  
  function tampilkan() {
    const tabel = document.getElementById('tabel');
    let total = 0;
    tabel.innerHTML = '<tr><th>Tanggal</th><th>Jumlah (Rp)</th></tr>';
    data.forEach(d => {
      tabel.innerHTML += <tr><td>${d.tanggal}</td><td>${d.jumlah}</td></tr>;
      total += Number(d.jumlah);
    });
    document.getElementById('total').textContent = total;
  }

  function tambahTabungan() {
    const tanggal = document.getElementById('tanggal').value;
    const jumlah = document.getElementById('jumlah').value;
    if (!tanggal || !jumlah) return alert('Isi semua data!');
    data.push({ tanggal, jumlah });
    localStorage.setItem('tabungan', JSON.stringify(data));
    document.getElementById('jumlah').value = '';
    tampilkan();
  }

  tampilkan();
</script>
</body>
</html>
