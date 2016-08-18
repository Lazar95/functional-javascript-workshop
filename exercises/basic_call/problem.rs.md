Јаваскрипт имплементира "патколико" типизирање података. Патколико типизирање је стил динамичког типизирања у којем методе и својства објекта одређују исправну семантику, а не његово наследство из одређене класе, нити имплементација одређеног интерфејса. Име и концепт односе се на патколик тест, који се преписује Џејмсу Виткомбу Рајлију, и може се исказати на следећи начин:

  "Када видим птицу која хода као патка и плива као патка и кваче као патка, ја ту птицу зовем патка."

У Јаваскрипту, како бисмо писали робусне програме, понекад треба да проверимо да ли се објекат уклапа у тип који очекујемо.

Можемо да користимо Object#hasOwnProperty како бисмо детектовали да ли објекат "има" својство дефинисано на самом себи (а не наслеђено из прототипа):

```js
var duck = {
  quack: function() {
    console.log('quack')
  }
}

duck.hasOwnProperty('quack') // => true
```

Патки нисмо дали методу `.hasOwnProperty`; одакле јој онда?

Патка је креирана синтаксом `{}`, па због тога наслеђује од `Object.prototype`:

```js
var object = {quack: true}

Object.getPrototypeOf(object) === Object.prototype // => true
object.hasOwnProperty('quack')                     // => true
```

Али шта ако објекат не наслеђује од `Object.prototype`?

```js
// create an object with 'null' prototype.
var object = Object.create(null)
object.quack = function() {
  console.log('quack')
}

Object.getPrototypeOf(object) === Object.prototype // => false
Object.getPrototypeOf(object) === null             // => true

object.hasOwnProperty('quack')
// => TypeError: Object object has no method 'hasOwnProperty'
```

И даље можемо да користимо `hasOwnProperty` из `Object.prototype`, ако га позовемо тако да је `this` подешено на нешто што "изгледа као објекат". `Function#call` нам дозвољава да позовемо било коју функцију са измењеном вредношћу `this`.

```js
// први аргумент функцији `call` постаје вредност `this`
// остатак аргумената се прослеђују функцији такви какву су

Object.prototype.hasOwnProperty.call(object, 'quack') // => true
```
# Задатак

Напиши функцију `duckCount` која враћа број прослеђених аргумената којима је својство `quack` дефинисано директно. Не рачунај својства наслеђена из прототипа.

Пример:

```js
var notDuck = Object.create({quack: true})
var duck = {quack: true}
duckCount(duck, notDuck) // 1
```
## Аргументи

* Биће ти прослеђено 0-20 аргумената. Сваки аргумент може да буде било ког типа са било којим својствима. Неки од аргумената ће имати својство `quack`.

## Услови

* Немој да користиш for и while петље, као ни Array#forEach.
* Немој да креираш бројачке или акумулаторске променљиве.
* Немој да креираш непотребне помоћне функције.

## Помоћ

* Променљива `arguments`, која је доступна у свакој функцији, је *објекат* који кваче као *низ*:

```js
{
  0: 'argument0',
  1: 'argument1', // итд.
  length: 2
}
```

## Ресурси

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice#Array-like
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments


## Бојлерплејт

```js
function duckCount() {
  // ОВДЕ ИДЕ РЕШЕЊЕ 
}

module.exports = duckCount
```
