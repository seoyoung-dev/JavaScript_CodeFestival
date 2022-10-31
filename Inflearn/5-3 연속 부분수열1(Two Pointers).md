## 문제 설명

N개의 수로 이루어진 수열이 주어집니다.
이 수열에서 연속부분수열의 합이 특정숫자 M이 되는 경우가 몇 번 있는지 구하는 프로그램을 작성하세요.<br>
만약 N=8, M=6이고 수열이 다음과 같다면<br>
12131112<br>
합이 6이 되는 연속부분수열은 {2, 1, 3}, {1, 3, 1, 1}, {3, 1, 1, 1}로 총 3가지입니다.
<br>
<br>

## 입력 설명

특정숫자 M과 배열이 입력으로 주어집니다.
<br>
<br>

## 출력 설명

합이 M이 되는 연속부분수열의 갯수를 출력하세요.
<br>
<br>

## 입력/출력 예제

| 입력                        | 출력 |
| --------------------------- | ---- |
| 6, [1, 2, 1, 3, 1, 1, 1, 2] | 3    |

<br>
<br>

## 내 답안

```js
function solution(m, arr) {
    let p1 = (p2 = 0);
    let n = arr.length;
    let count = 0;
    let sum = arr[0];
    // p1을 움직일 떄: sum이 6과 같거나 작을 때
    // p2를 움직일 때: sum이 6을 초과

    // p1이 더 움직일 수 없는 순간 종료된다
    while (p1 < n && p2 < n) {
        if (sum === m) {
            count++;
            sum -= arr[p2];
            p2++;
        } else if (sum < m) {
            p1++;
            sum += arr[p1];
        } else {
            sum -= arr[p2];
            p2++;
        }
    }

    return count;
}

let a = [1, 2, 1, 3, 1, 1, 1, 2];
console.log(solution(6, a));
```

<br>
<br>

## 모범답안

```js
function solution(m, arr) {
    let answer = 0,
        lt = 0,
        sum = 0;
    for (let rt = 0; rt < arr.length; rt++) {
        sum += arr[rt];
        if (sum === m) answer++;
        while (sum >= m) {
            sum -= arr[lt++];
            if (sum === m) answer++;
        }
    }
    return answer;
}

let a = [1, 2, 1, 3, 1, 1, 1, 2];
console.log(solution(6, a));
```

-   합이 6이 될 경우 오른쪽 좌표가 아닌 왼쪽 좌표를 움직여 <code>sum</code>에서 값을 뺀다.
