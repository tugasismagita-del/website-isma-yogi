<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Tabungan Harian</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #f0f4f8;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      height: 100vh;
      margin: 0;
      padding: 20px;
    }
    .container {
      background: white;
      padding: 25px 30px;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      width: 320px;
    }
    h1 {
      text-align: center;
      color: #333;
      margin-bottom: 20px;
    }
    label {
      display: block;
      margin-bottom: 8px;
      color: #555;
      font-weight: 600;
    }
    input[type="date"], input[type="number"] {
      width: 100%;
      padding: 8px 10px;
      margin-bottom: 15px;
      border: 1.8px solid #ccc;
      border-radius: 5px;
      font-size: 1rem;
      box-sizing: border-box;
      transition: border-color 0.3s;
    }
    input[type="date"]:focus, input[type="number"]:focus {
      border-color: #007bff;
      outline: none;
    }
    button {
      width: 100%;
      padding: 10px 0;
      background-color: #007bff;
      border: none;
      border-radius: 6px;
      color: white;
      font-size: 1.1rem;
      cursor: pointer;
      transition: background-color 0.3s;
      font-weight: 600;
    }
    button:hover {
      background-color: #0056b3;
    }
    .list-tabungan {
      margin-top: 25px;
      max-height: 180px;
      overflow-y: auto;
      border-top: 1.5px solid #ddd;
      padding-top: 15px;
    }
    .item-tabungan {
      display: flex;
      justify-content: space-between;
      padding: 6px 0;
      border-bottom: 1px solid #eee;
      color: #444;
      font-size: 0.95rem;
    }
    .total {
      margin-top: 20px;
      font-size: 1.25rem;
      font-weight: 700;
      color: #007bff;
      text-align: center;
    }
    .no-data {
      text-align: center;
      color: #999;
      font-style: italic;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Tabungan Harian</h1>
    <label for="tanggal">Tanggal</label>
    <input type="date" id="tanggal" />
    <label for="jumlah">Jumlah (Rp)</label>
    <input type="number" id="jumlah" min="0" placeholder="Masukkan jumlah tabungan" />
    <button id="btn-tambah">Tambah Tabungan</button>

    <div class="list-tabungan" id="listTabungan">
      <p class="no-data">Belum ada data tabungan.</p>
    </div>

    <div class="total" id="totalTabungan">Total Tabungan: Rp 0</div>
  </div>

  <script>
    const tanggalInput = document.getElementById('tanggal');
    const jumlahInput = document.getElementById('jumlah');
    const btnTambah = document.getElementById('btn-tambah');
    const listTabungan = document.getElementById('listTabungan');
    const totalTabungan = document.getElementById('totalTabungan');

    let tabungan = [];

    // Format angka ke Rupiah (misal Rp 1.000.000)
    function formatRupiah(angka) {
      return 'Rp ' + angka.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    }

    function tampilkanData() {
      if (tabungan.length === 0) {
        listTabungan.innerHTML = '<p class="no-data">Belum ada data tabungan.</p>';
        totalTabungan.textContent = 'Total Tabungan: Rp 0';
        return;
      }
      // Urutkan data berdasarkan tanggal
      tabungan.sort((a,b) => new Date(a.tanggal) - new Date(b.tanggal));

      let html = '';
      let total = 0;
      tabungan.forEach(item => {
        html += `
          <div class="item-tabungan">
            <div>${item.tanggal}</div>
            <div>${formatRupiah(item.jumlah)}</div>
          </div>
        `;
        total += item.jumlah;
      });

      listTabungan.innerHTML = html;
      totalTabungan.textContent = 'Total Tabungan: ' + formatRupiah(total);
    }

    btnTambah.addEventListener('click', () => {
      const tanggal = tanggalInput.value;
      const jumlah = parseInt(jumlahInput.value);

      if (!tanggal) {
        alert('Silakan pilih tanggal.');
        return;
      }
      if (isNaN(jumlah) || jumlah <= 0) {
        alert('Jumlah tabungan harus lebih dari 0.');
        return;
      }

      tabungan.push({ tanggal, jumlah });

      // Reset input
      tanggalInput.value = '';
      jumlahInput.value = '';

      tampilkanData();
    });

    // Inisialisasi tampilan awal
    tampilkanData();
  </script>
</body>
</html>
