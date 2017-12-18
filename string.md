### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```
```js
function insensitiveEqual(str1, str2){
  return str1.toLowerCase() === str2.toLowerCase();
}

insensitiveEqual('hello', 'Hello');
```


### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```
```js
function leftPad(s, n){

  if(s.length < n){
    //console.log(s);
    return ' '.repeat(n - s.length) + s;
  }else{
    return s;
  }
  
}

leftPad('hello', 8); //  '   hello'
leftPad('hello', 3); //  'hello'
```

### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

```js
function letter(str){
  let arrStr = Array.from(str);
  console.log(arrStr);
  let moeum = ['a', 'e', 'i', 'o', 'u'];
  for(let item of arrStr) {
    if(moeum.includes(item)){
      //arrStr의 모음 갯수 카운팅
    }
  }
}

letter('hello');
```

### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```
```js
function countChar(str){
  const obj = {};
  for(let c of str){
    if(obj[c] === undefined){
      obj[c] = 1;
    } else {
      obj[c]++;
    }
  }
  return obj;
}

counterChar('hello');
```
```js
const obj = {
  a: 1,
  b: 2
};
const propName = 'a';
obj[propName]; //1

console.log(obj.a);
console.log(obj['a']);
console.log(obj[propName]);  ///////*
```
### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)
```js
function isPalindrome(str){
  for(let i=0; i < str.length; i++){
    if(str[i] !== str[str.length-1-i]) {
      return false;
    }
    return '회문이요!';
  }
}

// 내가 짠 코드
function isPalindrome2(str){
  let n = str.length; //문자열의 갯수
  for(let i=0; i < Math.floor(n/2); i++){
    if(str[i] !== str[n -1 -i]) {
      return false;
    }
    return '회문이요!';
  }
}

function isPalindrome3(str){
  const arr1 = Array.from(str);
  const arr2 = Array.from(str).reverse();
  for(let i=0; i < Math.floor(arr1.length/2);i++){
    if(arr1[i] !== arr2[i]){
      return false;
    }
    return '회문';
  }
  
  //값이 같다고해서 같은 배열은 아니다 false
  //각 배열이 담긴 객체는 다른 객체이므로..
  //배열을 이용해서 풀기위해선 각 인덱스를 돌면서 체크해야 한다.
}
function isPalindrome4(str){
  const spaceRemoved = str.replace(/\s/g,'').toLowerCase();
  return spaceRemoved === Array.from(spaceRemoved).reverse().join();
}


isPalindrome3('never odd or even');
```
### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```
```js
function subString(str){
  let arr = [];
  for(let i=0; i < str.length; i++){
    for(let j=i+1; j < str.length+1; j++){
      //console.log(str[i],str[j]);
      arr.push(str.slice(i,j));
    }
  }
  return arr;
}

subString('햄버거');
```
### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```
```js
function removeDuplicates(str){
  let newStr = '';
  for(let item of str){
    if(!newStr.includes(item)){
      newStr += item;
    }
    
  }
  return newStr;
}

removeDuplicates('tomato');

```
### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.
```js
function hiddenId(str){
  let newStr = str.split('@');
  const seperator = '@';
  //console.log(newStr);
  return '*'.repeat(newStr[0].length) + seperator + newStr[1];
}

hiddenId('aaa@naver.com');
```
```js
function hideId(email){
  let numOfId = 0;
  let atAppeared = false;
  let domain ='';
  for(let c of email) {
    if(c === '@') { atAppeared = true; }
    if(!atAppeared) {
      numOfId++;
    }else{
      domain += c;
    }
  }
  let result ='';
  for(let i=0; i < numOfId; i++){
    result += '*';
  }
  result += '@';
  result += domain;
  return result;
}
hideId('aaa@naver.com');
```
```js
function hideId2(email){ //분해대입
  const [id, domain] = email.split('@');
  return '*'.repeat(id.length) + '@' + domain;
}
hideId2('aaa@naver.com');
```

### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.
```js
function textTransform(str){
  let newStr='';
  for(let item of str) {
    if(item.toLowerCase() !== item){
      newStr += item.toLowerCase();
    }else{
      newStr += item.toUpperCase()
    }

  }
  return newStr;
}

textTransform('ShinHyeJin');
```
```js
function changeCase(str){
  let newStr = '';
  for(let c of str){
    if(c.toLowerCase() === c){
      newStr += c.toUpperCase();
    }else{
      newStr += c.toLowerCase();
    }
  }
  return newStr;
}
changeCase('ShinHyeJin');

```

---

### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)
```js
function textUppercase(str){
  
  let arr = str.split(' ');
  let newArr= [];
  console.log(arr);
  for(let item of arr){
    item = item[0].toUpperCase()+item.slice(1,item.length);
    newArr.push(item);
  }
    return newArr.join(' ');
}

textUppercase('hello my name is apple');
```

### 문제 11

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)
```js
function longestWord(str){
  let arr = str.split(' ');
  let newStr = '';
  let temp;
  
  for(let i=0; i < arr.length-1; i++){
    if(arr[i].length > arr[i+1].length ){
      temp = arr[i];
      arr[i] = arr[i+1];
      arr[i+1] = temp;
    }else{
      temp = arr[i+1];
      arr[i+1] = arr[i];
      arr[i] = temp;
    }
    newStr = temp;
  }
  return newStr;
  
}

longestWord('how is it going');
```
```js
function longestWord2(str){
  const arr = str.split(' ');
  console.log(arr);
  let longest = arr[0];
  for(let i=1; i < arr.length; i++) {
    if(arr[i].length > longest.length){
      longest = arr[i]; //새로운 값을 담는다
    }
  }
  return longest;
}
longestWord2('hello fun javascript');
```

### 문제 12

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.
```js
function fisrtChars(s, n){
  let newStr = '';
  for(let i=0; i < n && i < s.length; i++){
    newStr += s[i];
  }
  return newStr;
}

fisrtChars('hello','4');
```


---
### 문제 13 - 숙제

Camel case의 문자열을 입력받아, snake case로 바꾸어주는 함수를 작성하세요.
```js
function snakecase(str){
  let newStr = '';
  
  for(let c of str){
    if(c.toUpperCase() === c){
      newStr += '-' + c.toLowerCase();
    }else{
      newStr += c;
    }
  }
  return newStr;
  
}

snakecase('helloFunJavascript'); //'hello-fun-javascript'
```


### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾸어주는 함수를 작성하세요.
```js

```
### 문제 15

`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.
```js

//split 내부함수
function split(arr, func){
  return arr.reduce( (acc, item) => {
    //...
    return acc;
  });
}
function cutArr(str){

}

cutArr('-', );

```
예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```

### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```
```js
function convertBinary(str){
  console.log(str.length);
  //console.log(num); 1011 
  let sum = 0;
  for(let i=0; i < str.length; i++){
    sum += Number(str[i] * (2 ** (str.length -1 -i) )); //str.length = 4
  }
  return sum;
}


convertBinary('1101');
```

### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```



```js
function filter(arr, func) {
  return arr.reduce((acc, item) => {
    console.log(acc, item);
    if (func(item)) {
      acc.push(item);
    }
    return acc;
  }, []);
}

function map(arr, func) {
  return arr.reduce((acc, item) => {
    acc.push(func(item));
    return acc;
  }, []);
}

function every(arr, func) {
  return arr.reduce((acc, item) => {
    return acc && func(item);
  }, true);
}

function some(arr, func) {
  return arr.reduce((acc, item) => {
    return acc || func(item)
  }, false);
}

```