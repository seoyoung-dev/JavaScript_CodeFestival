## 문제 설명

오름차순으로 정렬이 된 두 배열이 주어지면 두 배열을 오름차순으로 합쳐 출력하는 프로그램 을 작성하세요.
<br>
<br>

## 입력 설명

첫 번쨰 줄에 10진수 N(1<=N<=1,000)이 주어집니다.
<br>
<br>

## 출력 설명

오름차순으로 정렬된 배열을 출력합니다.
<br>
<br>

## 입력/출력 예제

| 입력                       | 출력                     |
| -------------------------- | ------------------------ |
| [1, 3, 5], [2, 3, 6, 7, 9] | [1, 2, 3, 3, 5, 6, 7, 9] |

<br>
<br>

## 내 답안

```js
function solution(arr1, arr2) {
    let answer = [];
    let n = arr1.length;
    let m = arr2.length;
    let p1 = (p2 = 0);
    while (p1 < n && p2 < m) {
        if (arr1[p1] <= arr2[p2]) answer.push(arr1[p1++]);
        else answer.push(arr2[p2++]);
    }
    while (p1 < n) answer.push(arr1[p1++]);
    while (p2 < m) answer.push(arr2[p2++]);
    return answer;
}

let a = [1, 3, 5];
let b = [2, 3, 6, 7, 9];
console.log(solution(a, b));
```

<br>
<br>

## 새로 학습한 내용

-   투 포인터
