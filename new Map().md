### Реализуйте и экспортируйте по умолчанию функцию, которая принимает на вход два параметра: список слов и список стоп-слов. Задача функции вернуть объект типа `Map`, содержащий в себе частоту переданных слов. То есть, ключами являются сами слова, а значениями число повторений.
```
export default function wordsCount(words, stopWords) {
  const newWords = words.map((item) => item.toLowerCase())
    .filter((word) => {
      if (!stopWords.includes(word)) {
        return word;
      }
    })
    .reduce((acc, word) => {
      const count = acc.get(word) || 0;
      acc.set(word, count + 1);
      return acc;
    }, new Map());
  return newWords;
}

ILI

export default (words, stopWords) => words
  .map((word) => word.toLowerCase())
  .filter((word) => !stopWords.includes(word))
  .reduce((acc, word) => {
    const count = acc.get(word) || 0;
    return acc.set(word, count + 1);
  }, new Map());
```