# Задатак

Искористи `Array$filter` да напишеш функцију `getShortMessages`.

`getShortMessages` узима низ објеката са својством `.message` и враћа низ порука које су *краће од 50 знакова*.

Функција треба да врати низ који садржи саме поруке, *без објекта који их садржи*.

## Аргументи

* `messages`: низ од 10 до 100 насумичних објеката који изгледа отприлике овако:

```js
{
  message: 'Esse id amet quis eu esse aute officia ipsum.' // насумице генерисано
}
```

## Услови

* Немој да користиш for и while петље, као ни Array#forEach.
* Немој да креираш непотребне помоћне функције.

## Помоћ

* Пробај да надовежеш неке методе низа!

## Пример

```
[ 'Tempor quis esse consequat sunt ea eiusmod.',
  'Id culpa ad proident ad nulla laborum incididunt.',
  'Ullamco in ea et ad anim anim ullamco est.',
  'Est ut irure irure nisi.' ]
```

## Ресурси

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map

## Бојлерплејт

```js
function getShortMessages(messages) {
  // ОВДЕ ИДЕ РЕШЕЊЕ
}

module.exports = getShortMessages
```
