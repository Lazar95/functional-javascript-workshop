# Задатак

Претвори следећи код из `for`-петље у `Array#map`:

```js
function doubleAll(numbers) {
  var result = []
  for (var i = 0; i < numbers.length; i++) {
    result.push(numbers[i] * 2)
  }
  return result
}

module.exports = doubleAll
```

## Аргументи

* numbers: Низ од 0 до 20 целих бројева између 0 и 9.

## Услови

* Твоје решење мора да користи `Array.prototype.map()`.
* Немој да користиш `for` и `while` петље, као ни `Array.prototype.forEach`.
* Немој да креираш никакве помоћне функције.

## Ресурси

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map

## Бојлерплејт

```js
function doubleAll(numbers) {
  // ОВДЕ ИДЕ РЕШЕЊЕ
}

module.exports = doubleAll
```
