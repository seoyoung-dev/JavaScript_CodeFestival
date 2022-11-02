## 문제 설명

N\*N의 섬나라 아일랜드의 지도가 격자판의 정보로 주어집니다. 각 섬은 1로 표시되어 상하좌 우와 대각선으로 연결되어 있으며, 0은 바다입니다. 섬나라 아일랜드에 몇 개의 섬이 있는지 구하는 프로그램을 작성하세요.

<br>
<img width="300" alt="detail" src="../src/inf_9-7.png">

<br />
<br />
<br />

## 입력/출력 예제

| 입력  | 출력 |
| ----- | ---- |
| board | 5    |

<br />
<br />

## 내 답안

```js
function solution(board) {
    let answer = 0;
    let queue = [];
    let n = board.length;
    let dx = [-1, -1, 0, 1, 1, 1, 0, -1];
    let dy = [0, 1, 1, 1, 0, -1, -1, -1];

    function BFS(i, j) {
        board[i][j] = 0;
        for (k = 0; k < 8; k++) {
            let nx = i + dx[k];
            let ny = j + dy[k];
            if (nx >= 0 && nx < n && ny >= 0 && ny < n && board[nx][ny] === 1) {
                queue.push([nx, ny]);
                board[nx][ny] = 0;
            }
        }
    }

    for (let i = 0; i < n; i++) {
        for (let j = 0; j < n; j++) {
            if (board[i][j] === 1) {
                BFS(i, j);
                while (queue.length) {
                    let v = queue.shift();
                    BFS(...v);
                }
                answer++;
            }
        }
    }
    return answer;
}

let arr = [
    [1, 1, 0, 0, 0, 1, 0],
    [0, 1, 1, 0, 1, 1, 0],
    [0, 1, 0, 0, 0, 0, 0],
    [0, 0, 0, 1, 0, 1, 1],
    [1, 1, 0, 1, 1, 0, 0],
    [1, 0, 0, 0, 1, 0, 0],
    [1, 0, 1, 0, 1, 0, 0]
];

console.log(solution(arr));
```

<br />
<br />

## 모범답안

```js
function solution(board) {
    let answer = 0;
    let queue = [];
    let n = board.length;
    let dx = [-1, -1, 0, 1, 1, 1, 0, -1];
    let dy = [0, 1, 1, 1, 0, -1, -1, -1];

    for (let i = 0; i < n; i++) {
        for (let j = 0; j < n; j++) {
            if (board[i][j] === 1) {
                board[i][j] = 0;
                queue.push([i, j]);
                answer++;
                while (queue.length) {
                    let [x, y] = queue.shift();
                    for (let k = 0; k < 8; k++) {
                        let nx = x + dx[k];
                        let ny = y + dy[k];
                        if (
                            nx >= 0 &&
                            nx < n &&
                            ny >= 0 &&
                            ny < n &&
                            board[nx][ny] === 1
                        ) {
                            board[nx][ny] = 0;
                            queue.push([nx, ny]);
                        }
                    }
                }
            }
        }
    }
    return answer;
}

let arr = [
    [1, 1, 0, 0, 0, 1, 0],
    [0, 1, 1, 0, 1, 1, 0],
    [0, 1, 0, 0, 0, 0, 0],
    [0, 0, 0, 1, 0, 1, 1],
    [1, 1, 0, 1, 1, 0, 0],
    [1, 0, 0, 0, 1, 0, 0],
    [1, 0, 1, 0, 1, 0, 0]
];

console.log(solution(arr));
```

-   queue에 담는 순간 0으로 마킹해야 queue에 중복으로 값이 저장되는 것을 막을 수 있다.
