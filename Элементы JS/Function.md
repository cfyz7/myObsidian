### Итеративный процесс
```
const smallestDivisor = (num) => {
  const iter = (acc) => { 
    if (acc > num / 2) {
      return num;
    }
    if (num % acc === 0) {
      return acc;
    }
    return iter(acc + 1);
  }; 
  return iter(2);
};
console.log(smallestDivisor(13))
```

### Рекурсивный метод
```
const sequenceSum = (begin, end) => {
  // BEGIN
  // Visualize Execution: https://goo.gl/UlTxCs
  if (begin > end) {
    return NaN;
  }
  if (begin === end) {
    return begin;
  }
  return begin + sequenceSum(begin + 1, end);
  // END
};

console.log(sequenceSum(4, 10));
```
