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



