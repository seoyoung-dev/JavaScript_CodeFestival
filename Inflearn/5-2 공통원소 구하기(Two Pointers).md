## 문제 설명

A, B 두 개의 집합이 주어지면 두 집합의 공통 원소를 추출하여 오름차순으로 출력하는 프로 그램을 작성하세요.
<br>
<br>

## 입력 설명

집합 a, b가 입력됩니다.
<br>
<br>

## 출력 설명

두 집합의 공통원소를 오름차순 정렬하여 출력합니다.
<br>
<br>

## 입력/출력 예제

| 입력                             | 출력      |
| -------------------------------- | --------- |
| [1, 3, 9, 5, 2], [3, 2, 5, 7, 8] | [2, 3, 5] |

<br>
<br>

## 내 답안

```js
function solution(arr1, arr2) {
    let answer = [];
    let p1 = (p2 = 0);
    let sa = arr1.sort((a, b) => a - b);
    let sb = arr2.sort((a, b) => a - b);
    let n = sa.length;
    let m = sb.length;
    while (p1 < n && p2 < m) {
        if (sa[p1] === sb[p2]) {
            answer.push(sa[p1]);
            p1++;
            p2++;
        } else if (sa[p1] < sb[p2]) {
            p1++;
        } else {
            p2++;
        }
    }
    return answer;
}

let a = [1, 3, 9, 5, 2];
let b = [3, 2, 5, 7, 8];
console.log(solution(a, b));
```

<br>
<br>

## 모범답안

```js
function solution(arr1, arr2) {
    let answer = [];
    arr1.sort((a, b) => a - b);
    arr2.sort((a, b) => a - b);
    let p1 = (p2 = 0);

    while (p1 < arr1.length && p2 < arr2.length) {
        if (arr1[p1] == arr2[p2]) {
            answer.push(arr1[p1++]);
            p2++;
        } else if (arr1[p1] < arr2[p2]) p1++;
        else p2++;
    }
    return answer;
}

let a = [1, 3, 9, 5, 2];
let b = [3, 2, 5, 7, 8];
console.log(solution(a, b));
```

-   p1과 p2 둘 중 하나라도 마지막 인덱스에서 벗어나면 while문은 종료된다
