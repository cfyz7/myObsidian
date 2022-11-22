### `import fs from "fs";`
Встроенный в Node.js модуль для работы с файлами
`

### `const data = fs.readFileSync("path/to/file");`
 Читает содержимое файла


### `запросить у пользователя информацию`
нужно скачать библиотеку
`npm i readline-sync`
var readlineSync = require('readline-sync');

//Ждем ответа пользователя.
var userName = readlineSync.question('May I have your name? ');
console.log('Hi ' + userName + '!');

//Обработать секретный текст (например, пароль).
var favFood = readlineSync.question('What is your favorite food? ', {
  hideEchoBack: true //  Набранный текст на экране скрыт `*` (по умолчанию).
});
console.log('Oh, ' + userName + ' loves ' + favFood + '!');
