# Задатак

Имплементиран рекурзивну верзију функције која враћа све уникатне зависности и под-зависности модула, сортиране по алфабетном редоследу. Завиности треба да буду одштампане у формату `зависност@верзија`, нпр. `inflection@1.2.6`.

Више верзија истог модула је дозвољено, али дупли модуле исте верзије треба да се уклоне.

## Аргументи

* tree: Стаблно зависности. Погледај доле за пример структуре.

## Пример

```js
var loremIpsum = {
  "name": "lorem-ipsum",
  "version": "0.1.1",
  "dependencies": {
    "optimist": {
      "version": "0.3.7",
      "dependencies": {
        "wordwrap": {
          "version": "0.0.2"
        }
      }
    },
    "inflection": {
      "version": "1.2.6"
    }
  }
}

getDependencies(loremIpsum) // => [ 'inflection@1.2.6', 'optimist@0.3.7', 'wordwrap@0.0.2' ]

```

## Услови:

* Немој да користиш `for` и `while` петље.

## Бојлерплејт

```js

function getDependencies(tree) {
  // ОВДЕ ИДЕ РЕШЕЊЕ
  // Напомена: Слободно убаци још неке аргументе
  // овој функцији које ћеш користити кроз рекурзивне
  // позиве. Или немој! Има много начина на које
  // се може остварити рекурзија.
}

module.exports = getDependencies

```

## Ресурси

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys
