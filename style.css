const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
const scoreDisplay = document.getElementById('score');
const statusDisplay = document.getElementById('status');
const tile = 32;
let map = [
  [1,1,1,1,1,1,1,1,1,1],
  [1,0,0,0,0,0,3,0,0,1],
  [1,0,2,1,0,0,0,0,0,1],
  [1,0,0,1,4,0,0,3,0,1],
  [1,0,0,0,0,0,0,0,0,1],
  [1,1,1,1,1,1,1,1,1,1]
];
let player = { x: 4, y: 3 };
let score = 0;
function drawMap() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  for (let y = 0; y < map.length; y++) {
    for (let x = 0; x < map[y].length; x++) {
      switch(map[y][x]) {
        case 1:
          ctx.fillStyle = '#555'; 
          ctx.fillRect(x*tile, y*tile, tile-2, tile-2);
          break;
        case 2:
          ctx.fillStyle = '#c09300'; 
          ctx.fillRect(x*tile+4, y*tile+4, tile-8, tile-8);
          break;
        case 3:
          ctx.fillStyle = '#0077ff'; 
          ctx.fillRect(x*tile+6, y*tile+6, tile-12, tile-12);
          break;
        case 4:
          ctx.fillStyle = '#00cc44'; 
          ctx.beginPath();
          ctx.arc(x*tile + tile/2, y*tile + tile/2, tile/3, 0, Math.PI*2);
          ctx.fill();
          break;
        default:
          ctx.fillStyle = '#111'; 
          ctx.fillRect(x*tile, y*tile, tile-2, tile-2);
      }
    }
  }
}

function movePlayer(dx, dy) {
  let nx = player.x + dx;
  let ny = player.y + dy;
  let nextCell = map[ny][nx];
  if (nextCell === 1) return; 
  if (nextCell === 2) {
    let nx2 = nx + dx;
    let ny2 = ny + dy;
    let beyond = map[ny2] && map[ny2][nx2];
    if (beyond === 0 || beyond === 3) {
      map[ny2][nx2] = 2;
      map[ny][nx] = 4;
      map[player.y][player.x] = 0;
      player.x = nx;
      player.y = ny;
      score += 1;
      scoreDisplay.textContent = score;
    }
  } else if (nextCell === 0 || nextCell === 3) {
    map[player.y][player.x] = 0;
    map[ny][nx] = 4;
    player.x = nx;
    player.y = ny;
  }
  checkWin();
  drawMap();
}
function checkWin() {
  let goalsRemaining = 0;
  for (let y = 0; y < map.length; y++) {
    for (let x = 0; x < map[y].length; x++) {
      if (map[y][x] === 3) goalsRemaining++;
    }
  }
  if (goalsRemaining === 0) {
    statusDisplay.textContent = ' Bạn đã thắng ';
  }
}
window.addEventListener('keydown', (e) => {
  switch(e.key) {
    case 'ArrowUp': movePlayer(0, -1); break;
    case 'ArrowDown': movePlayer(0, 1); break;
    case 'ArrowLeft': movePlayer(-1, 0); break;
    case 'ArrowRight': movePlayer(1, 0); break;
  }
});
drawMap();