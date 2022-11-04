## 문제 설명

현수의 아빠는 제과점을 운영합니다. 현수 아빠는 현수에게 N일 동안의 매출기록을 주고 연속 된 K일 동안의 최대 매출액이 얼마인지 구하라고 했습니다.<br />
만약 N=10이고 10일 간의 매출기록이 아래와 같습니다. 이때 K=3이면<br />
12 15 <b>11 20 25</b> 10 20 19 13 15<br />
연속된 3일간의 최대 매출액은 11+20+25=56만원입니다. 여러분이 현수를 도와주세요.<br />

<br />
<br />

## 입력/출력 예제

| 입력                      | 출력 |
| ------------------------- | ---- |
| 259, [81, 58, 42, 33, 61] | 242  |

<br />
<br />

## 내 답안

```js
function solution(k, arr) {
    let subtotals = [];
    let sum;
    let n = arr.length;
    for (let i = 0; i <= n - k; i++) {
        sum = arr.slice(i, i + k).reduce((pre, cur) => pre + cur);
        subtotals.push(sum);
    }
    return Math.max(...subtotals);
}

let a = [12, 15, 11, 20, 25, 10, 20, 19, 13, 15];
console.log(solution(3, a));
```

-   알고리즘을 사용하지 않은 단순 구현 방법

</br>  
</br>

## 모범답안

```js
function solution(k, arr) {
    let answer,
        sum = 0;
    for (let i = 0; i < k; i++) sum += arr[i];
    answer = sum;
    for (let i = k; i < arr.length; i++) {
        sum += arr[i] - arr[i - k];
        if (sum > answer) answer = sum;
    }
    return answer;
}

let a = [12, 15, 11, 20, 25, 10, 20, 19, 13, 15];
console.log(solution(3, a));
```

-   for문을 통해 새로운 인덱스의 값이 추가하고, window에 해당하지 않는 인덱스의 값은 삭제한다.

</br>  
</br>

## 새로 학습한 내용

-   슬라이딩 윈도우
    -   '창문을 만들고 그것을 쭉 민다'
    -   이중 for문을 사용하지 않고 단일 for문으로 값을 연산한다.
