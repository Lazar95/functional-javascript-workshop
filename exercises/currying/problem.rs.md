Ово је пример имплементације функције `curry3`, које карингује до три аргумента:

```js
function curry3(fun){
  return function(one){
    return function(two){
      return function (three){
        return fun(one, two, three)
      }
    }
  }
}
```

Ако бисмо искористили ову имплементацију са овом функцијом...

```js
function abc(one, two, three) {
  return one/two/three
}
```

...радило би овако:

```js
var curryC = curry3(abc)
var curryB = curryC(6)
var curryA = curryB(3)

console.log(curryA(2)) // => 1
```

# Задатак

У овом изазову, треба да имплементираш каринг функцију за произвољан број аргумената.

Функција `curryN` треба да узима два параметра:

* fn: Функција која треба да се карингује.
* n: Опциони број аргумената који се карингује. Ако није наведен, `curryN` треба да користи арност функције `fn` за вредност `n`.

## Пример

```js
function add3(one, two, three) {
  return one + two + three
}

var curryC = curryN(add3)
var curryB = curryC(1)
var curryA = curryB(2)
console.log(curryA(3)) // => 6
console.log(curryA(10)) // => 13

console.log(curryN(add3)(1)(2)(3)) // => 6
```

## Услови

* Немој да користиш `for`  и `while` петље, као ни `Array.prototype.forEach`.

## Помоћ

* Можеш да детектујеш број очекиваних аргумената функције (њену арност) тако што ћеш проверити својство `.length` функције.

## Бојлерплејт

```js
function curryN(fn, n) {
  // ОВДЕ ИДЕ РЕШЕЊЕ
}

module.exports = curryN
```
