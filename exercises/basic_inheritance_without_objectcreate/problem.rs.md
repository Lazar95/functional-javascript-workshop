# Задатак

Реши исти проблем као у задатку "Основно наслеђивање са Object.create", али овај пут немој да користиш Object.create!

Детаљи су копирани у наставку као референца.

## Услови

* Немој да без потребе зовеш конструктор класе `User`!
* Немој да користиш `Object.create`.
* Немој да користиш `__proto__`.

## Помоћ

* Прототипови су увек објекти.
* Инстанце твоје класе `BetterUser` треба да "наследе" од `User.prototype`.
* Нема разлога да не креираш помоћне објекте у стаблу наслеђивања.
* Добро проучи шта ради `Object.create`.

## Ресурси

* http://www.bennadel.com/blog/2184-Object-create-Improves-Constructor-Based-Inheritance-In-Javascript-It-Doesn-t-Replace-It.htm

## Текст из прошлог задатка

# Задатак

Креирај нови тип `BetterUser` који проширује `User` тако што преклапа методу `.toString` из `User`.

Функција коју изведеш ће бити прослеђена конструкторској функцији за тип `User` који изгледа овако:

```js
/**
 * Конструктор за тип `User`.
 *
 * @param title {String} Корисникова титула, нпр. "Mr.", "Mrs.", "Dr.", итд.
 * @param name {String} Име корисника, нпр. "John Smith".
 */

function User(title, name) {
  this.title = title
  this.name = name
  console.info('NEW USER: ' + this)
}

/**
 * Креира пуно име за приказ за корисника.
 * @return {String} Име за приказ.
 */

User.prototype.displayName = function() {
  return this.title + ' ' + this.name
}

/**
 * @return {String} Форматирано име и титула
 */

User.prototype.toString = function() {
  return '[User:'+this.displayName()+']'
}
```

Обрати пажњу: не треба да копираш ово у своје решење.

## Пример

Из функције коју изведеш врати конструторску функцију `BetterUser` која наслеђује `User` са новом методом `.toString` која ради на следећи начин:

```js
var joe = new BetterUser('Mr.', 'Joe Smith') // проследи титулу и име
console.log('Hello ' + joe) // 'Hello [BetterUser: Mr. Joe Smith]'
```

## Услови

* Немој да без потребе зовеш контруктор `User`!
* Немој да користиш `__proto__`.
* Немој да креираш непотребе помоћне функције.

## Ресурси

* http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/
* http://tobyho.com/2011/11/11/js-object-inheritance/
* http://hughfdjackson.com/javascript/2012/01/05/prototypes:-the-short%28est-possible%29-story/

## Бојлерплејт

```js
// User је конструктор
function upgradeUser(User) {

  // ИЗМЕНИ ОВО У СКЛАДУ С ПОТРЕБАМА
  function BetterUser() {

  }

  return BetterUser
}

module.exports = upgradeUser
```
