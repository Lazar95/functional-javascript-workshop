# Задатак

За задати низ стрингова, искористи `Array#reduce` за креирање објекта који садржи број понављања сваког стринга у низу. Врати објекат директно (нема потребе за коришћењем `console.log`).

## Пример

```js
var inputWords = ['Apple', 'Banana', 'Apple', 'Durian', 'Durian', 'Durian']

console.log(countWords(inputWords))

// =>
// {
//   Apple: 2,
//   Banana: 1,
//   Durian: 3
// }
```

## Аргументи

* inputWords: Низ насумице генерисаних стрингова. 

## Услови

* Немој да користиш for и while петље, као ни Array#forEach.
* Немој да креираш непотребне помоћне функције.

## Ресурси

* https://en.wikipedia.org/wiki/Reduce_(higher-order_function)
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce

## Бојлерплејт

```js
function countWords(inputWords) {
  // ОВДЕ ИДЕ РЕШЕЊЕ 
}

module.exports = countWords
```
