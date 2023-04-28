## 1

Вот пример реализации функции bind без использования стандартной функции bind():

function bind(obj, fn) {   
	return function (...args) {     
		return fn.apply(obj, args);   
	}; 
}`

Эта функция принимает два аргумента – объект, который будет привязан к контексту и функцию, которую нужно привязать к контексту. Она возвращает новую функцию, которая вызывает оригинальную функцию с привязанным контекстом объекта.

## 2

Для решения данной задачи можно использовать метод forEach. Вот пример решения:

export default (objects, callback) => {
  objects.forEach(function() {
    callback.call(this);
  });
}
Эта функция принимает коллекцию объектов и колбек функцию. Для каждого объекта в коллекции, функция вызывает переданный колбек. Но вместо передачи самого объекта в колбек функцию, мы устанавливаем его как контекст с помощью метода call(). Это позволяет в колбеке обращаться к свойствам и методам объекта через ключевое слово this.

## 3

Для решения данной задачи необходимо реализовать функцию `each`, которая принимает на вход коллекцию объектов и колбек-функцию, и вызывает эту функцию для каждого объекта коллекции, устанавливая объект в качестве контекста. Функция `each` должна модифицировать объекты коллекции в соответствии с логикой колбек-функции.

Пример реализации:

function each(collection, callback) {   
	for (let i = 0; i < collection.length; i++) { 
	    callback.call(collection[i]);   
	} 
}  

В данном примере функция `each` вызывает колбек-функцию `callback` для каждого объекта из коллекции `objects`, устанавливая объект как контекст. Функция `callback` модифицирует объекты коллекции, переворачивая строки свойства `name`. После вызова функции `each` коллекция `objects` будет изменена.

# 4
```javascript
Вот решение на JavaScript:

export default function reverseSegment(segment) {   
	const begin = new Point(segment.end.x, segment.end.y);   
	const end = new Point(segment.begin.x, segment.begin.y);   
	return new Segment(begin, end);
}

В данном решении используются классы `Point` и `Segment`. Предполагается, что они уже определены в коде. Если нет, то их можно реализовать следующим образом:

`class Point {   
	constructor(x, y) {     
		this.x = x;    
		this.y = y;   
	} 
} 

class Segment {   
	constructor(begin, end) {
	    this.begin = begin;     
	    this.end = end;   
	} 
}`

Эти классы определяют точку и отрезок соответственно. Конструкторы классов
```

### 5
```javascript
class Tree {
  constructor(key) {
    this.key = key;
    this.children = new Map();
    this.parent = null;
  }

  getKey() {
    return this.key;
  }

  getParent() {
    return this.parent;
  }

  getChildren() {
    return [...this.children.values()];
  }

  hasChildren() {
    return this.children.size > 0;
  }

  hasChild(key) {
    return this.children.has(key);
  }

  addChild(key) {
    const child = new Tree(key);
    child.parent = this;
    this.children.set(key, child);
    return child;
  }

  removeChild(key) {
    return this.children.delete(key);
  }

  getDeepChild(keys) {
    if (!keys || keys.length === 

```

```javascript
Вот решение:
import fsPromises from 'fs/promises';
import path from 'path';
import _ from 'lodash';

const getDirectorySize = async (directoryPath) => {
  const files = await fsPromises.readdir(directoryPath);
  const filesDetails = await Promise.all(files.map(async (file) => {
    const filePath = path.join(directoryPath, file);
    const stat = await fsPromises.stat(filePath);
    return {
      name: file,
      size: stat.size,
      isDirectory: stat.isDirectory(),
    };
  }));
  const filesSize = _.sumBy(filesDetails.filter(({ isDirectory }) => !isDirectory), 'size');

  return filesSize;
};
}
export { getDirectorySize };
```
Код на JavaScript, который экспортирует функцию `getDirectorySize`. Эта функция принимает путь к директории как аргумент и возвращает размер всех файлов в этой директории.

Внутри функции происходит следующее:

1.  Через модуль fs.promises (fsp) получаются имена всех файлов в директории.
2.  Далее для каждого файла формируется объект с информацией о его имени, размере и типе (файл или директория).
3.  С помщью библиотеки Promise.all собираются все промисы, которые получают информацию о каждом файле, в массив. Таким образом получается массив объектов с информацией о каждом файле в директории.
4.  Фильтруются только те файлы, которые являются файлами, а не директориями.
5.  С помощью библиотеки lodash вычисляется общий размер всех файлов при помощи метода sumBy.
6.  Размер всех файлов возвращается из функции.


