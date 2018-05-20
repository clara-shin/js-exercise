### 문제 1

두 정수 `start`, `end`를 입력받아, `start`부터 `end`까지의 모든 정수를 배열로 반환하는 함수를 작성하세요.

예:
```
range(3, 6); -> [3, 4, 5, 6]
```
```js
function range(start, end){
  //console.log(start, end);
  const arr = [];
  for(let i = start; i < end+1; i++){
    arr.push(i);
  }
   console.log(arr);
}

range(2,6);
```

### 문제 2

수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 합을 구하는 함수를 작성하세요.

### 문제 3

배열을 입력받아, falsy인 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.
```js
function filter(arr){
  
  const newArr= [];
  for(let item of arr){
    if(item){
      newArr.push(item);
    }
    
  }
  return newArr;

}

filter([3,4,'hello',null]);
```
### 문제 4

배열을 입력받아, 중복된 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.
```js
const arr = [1,1,2,3,4,4,5,6,7,7,8];


function removeDuplicate(arr) {
  const newArr = [];
  for(let item of arr) {

    //새로 담기는 배열에서 중복을 체크해야 하죠!
    if ( !newArr.includes(item) ) {
     newArr.push(item);
    }
  }
  
  return newArr;
}


removeDuplicate(arr);
```
### 문제 5

수 타입의 값으로만 이루어진 두 배열을 입력받아, 다음과 같이 동작하는 함수를 작성하세요.
- 두 배열의 같은 자리에 있는 요소를 더한 결과가 새 배열의 요소가 됩니다.
- 만약 입력받은 두 배열의 길이가 갖지 않다면, 긴 배열에 있는 요소를 새 배열의 같은 위치에 포함시키세요.

예:
```
addArray([1, 2, 3], [4, 5, 6, 7]) -> [5, 7, 9, 7]
```
```js
function addArray(arr1, arr2) {
  const newArr = [];
  
  if(arr1.length > arr2.length ){
    for(let i=0 ; i < arr1.length; i++) {
        if(arr2[i] === undefined) {
          newArr.push(arr1[i]);
        }else{
          newArr.push(arr1[i]+arr2[i]);
        }
      }
    }else if(arr1.length < arr2.length){
    for(let i=0 ; i < arr2.length; i++) {
        if(arr1[i] === undefined) {
          newArr.push(arr2[i]);
        }else{
          newArr.push(arr1[i]+arr2[i]);
        }
      }
  }

  return newArr;
}

addArray([1, 2, 3], [4, 5, 6, 7]);
```

```js
function addArray(arr1, arr2) {
  const newArr = [];
  
  let array = arr1.length > arr2.length ? arr1.length : arr2.length ;
  //console.log(array);
  for(let i=0 ; i < array; i++) {
    
    if(arr2[i] === undefined) {
      newArr.push(arr1[i]);
    }else if(arr1[i] === undefined) {
      newArr.push(arr2[i]);
    }else{
      newArr.push(arr1[i]+arr2[i]);
    }
    
  }

  return newArr;
}

addArray([1, 2, 3], [4, 5, 6, 7]);
```
### 문제 6

배열을 입력받아, 배열의 요소 중 두 개를 선택하는 조합을 모두 포함하는 배열을 작성하세요.

예:
```
combination([1, 2, 3]); -> [[1, 2], [1, 3], [2, 3]]
```
```js
function combination(arr){
  let newArr = [];
  for(let i=0; i < arr.length; i++){
    for(let j=i+1; j < arr.length; j++){
      console.log(i,j);
      newArr.push([arr[i], arr[j]]);
    }
  }
  return newArr;

}

combination([1, 2, 3]);
```

### 문제 7

'금액'과 '동전의 종류가 들어있는 배열'를 입력받아, 최소한의 동전을 사용해서 금액을 맞출 수 있는 방법을 출력하는 함수를 작성하세요.

예:
```
coins(163, [100, 50, 10, 5, 1]);
// 출력
100
50
10
1
1
1
```
```js
function coins(amount, coinTypes){
  
  let currentAmount = amount;
  for(let ct of coinTypes) {
    //정수나눗셈
    const result = Math.floor(currentAmount / ct);
    //코인타입을 result만큼 출력(for)
    for(let i=0; i < result; i++) {
      console.log(ct);
    }
    //빼기
    currentAmount = currentAmount - result *ct;
  }
  
}
coins(363, [100, 50, 10, 5, 1]);
```
```js
function coins2(amount, coinTypes){
  let currentAmount = amount;
  for(let ct of coinTypes){
    while( currentAmount - ct > 0) {
      console.log(ct);
      currentAmount -= ct;
    }
  }
}
coins2(463, [100, 50, 10, 5, 1]);
```
### 문제 8

수 타입의 값만 들어있는 배열을 입력받아, 해당 배열을 오름차순 정렬하는 함수를 작성하세요. (`Array.prototype.sort`를 사용하지 않고 작성해보세요. [선택 정렬](https://ko.wikipedia.org/wiki/%EC%84%A0%ED%83%9D_%EC%A0%95%EB%A0%AC)을 참고하세요.)
```js
//let minIndex = i; 최소값에 대한 최소값의 인덱스를 저장하는 변수
//let min = arr[i]; 최소값 변수

function sort(arr){

  for(let i=0; i < arr.length; i++){
    let min = arr[i];
    let minIndex = i;
    //지금 탐색중인 값이 최소값인지 검사
    for(let j=i+1; j < arr.length; j++){
      if(min > arr[j]){
        //최소값과 인덱스를 기억
        min = arr[j];
        minIndex = j;
      }
      //자리바꿈
      // const temp = arr[minIndex];
      // arr[minIndex] = arr[i];
      // arr[i] = temp;
      [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
    }
    
  }
  return arr;
}

sort([5,4,3,2,1]);


//버블정렬도 짜보자
function sort(arr){
  for(let i=0; i < arr.length; i++){
    for(let j=i+1; j < arr.length; j++){
      if(arr[i] > arr[j]){
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
    }
  }
  return arr;
}


```


알고리즘


자료구조
어떻게 자료를 정리할 것인지
배열
스택 stack
트리 tree