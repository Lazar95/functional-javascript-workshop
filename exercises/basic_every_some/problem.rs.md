# Задатак

Врати функцију која узима листу валидних корисника, и враћа функцију која враћа `true` ако сви прослеђени корисници постоје у првобитној листи корисника.

Треба да провериш само да ли се идентификатори поклапају.

## Example

```js
var goodUsers = [
  { id: 1 },
  { id: 2 },
  { id: 3 }
]

// `checkUsersValid` је функција коју ти треба да дефинишеш
var testAllValid = checkUsersValid(goodUsers)

testAllValid([
  { id: 2 },
  { id: 1 }
])
// => true

testAllValid([
  { id: 2 },
  { id: 4 },
  { id: 1 }
])
// => false
```

## Аргументи

* goodUsers: листа валидних корисника.

Искористи `Array#some` и `Array#every` за проверу да ли сваки корисник прослеђен враћеној функцији у низу постоји у низу прослеђеном извезеној функцији.

## Услови

* Немој да користиш `for` и `while` петље, као ни `Array#forEach`.
* Немој да креираш непотребне помоћне функције.

## Ресурси

* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/every
* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/some

## Бојлерпејт

```js
function checkUsersValid(goodUsers) {
  return function allUsersValid(submittedUsers) {
    // ОВДЕ ИДЕ РЕШЕЊЕ
  };
}

module.exports = checkUsersValid
```
