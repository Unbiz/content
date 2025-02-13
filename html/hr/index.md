---
title: "`<hr>`"
authors:
  - lenaryan
keywords:
  - тэг
  - тег
  - разделитель
  - горизонтальная черта
  - hr
  - "<hr>"
tags:
  - doka
---

## Кратко

Та самая горизонтальная черта, которая разделяет смысловые блоки на странице.

## Пример

Разделим два абзаца горизонтальной чертой и немного стилизуем её.

```html
<p>Первый абзац</p>
<hr>
<p>Второй абзац</p>
```

```css
hr {
  width: 80%;
  margin: 20px auto;
  border: 2px dashed cornflowerblue;
}
```

<iframe title="Горизонтальная линия" src="demos/hr/" height="200"></iframe>

## Как это понять

Тег `<hr>` помогает отделить независимые друг от друга блоки — например, подразделы в статье. Это блочный элемент, поэтому он встаёт в отдельном ряду, визуально разделяя информацию на странице.

## Как пишется

Одиночный тег, который не нужно закрывать — просто ставим `<hr>` в том месте, где нужен разделитель.
