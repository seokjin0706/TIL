# Array 선언과 동시에 초기화

``` typescript
let arr = new Array<number>(5).fill(0)); // [0, 0, 0, 0, 0]

```

# Array 맨 앞에 원소 삽입

[unshift]

``` typescript
arr.unshift(10);
```

# Array 특정 위치에 원소 제거

[splice]

``` typescript
arr.splice(3,1); // index 3의 원소 1개 제거
```

# Array 정렬

[sort]

``` typescript

let numbers = [1, 10, 4, 5, 7, 2, 3];
numbers.sort((a, b)=>{
if(a > b) return 1;  // b가 a 앞에 온다.
if(a < b) return -1; // a가 b 앞에 온다.
return 0;     // a, b 정렬 유지
})
console.log(numbers);

```

# Array 특정 원소 찾기
[find]

원소가 배열 안에 있으면 해당 값을 리턴, 없으면 undefined
```typescript
let numbers = [1, 10, 4, 5, 7, 2, 3];
number.find((n)=>n === 10)  //10
```

[findIndex]

원소가 배열 안에 있으면 해당 원소의 index 리턴, 없으면 -1 리턴

``` typescript
let numbers = [1, 10, 4, 5, 7, 2, 3];
number.findIndex((n)=>n === 10)  //1

```
