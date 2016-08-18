Ручно ћемо имплементирати груби аналог ЈаваСкриптовог прототипског наслеђивања, како бисмо се уверили да у потпуности разумемо како прототипско наслеђивање функционише.

# Задатак

Имплементирај функције `New`, `Create` и `Lookup` за симулацију `new`, `Object.create` и механизма за претрагу по својствима које ЈаваСкрипт има уграђене у себе, респективно.

Кроз ову вежбу, избегаваћеш коришћење било којих ЈаваСкриптових уграђених механизама за наслеђивање. Уместо тога, мораћеш да користиш своје `New`, `Create` и `Lookup` функције као и `__PROTO__` за представљаре инстанце прототипа, и `PROTOTYPE` за представљање прототипа конструктора.

На пример:

* `New(Apple, 1,2,3)` == new Apple(1,2,3)
* `obj.__PROTO__` == obj.__proto__ || Object.getPrototypeOf(obj)
* `Constructor.PROTOTYPE` == `Constructor.prototype`

## Део 1: Lookup

`Lookup` ће симулирати понашање механизма за тражење прототипа у ЈаваСкрипту, или "гетере". Када референцираш било својство било ког објекта у ЈаваСкрипту, ЈаваСкрипт ће "прошетати уз ланац прототипова" да нађе својство; ако га пронађе, вратиће његову вредност, а иначе ће вратити `undefined`.

Твојој функцији `Lookup` ће бити достављен објект контеста, и стринг који представља својство које се тражи. Ако се својство нађе у тренутном контексту, врати то својство, иначе провери прототип контекста, `__PROTO__`.

Ако својство није могуће наћи у ланцу прототипова објекта, само врати `undefined`.

```js

var cat = {
  color: 'black'
}

var kitten = {
  size: 'small'
}

var otherKitten = {
  size: 'small',
  color: 'grey'
}

kitten.__PROTO__ = cat
otherKitten.__PROTO__ = cat

Lookup(kitten, 'color')  // => 'black'
Lookup(otherKitten, 'color')  // => 'grey'

Lookup(kitten, 'wings')  // => undefined

// Промена својстава на прототипу треба да има
// утицај на све инстанце које наслеђују из ње.
cat.color = 'blue'

Lookup(kitten, 'color')  // => 'blue'

// Преклопљена својства треба и даље да раде
Lookup(otherKitten, 'color')  // => 'grey'

```

Мала дигресија: у ЈаваСкрипту, када "гетујеш" својство (тј. обавиш lookup), енџин врши тражење уз ланац да нађе вредност, али ако "сетујеш" својство, игнорише прототипски ланац и једноставно постави вредност над тренутним објектом. Могли смо да имплементирамо `Setter` као вежбу, али пошто нема магије, прилично је тривијално:

```js

function Setter(context, property, value) {
  return context[property] = value
}

```

## Део 2: Create

`Create` ће симулирати понашање методе `Object.create`.

Функцији `Create` ће бити прослеђен објекат, и мораш да вратиш нови објект са његовим прототипом (`__PROTO__`) постављеним на достављени објекат.

```js
fuction Cat() {

}

Cat.PROTOTYPE.speak = function() {
  return 'Meow!'
}

function Kitten() {
  Cat.apply(this, arguments)
}

Kitten.PROTOTYPE = Create(Cat.PROTOTYPE)

var kitten = New(Kitten)
Lookup(kitten, 'speak')() // => 'Meow!'

```

## Финале: New

`New` ће симулирати понашање клјуљчне речи `new` из ЈаваСкрипта.

Први аргумент који прима `New` ће бити конструкторска функција (тј. тип). Остали параметри морају да се пренесу конструкторској функцији када се креира нови објекат.

`New` ће вратити нове објекте користећи достављену конструкторску функцију.

```js

function Cat(color) {
  this.color = color
}

var blackCat = New(Cat, 'black')
blackCat.color // => black

var brownCat = New(Cat, 'brown')
brownCat.color // => brown

```

Конструкторска функција која се прослеђује функцији `New` може да има својство `.PROTOTYPE`. Сви објекти креирани обим конструктором треба да имају свој `__PROTO__` подешен на конструкторово својство `.PROTOTYPE`.

```js

function Cat(color) {
  this.color = color
}

Cat.PROTOTYPE.speak = function() {
  return 'Meow!'
}

function Kitten() {
  Cat.apply(this, arguments)
}

Kitten.PROTOTYPE = Create(Cat)

Kitten.PROTOTYPE.speak = function() {
  return 'Mew.'
}

var blackCat = New(Cat, 'black')
blackCat.color // => black

var brownCat = New(Cat, 'brown')
brownCat.color // => brown

```

Прототипска својства треба да буду доступна у конструктору:

```js
function Cow() {
  // lookup this.moo:
  console.log('moo', Lookup(this, 'moo'));
}

// Овај корак аутомарски ради "прати" ЈаваСкрипт
Cow.PROTOTYPE = {}

Cow.PROTOTYPE.moo = true
var cow = New(Cow) // 'moo' true

```

Морамо и да симулирамо још једно понашање кључне речи `new`: ако сам конструктор враћа вредност, `New` треба да врати ту вредност.

```js

function Cat(){
  return 3
}
var cat = new Cat() // 3
var cat = New(Cat) // 3

```

## Услови

* Немој да користиш никакве механизме за прототипско наслеђивање из ЈаваСкрипта.
* Немој да зовеш `new`.
* Немој да користиш `__proto__`, `Object.getPrototypeOf`, као ни `Object.setPrototypeOf`.

## Помоћ

* Употреби `hasOwnProperty` да откријеш да ли објекат има својство.


## Бојлерполејт

```js

/**
 * @param context {Object} Иницијални објекат за почетак трагања за `property`.
 * @param property {String} Име својства које покушавамо да нађемо.
 * @return {Mixed} Вредност `property`-ја у `context`-у или негде у његовом ланцу прототипа.
 */

function Lookup(context, property) {

}

/**
 * @param proto {Object} Прототип који треба да се употреби за креирани објекат.
 * @return Нови објекат чији је прототип подешен на `proto`.
 */

function Create(proto) {

}

/**
 * @param Constructor {Function} Конструктор за нови тип.
 * @return Нова инстанца типа који је дефинисан помоћу `Constructor`.
 */

function New(Constructor) {

}

module.exports = {
  Lookup: Lookup,
  Create: Create,
  New: New
}

```
