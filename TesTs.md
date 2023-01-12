### NODE_OPTIONS=--experimental-vm-modules npx jest 


## Matchers
### https://jestjs.io/ru/docs/expect
````
expect(null).toBeNull();

// Проверяет значение на truthy (любое значение, которое приводится к true)
expect(true).toBeTruthy();
// Точное сравнение с true
expect(true).toBe(true);

expect(undefined).toBeUndefined();

// Проверка, что массив содержит элемент
expect([1, 2, 3]).toContain(2);

// Проверка, что строка содержит подстроку
expect('hello, world').toMatch('hello');

// Проверяет, что в объекте есть свойство с определённым значением
expect({ key: 'value' }).toHaveProperty('key', 'value');
------------------------------------------------------------------------------

expect(null).not.toBeNull(); // not null
expect(undefined).not.toBeUndefined(); // not undefined
expect([1, 2, 3]).not.toContain(2); // not contain 2
expect('hello, world').not.toMatch('hello'); // not match hello
-------------------------------------------------------------------------------

expect(user).toMatchObject({ firstName: 'tolya' });
--------------------------------------------------------------------------------

test('gt', () => { 
	expect(gt(3, 1)).toBe(true); 
	expect(gt(3, 3)).toBe(false);
	expect(gt(1, 3)).toBe(false);
});
--------------------------------------------------------------------------------

import _ from 'lodash';
import getFunction from '../functions.js';

const set = getFunction();
 
const object = { a: [{ b: { c: 3 } }] };
test('set', () => {
  expect(set(object, 'a[0].b.c', 4)).toEqual({ a: [{ b: { c: 4 } }] });
});

test('set2', () => {
  expect(set(object, ['x', '0', 'y', 'z'], 5)).toEqual(
  { "a": [{ "b": { "c": 4 } }], "x": [{ "y": { "z": 5 } }] }
  );
});
````

### https://jestjs.io/docs/api#methods
```
let now;

// Запускается перед каждым тестом
beforeEach(() => {
  now = Date.now(); // текущий timestamp
});

test('first example', () => console.log(now));
test('second example', () => console.log(now));

//  console.log __tests__/index.test.js:9
//    1583871515943 
//  console.log __tests__/index.test.js:10
//    1583871515950
```

## Тесты на добавление товара в корзину
```
Напишите тесты для корзины интернет-магазина. Интерфейс:

makeCart() – создаёт новую пустую корзину (объект).
-----------------
addItem(good, count) – добавляет в корзину товары и их количество. Товар – это объект с двумя свойствами: name (имя) и price (стоимость).
----------------
getItems() – возвращает список товаров в формате [{ good, count }, { good, count }, ...]
----------------
getCost() – возвращает стоимость корзины. Стоимость корзины высчитывается как сумма всех добавленных товаров с учётом их количества.
------------------
getCount() – возвращает количество товаров в корзине.
-----------------
import getImpelementation from '../implementations/index.js';

const makeCart = getImpelementation();

// BEGIN
test('Cart', () => {
  const cart = makeCart();
  expect(cart.getItems()).toHaveLength(0);

  const car = { name: 'car', price: 3 };
  cart.addItem(car, 5);
  expect(cart.getItems()).toEqual(expect.arrayContaining([{ good: car, count: 5 }]));
  expect(cart.getCost()).toBe(15);
  expect(cart.getCount()).toBe(5);

  const house = { name: 'house', price: 10 };
  cart.addItem(house, 2);
  expect(cart.getItems()).toEqual(
    expect.arrayContaining([{ good: car, count: 5 }, { good: house, count: 2 }],
  ));
  expect(cart.getCost()).toBe(35);
  expect(cart.getCount()).toBe(7);
});
```

# Человеческие тесты
```import getImpelementation from '../implementations/functions.js';

const fill = getImpelementation();

// BEGIN
let array;

beforeEach(() => {
  array = [1, 2, 3, 4];
});

test('common case', () => {
  fill(array, '*', 1, 3);
  expect(array).toEqual([1, '*', '*', 4]);
});

test('should use default start and end', () => {
  fill(array, '*');
  expect(array).toEqual(['*', '*', '*', '*']);
});

test('should works with start >= length', () => {
  fill(array, '*', 10, 12);
  expect(array).toEqual([1, 2, 3, 4]);
});

test('should works with start >= end', () => {
  fill(array, '*', 2, 2);
  expect(array).toEqual([1, 2, 3, 4]);
});

test('should works with end > length', () => {
  fill(array, '*', 0, 10);
  expect(array).toEqual(['*', '*', '*', '*']);
});
----------------------------------------------------------------
const fill = (coll, value, start = 0, end = coll.length) => {
  const collLength = coll.length;
  const normalizedStart = start > collLength ? end : start;
  const normalizedEnd = end > collLength ? collLength : end;
  for (let i = normalizedStart; i < normalizedEnd; i += 1) {
    coll[i] = value;
  }
  return coll;
};

export default fill;
```