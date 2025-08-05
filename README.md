<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Galaxy Tool</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>🌌 Galaxy Nổ Hũ Tracker</h1>
    <form id="data-form">
      <input type="text" id="game" placeholder="Tên game" required />
      <input type="text" id="khunggio" placeholder="Khung giờ" required />
      <input type="number" id="cuoc" placeholder="Tiền cược (VND)" required />
      <input type="text" id="ketqua" placeholder="Kết quả (nổ, trượt...)" required />
      <button type="submit">Gửi dữ liệu</button>
    </form>
    <p id="status"></p>
  </div>

  <script src="script.js"></script>
</body>
</html>

