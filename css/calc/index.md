---
title: "`calc()`"
authors:
  - solarrust
contributors:
  - skorobaeus
keywords:
  - функция
  - вычисление
tags:
  - doka
---

## Кратко

Крутейшая функция, позволяющая производить математические вычисления прямо в CSS. Раньше, до появления `calc()`, приходилось **страдать** и вычислять размеры примерно.

## Пример

Частая ситуация: в вёрстке три колонки, ширина каждой из которых должна быть ровно третью от 100%. 100% / 3 = 33.3333333333...%. Раньше мы допускали неточность и указывали ширину как 33%. Теперь можно использовать `calc()` и пусть браузер сам считает.

```css
/* при отрисовке страницы браузер сам высчитает и подставит значение */
.selector {
  width: calc(100% / 3);
}
```

Но лучше не перегружать браузер расчётами. На каждую операцию он тратит некую долю секунды и часть оперативной памяти. Если расчётов будет много, то это потенциально повлияет на скорость загрузки страницы. Используйте `calc()` с умом.

## Как пишется

В круглых скобках мы можем писать любые математические операции с любыми единицами измерения, доступными в вебе (%, px, rem, em, vw, vh, vmin и т.д.). Доступны четыре стандартных операнда:

- `+` — сложение
- `-` — вычитание
- `/` — деление
- `*` — умножение

Операторы сложения и вычитания обязательно с двух сторон должны отбиваться пробелом. Иначе браузер воспримет их как часть числа. Хоть операторы деления и умножения не требуют такой строгости к себе, но принято и их тоже отбивать пробелами для удобства чтения.

```css
/* 👍 */
.selector {
  width: calc(100% - 2rem);
}

/* 👎 */
.selector {
  width: calc(100% -2rem);
}
```

Внутри скобок может быть больше одного вычисления, можно группировать операции при помощи скобок. Всё как в **настоящем** языке программирования 😺 Но не стоит увлекаться, чем короче вычисление, тем проще потом его прочитать и понять что там вообще происходит.

Для каких свойств можно указать `calc()` в качестве значения? Для любых, значением которых должна быть цифра! Причём если свойство предполагает составное значение, то можно указать функцию как часть этого значения:

```css
.selector {
  margin: calc(5vh / 4) 20px;
  transition: transform calc(0.5s + 120ms);
}
```

Внутри круглых скобок можно складывать только числовые значения. Нельзя сложить число со строкой, хотя в полноценных языках программирования, типа JavaScript, такой трюк с лёгкостью бы удался.

Ещё одно неудачное место для этой функции — медиавыражения. Вот такая запись считается не валидной:

```css
@media (min-width: calc(465px + 1vw)) {
  ...;
}
```

Хотя бы у одной из цифр внутри скобок нужно указать единицу измерения, иначе браузер не сможет понять, от чего же вести вычисление.

## Как это понять

Во время отрисовки (рендеринга) страницы браузер заглядывает в CSS и производит все вычисления из функций `calc()`, подставляя на их место итоговое значение. Исходя из этих значений и отрисовываются стили элементов.

## Подсказки

💡 Очень удобно (и часто приходится) использовать, когда из одной величины в относительных единицах надо вычесть другую величину в абсолютных единицах. Самостоятельно это никак не посчитать, а браузеру раз плюнуть.

```css
/* Сколько будет? */
.selector {
  height: calc(100vh - 34px);
}
```
