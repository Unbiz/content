---
title: "Большое целое"
authors:
  - doka-dog
tags:
  - doka
  - placeholder
---

## Кратко

Тип большого целого `BigInt` — примитивный тип, который представляет целые числа больше 2<sup>53</sup>-1. Эти числа уже не помещаются в стандартный [примитив «число»](/js/number).

Этот тип может использоваться для работы с произвольно большими целыми числами.

## Как пишется

Создать `BigInt` можно двумя способами.

1️⃣ Добавить суффикс `n` в конец записи числа:

```js
const biggy = 9997000254740991n
```

2️⃣ Вызвать конструктор `BigInt`:

```js
const alsoBig = BigInt(9997000254999999)
```

Для `BigInt` определены операции сложения `+`, вычитания `-`, умножения `*`, взятия остатка от деления `%`, возведение в степень `**`.

Операция деления `/` также работает, но дробная часть будет отброшена:

```js
const seven = 7n
const five = 5n

console.log(seven / five)
// 1
```

<aside>

☝️ `BigInt` не сериализуется в [JSON](/tools/json). Это усложняет использование этого типа данных в задачах взаимодействия с сервером.

</aside>
