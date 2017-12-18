### 문제 1

두 수를 입력받아 큰 수를 반환하는 함수를 작성하세요.
```js
//두 수를 입력받아 큰 수를 반환하는 함수를 작성하세요.

function larger(x, y){
  
  if(x > y) { //만약 x가 크면 x를 반환
    return x;
  }else { //아니라면 y를 반환
    return y;
  }
  
}

larger(10,6);


function larger2(x, y) {
  return x > y ? x : y; //삼항연산자
}

larger2(4,7);

```

### 문제 2

세 수를 입력받아 그 곱이 양수이면 `true`, 0 혹은 음수이면 `false`, 둘 다 아니면 에러를 발생시키는 함수를 작성하세요.

```js

function isPositive(x, y, z) {
  //방어적 코드가 필요
  //입력받는 값이 숫자인지 유한한 수인지 체크
  if ( !isNaN(x) && !isNaN(y) && !isNaN(z) ) {
    const product = x * y * z ;
    if(product > 0){
      return console.log(product, 'true');
    }
    else if(product < 0){
      return console.log(product, 'false');
    }
  }else{
    throw new Error('입력값이 잘못되었습니다');
  }

}

isPositive(10,1,-2);
```
### 문제 3

세 수 `min`, `max`, `input`을 입력받아, 다음과 같이 동작하는 함수를 작성하세요.
- `min`보다 `input`이 작으면, `min`을 반환합니다.
- `max`보다 `input`이 크면, `max`를 반환합니다.
- 아니면 `input`을 반환합니다.

예:
```
limit(3, 7, 5); -> 5
limit(3, 7, 11); -> 7
limit(3, 7, 0); -> 3
```
```js
function limit(min,max,input) {
  if(input < min){
    return min;
  }else if(input > max){
    return max;
  }else{
    return input;
  }
}

function limit2(min,max,input){
  return (input < min) ?  min : 
         (input > max) ?  max : 
         input;
}

limit2(40,300,25);
```


### 문제 4

어떤 정수가 짝수인지 홀수인지 출력하는 함수를 작성하세요. 이를 이용해서, 1부터 20까지의 수가 각각 짝수인지 홀수인지 출력하는 프로그램을 작성하세요.
```js
function printIfEvenOrOdd(x) {
  if (x % 2 === 0){
    console.log(`${x}는 짝수입니다.`);
  }else{
    console.log(`${x}는 홀수입니다.`);
  }
}

for(let i=1; i < 21; i++) {
  printIfEvenOrOdd(i);
}
for(let i=1; i < 21; i++) {
  printIfEvenOrOdd(20-i);
}

for(let i=20; i > 0; i--){
  printIfEvenOrOdd(i);
}
```


### 문제 5

100 이하의 자연수 중 3과 5의 공배수를 모두 출력하는 프로그램을 작성하세요.
```js
for(let i=0; i < 101; i++){
  if( i % 3 === 0 && i % 5 === 0){
    console.log(i);
  }
}
```
### 문제 6

자연수를 입력받아, 그 수의 모든 약수를 출력하는 함수를 작성하세요.
```js
function divisor(x){
  for(let i=1; i < x; i++){
    if(x % i === 0){
      console.log(`${i}는 x의 약수입니다.`)
    }else{
      console.log(`${i}는 x의 약수가 아닙니다.`)
    }
  }
}
divisor(10);
```

### 문제 7

2 이상의 자연수를 입력받아, 그 수가 소수인지 아닌지를 판별하는 함수를 작성하세요.
```js
function isPrime(n){
  if(n < 2){
    alert('2이상의 자연수를 입력해주세요.');
  }else if(n < 0){
    alert('양수를 입력해주세요.');
  }else{
    //console.log('2이상의자연수입니다.');
    for(let i=2; i < n; i++) {
      console.log(`${i}에 대해서 루프 실행`);
      if(n % i === 0){
        //소수가 아니다
        return console.log(n+'는 소수 아니다.');
        //return false;
      }else{
        return console.log(n+'는 소수다.');
        //return true;
      } 
    } 
  }
}
isPrime(10);
```
### 문제 8

1부터 100까지의 수를 차례대로 출력하되, 자릿수에 3, 6, 9중 하나라도 포함되어 있으면 '짝!'을 대신 출력하는 프로그램을 작성하세요.

```js

```

### 문제 9

양의 정수를 입력받아, 다음과 같은 패턴의 출력을 하는 함수를 작성하세요.

1을 입력받은 경우:
```
*
```

3을 입력받은 경우:
```
*
* *
* * *
'*'.repeat(3);
```

5를 입력받은 경우:
```
*
* *
* * *
* * * *
* * * * *
```
```js
  for(let i=1; i <n;i++){
    console.log('*'.repeat(i));
  }
```

### 문제 10

양의 정수를 입력받아, 다음과 같은 패턴의 출력을 하는 함수를 작성하세요.

1를 입력받은 경우:
```
*
```

3를 입력받은 경우:
```
  *
 * *
* * *
 * *
  *
```

5를 입력받은 경우:
```
    *
   * *
  * * *
 * * * *
* * * * *
 * * * *
  * * *
   * *
    *
```

```js
  function diamond(n){
    for(let i=1; i <= n; i++){
      if(i < Math.ceil(n/2)){
        console.log(' '.repeat(n-i)+'* '.repeat(i));
      }else{
        console.log(' '.repeat(i)+'* '.repeat(n-i));
      }
    }
  }
  
  diamond(20);
  
  
  function diamond2(n){
    for(let i=1; i <= n; i++){
      console.log(' '.repeat(n-i)+'* '.repeat(i));
    }
    for(let i = Math.floor(n/2); n >= i; i++){
      console.log(' '.repeat(n-i)+'* '.repeat(i));
    }
    // for(let i = n-1; i > 0; i--){
    //   console.log(' '.repeat(n-i)+'* '.repeat(i));
    // }

  }
  
  diamond2(10);
```

### 문제 11

두 수를 입력받아서, 두 수의 최대공약수를 반환하는 함수를 작성하세요. ([유클리드 호제법](https://ko.wikipedia.org/wiki/%EC%9C%A0%ED%81%B4%EB%A6%AC%EB%93%9C_%ED%98%B8%EC%A0%9C%EB%B2%95)을 참고하세요.)

### 문제 12

세 수를 입력받아 큰 것부터 차례대로 출력하는 함수를 작성하세요.
```js
function sort(x, y, z) {
  if(x > y){
    [x, y] = [y, x]; //분해 대입
    // const temp = x;
    // x = y;
    // y = temp;
  }
  if(y > z){
    const temp = y;
    y = z;
    z = temp;
  }
  if(x > y){
    const temp = x;
    x = y;
    y = temp;
  }
  console.log(x, y, z);
}

sort(10,22,15);

```
### 문제 13

자연수 `n`을 입력받아, `n`번째 피보나치 수를 반환하는 함수를 작성하세요.
```js
function fibo(n){
  let x = 0;
  let y = 1;
  for(let i=0; i < n; i++){
      const sum = x + y;
      let arr=[];
      x = y;
      y = sum;
      console.log(x);
      //[x, y] = [y, x];
  }
}
fibo(10);
```