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

body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background-image: url('https://images.unsplash.com/photo-1476158085676-f2d8d8f2dcd3?auto=format&fit=crop&w=1950&q=80');
  background-size: cover;
  background-position: center;
  color: #fff;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  background-color: rgba(0, 0, 0, 0.6);
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 20px rgba(255,255,255,0.3);
  width: 350px;
  text-align: center;
}

h1 {
  margin-bottom: 20px;
}

input, button {
  width: 100%;
  padding: 10px;
  margin-top: 10px;
  border-radius: 8px;
  border: none;
  font-size: 14px;
}

input {
  background-color: #eee;
}

button {
  background-color: #3F51B5;
  color: white;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #5C6BC0;
}

#status {
  margin-top: 15px;
  font-size: 14px;
}
document.getElementById("data-form").addEventListener("submit", function (e) {
  e.preventDefault();

  const game = document.getElementById("game").value;
  const khunggio = document.getElementById("khunggio").value;
  const cuoc = document.getElementById("cuoc").value;
  const ketqua = document.getElementById("ketqua").value;

  const statusEl = document.getElementById("status");
  statusEl.textContent = "⏳ Đang gửi dữ liệu...";

  fetch("https://script.google.com/macros/s/AKfycbxHoAd49LIqYaACMu2WOL1AwmawTEGwtbf5TEZOb08xKMIBo_e8Tklq1MxiI-KQxO6EqQ/exec", {
    method: "POST",
    mode: "no-cors",
    headers: {
      "Content-Type": "application/x-www-form-urlencoded",
    },
    body: `game=${game}&khunggio=${khunggio}&cuoc=${cuoc}&ketqua=${ketqua}`,
  })
    .then(() => {
      statusEl.textContent = "✅ Gửi thành công!";
      document.getElementById("data-form").reset();
    })
    .catch(() => {
      statusEl.textContent = "❌ Gửi thất bại!";
    });
});
