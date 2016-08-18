# Задатак

Напиши функцију која ти дозвољава да користиш `Array.prototype.slice` тако да не мораш да користиш `slice.call` или `slice.apply` да је позовеш.

Обично мораш да користиш `slice` са `call` или `apply`:

```js
var slice = Array.prototype.slice

function() {
  var args = slice.call(arguments) // ово ради
}
```

Хоћемо да ово успе:

```js
var slice = yourFunction

function() {
  var args = slice(arguments) // ово ради
}
```

## Пример

Функција `slice` која се понаша на следећи начин.

```js
var nums = [1,2,3,4,5]

// Твоја функција `slice` треба да се поклапа са
// понашањем класичне верзије функције, осим што
// као први аргумент узима низ.

slice(nums, 0, 2) // [1, 2]
slice(nums, 1, 2) // [2]

// Класична функција `slice` ради поређења
nums.slice(0, 2) // [1, 2]
nums.slice(1, 2) // [2]
```

## Услови

* Немој да користиш `for` и `while` петље, као ни `Array#forEach`.
* Немој да користиш кључну реч `function` :D

## Помоћ

* Ово се решава у једном реду.
* Свака функција у ЈаваСкрипту наслеђује методе као што су `call`, `apply` и `bind` из објекта `Function.prototype`.
* `Function#call` извршава вредност `this` када се позове. Унутар `someFunction.call()`, вредност из `this` ће бити `someFunction`.
* И сама `Function.call` је функција, што значи да наслеђује од `Function.prototype`.

```js
function myFunction() {
  console.log('called my function')
}

Function.prototype.call.call(myFunction) // => "called my function"
```

## Бојлерплејт

```js
module.exports = // овде иде твоје решење!
```
