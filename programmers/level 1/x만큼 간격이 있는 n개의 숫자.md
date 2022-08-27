## 문제 설명

S함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.
<br>
<br>

## 제한사항

-   x는 -10000000 이상, 10000000 이하인 정수입니다.
-   n은 1000 이하인 자연수입니다.

<br>
<br>

## 입출력 예

| x   | n   | answer       |
| --- | --- | ------------ |
| 2   | 5   | [2,4,6,8,10] |
| 4   | 3   | [4,8,12]     |

<br>
<br>

## 나의 답

```js
function solution(x, n) {
    let answer = [];
    let cnt = 0;
    for (let i = 0; i < n; i++) {
        cnt += x;
        answer.push(cnt);
    }
    return answer;
}
```
