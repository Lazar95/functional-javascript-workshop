# Задатак

Искористи `Array#reduce` за имплементацију једноставне верзије `Array#map`.

## Очекивани излаз

Функција `map` која примењује функцију на сваки елемент низа и сакупља резултате у нови низ.

```js

var nums = [1,2,3,4,5]

// `map` је твоја извезена функција
var output = map(nums, function double(item) {
  return item * 2
})

console.log(output) // => [2,4,6,8,10]

```

## Аргументи

* input: произвољан низ било ког типа.
* operation: произвољна функција која се може применити на елементе низа `input`.

## Помоћ

* Нема потребе да имплементираш опциони аргумент `thisArg` који има `Array.prototype.map`, али добијаш бонус поене ако успеш!

## Ресурси

* https://en.wikipedia.org/wiki/Reduce_(higher-order_function)
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce

## Бојлерплејт

```js

module.exports = function arrayMap(arr, fn) {
  // ОВДЕ ИДЕ РЕШЕЊЕ
}

```

