# test1
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>擦擦卡遊戲</title>
<style>
  body {
    font-family: Arial, sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    background-color: #f0f0f0;
  }
  canvas {
    border: 1px solid #000;
  }
</style>
</head>
<body>
  <canvas id="scratchcard" width="300" height="200"></canvas>
  <script>
    // 在此處添加JavaScript代碼
  </script>
</body>
</html>
接下來，我們使用JavaScript編寫擦擦卡遊戲的邏輯：

const canvas = document.getElementById('scratchcard');
const ctx = canvas.getContext('2d');

// 初始化畫布
ctx.fillStyle = '#999';
ctx.fillRect(0, 0, canvas.width, canvas.height);
ctx.font = '48px serif';
ctx.fillStyle = '#f00';
ctx.fillText('獎品', 90, 100);

// 
ctx.globalCompositeOperation = 'destination-out';

let isDrawing = false;

// 
canvas.addEventListener('mousedown', (e) => {
  isDrawing = true;
  ctx.beginPath();
  ctx.moveTo(e.clientX - canvas.offsetLeft, e.clientY - canvas.offsetTop);
});

// 
canvas.addEventListener('mousemove', (e) => {
  if (!isDrawing) return;
  ctx.lineTo(e.clientX - canvas.offsetLeft, e.clientY - canvas.offsetTop);
  ctx.lineWidth = 20;
  ctx.lineCap = 'round';
  ctx.stroke();
});

// 
canvas.addEventListener('mouseup', () => {
  isDrawing = false;
});
