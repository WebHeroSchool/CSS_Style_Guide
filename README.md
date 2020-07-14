# WebHero CSS Style Guide

В данном руководстве описаны подходы по оформлению CSS. Данное руководство не является железным правилом для всех проектов во frontend, а только рекомендации для разработки проектов в нашей школе :slightly_smiling_face: На вашей работе могут быть другие правила. Все правила обсуждаются и согласовываются участниками команды и придерживаются их на протяжении разработки всего проекта.

&nbsp;
## Содержание

1. [Отступы, 2 или 4 пробела](#отступы-2-или-4-пробела)
2. [Точка с запятой](#точка-с-запятой)
3. [В строку или в столбик](#в-строку-или-в-столбик)
4. [: или :: для псевдоэлементов](#-или-для-псевдоэлементов)
5. [Пустые блоки](#пустые-блоки)
6. [Ноль, что с ним делать](#ноль-что-с-ним-делать)
7. [Специфичность](#специфичность)
8. [Шрифты](#шрифты)
9. [Строчные или заглавные буквы](#строчные-или-заглавные-буквы)
10. [Короткое или длинное название шестнадцатеричных цветов](#короткое-или-длинное-название-шестнадцатеричных-цветов)
11. [Пустая строка (Enter)](#пустая-строка-Enter)
12. [Пробелы](#пробелы)
13. [Дублирование](#дублирование)
14. [Использование только известных названий/имен/свойств и тд](#использование-только-известных-названийименсвойств-и-тд)
15. [Комментарии](#комментарии)
16. [!important в @keyframes](#important-в-keyframes)


&nbsp;

## Отступы, 2 или 4 пробела.

&nbsp;
#### 1. Всегда делай отступ в два пробела. (если ты пользуешься табом, то его можно также настроить на отступ в два пробела).

> stylelint: [`indentation`](https://stylelint.io/user-guide/rules/indentation#indentation)

&nbsp;

❌ не надо так 👇
```css
@media print {
a {
background-position: top left,
top right;
}
}

@media print {
a {
  background-position: top left,
    top right;
  }
}

@media print {
  a {
    background-position: top left,
    top right;
  }
}

@media print {
  a,
    b {
    background-position: top left,
      top right;
  }
}

a {
/* blergh */
  color: pink;
}
  /* blergh */

@media print,
(-webkit-min-device-pixel-ratio: 1.25),
(min-resolution: 120dpi) {}

a {
  color: rgb(
  255,
  255,
  255
  );
  top: 0;
}
 ```

&nbsp;

✅ надо так 👇
 ```css
@media print {
  a {
    background-position: top left,
      top right;
  }
}

@media print {
  a,
  b {
    background-position: top left,
      top right;
  }
}

a {
  /* blergh */
  color: pink;
}
/* blergh */

@media print,
  (-webkit-min-device-pixel-ratio: 1.25),
  (min-resolution: 120dpi) {}

a {
  color: rgb(
    255,
    255,
    255
  );
  top: 0;
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Точка с запятой.

&nbsp;
#### 1. Всегда ставь точку с запятой у последнего свойства в блоке.

> stylelint: [`declaration-block-trailing-semicolon`](https://stylelint.io/user-guide/rules/declaration-block-trailing-semicolon#declaration-block-trailing-semicolon)

&nbsp;

❌ не надо так 👇
```css
a { color: pink }
a { background: orange; color: pink }
a { @include foo }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
a { background: orange; color: pink; }
a { @include foo; }
```
&nbsp;
#### 2. Не ставь лишние точки с запятой.

> stylelint: [`no-extra-semicolons`](https://stylelint.io/user-guide/rules/no-extra-semicolons#no-extra-semicolons)

&nbsp;

❌ не надо так 👇
```css
@import "x.css";;
@import "x.css";
;
a {
  color: pink;;
}

a {
  ;color: pink;
}

a {
  color: pink;
  ;
}

a {
  color: red;
}
;
b {
  color: white;
}
```

&nbsp;

✅ надо так 👇
```css
@import "x.css";

a {
  color: pink;
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## В строку или в столбик.

&nbsp;
#### 1. Если свойств несколько, лучше писать их в столбик.

> stylelint: [`declaration-block-single-line-max-declarations`](https://stylelint.io/user-guide/rules/declaration-block-single-line-max-declarations#declaration-block-single-line-max-declarations)

&nbsp;

Такая запись более удобна для восприятия.

&nbsp;

❌ не надо так 👇
```css
a { color: pink; top: 3px; }

a,
b { color: pink; top: 3px; }
```

&nbsp;

✅ надо так 👇
```css
b { color: pink; }

a {
  color: pink;
  top: 3px;
}
```
&nbsp;
#### 2. В многострочных блоках пиши каждое свойство с новой строки(в столбик).

> stylelint: [`declaration-block-semicolon-newline-after`](https://stylelint.io/user-guide/rules/declaration-block-semicolon-newline-after)

&nbsp;

❌ не надо так 👇
```css
a {
  color: pink; top: 0;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  color: pink;
  top: 0;
}
```
&nbsp;
#### 3. Перечисляй селекторы в столбик (после запятой начинай с новой строки).

> stylelint: [`selector-list-comma-newline-after`](https://stylelint.io/user-guide/rules/selector-list-comma-newline-after#selector-list-comma-newline-after)

&nbsp;

❌ не надо так 👇
```css
a, b { color: pink; }

a
, b { color: pink; }
```

&nbsp;

✅ надо так 👇
```css
a,
b { color: pink; }

a
,
b { color: pink; }
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## : или :: для псевдоэлементов.

&nbsp;
#### Используй двойное двоеточие для псевдоэлементов.

> stylelint: [`selector-pseudo-element-colon-notation`](https://stylelint.io/user-guide/rules/selector-pseudo-element-colon-notation#selector-pseudo-element-colon-notation)

&nbsp;

❌ не надо так 👇
```css
a:before { color: pink; }
a:after { color: pink; }
a:first-letter { color: pink; }
a:first-line { color: pink; }
```

&nbsp;

✅ надо так 👇
```css
a::before { color: pink; }
a::after { color: pink; }
a::first-letter { color: pink; }
a::first-line { color: pink; }
input::placeholder { color: pink; }
li::marker { font-variant-numeric: tabular-nums; }
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Пустые блоки.

&nbsp;
#### Не оставляй пустые блоки со стилями.

> stylelint: [`block-no-empty`](https://stylelint.io/user-guide/rules/block-no-empty#block-no-empty)

&nbsp;

❌ не надо так 👇
```css
a {}

a { }

@media print {
  a {}
}
```

&nbsp;

✅ надо так 👇
```css
a {
  /* foo */
}
@media print {
  a {
    color: pink;
  }
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Ноль, что с ним делать.

&nbsp;
#### 1. Не ставь ведущий ноль у дробных чисел.

> stylelint: [`number-leading-zero`](https://stylelint.io/user-guide/rules/number-leading-zero#number-leading-zero)

&nbsp;

❌ не надо так 👇
```css
a { line-height: 0.5; }
a { transform: translate(2px, 0.4px); }
```

&nbsp;

✅ надо так 👇
```css
a { line-height: .5; }
a { transform: translate(2px, .4px); }

```
&nbsp;
#### 2. Не ставь единицы измерения длины, если значение нулевое.

> stylelint: [`length-zero-no-unit`](https://stylelint.io/user-guide/rules/length-zero-no-unit#length-zero-no-unit)

&nbsp;

Длина - это измерение , которое представляет собой число, за которым сразу следует идентификатор единицы измерения . Однако для нулевой длины идентификатор единицы является необязательным. Единицы длины: em, ex, ch, vw, vh, cm, mm, in, pt, pc, px, rem, vmin, и vmax.

&nbsp;

❌ не надо так 👇
```css
a { top: 0px }
a { top: 0.000em }
```

&nbsp;

✅ надо так 👇
```css
a { top: 0 } /* нет единицы */
a { transition-delay: 0s; } /* измерение*/
a { top: 2in; }
a { top: 1.001vh }
```
&nbsp;
#### 3. Не ставь нули в конце чисел, если они не несут смысла.

> stylelint: [`number-no-trailing-zeros`](https://stylelint.io/user-guide/rules/number-no-trailing-zeros#number-no-trailing-zeros)

&nbsp;

❌ не надо так 👇
```css
a { top: 1.0px }
a { top: 1.01000px }
```

&nbsp;

✅ надо так 👇
```css
a { top: 1px }
a { top: 1.01px }
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Специфичность.

&nbsp;
#### 1. Не пиши селекторы с меньшей специфичностью после селекторов с большей специфичностью.

> stylelint: [`no-descending-specificity`](https://stylelint.io/user-guide/rules/no-descending-specificity#no-descending-specificity)

&nbsp;

Когда два селектора имеют одинаковую специфичность, приоритет имеет тот , который появляется последним . Однако ситуация отличается, когда один из селекторов имеет более высокую специфичность. В этом случае исходный порядок не имеет значения: селектор с более высокой специфичностью победит, даже если он появится первым.

&nbsp;

❌ не надо так 👇
```css
b a {}
a {}
 
a + a {}
a {}
 
b > a[foo] {}
a[foo] {}
 
a {
  & > b {}
}
b {}
 
@media print {
  #c a {}
  a {}
}
```

&nbsp;

✅ надо так 👇
```css
a {}
b a {}
 
a {}
a + a {}
 
 
a[foo] {}
b > a[foo] {}
 
b {}
a {
  & > b {}
}
 
a::before {}
a:hover::before {}
a {}
a:hover {}
 
@media print {
  a {}
  #c a {}
}
 
a {}
@media print {
  #baz a {}
}
```
&nbsp;
#### 2. Не пиши сокращенные свойства  после связных свойств.

> stylelint: [`declaration-block-no-shorthand-property-overrides`](https://stylelint.io/user-guide/rules/declaration-block-no-shorthand-property-overrides#declaration-block-no-shorthand-property-overrides)

&nbsp;

Сокращенные свойства могут переопределить связные свойства.

&nbsp;

 ❌ не надо так 👇
```css
a {
  padding-left: 10px;
  padding: 20px;
}
 
a {
  transition-property: opacity;
  transition: opacity 1s linear;
}
 
a {
  -webkit-transition-property: opacity;
  -webkit-transition: opacity 1s linear;
}
 
a {
  border-top-width: 1px;
  top: 0;
  bottom: 3px;
  border: 2px solid blue;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  padding: 10px;
  padding-left: 20px;
}
 
a {
  transition-property: opacity;
}

a {
  transition: opacity 1s linear;
}
 
a {
  transition-property: opacity;
  -webkit-transition: opacity 1s linear;
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

# Шрифты.

&nbsp;
#### Ставь всегда тип шрифта(serif, sans-serif, cursive, fantasy или monospace).

> stylelint: [`font-family-no-missing-generic-family-keyword`](https://stylelint.io/user-guide/rules/font-family-no-missing-generic-family-keyword#font-family-no-missing-generic-family-keyword)

&nbsp;

Тип шрифта:
- может стоять в любом месте в списке шрифтов;
- может быть опущен, если используется ключевое слово, связанное с наследованием свойств или системным шрифтом.

&nbsp;

❌ не надо так 👇
```css
a { font-family: Helvetica, Arial, Verdana, Tahoma; }
a { font: 1em/1.3 Times; }
```

&nbsp;

✅ надо так 👇
```css
a { font-family: Helvetica, Arial, Verdana, Tahoma, sans-serif; }
a { font: 1em/1.3 Times, serif, Apple Color Emoji; }
a { font: inherit; }
a { font: caption; }
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Строчные или заглавные буквы.

&nbsp;
#### 1. Называй at-rules (правила) строчными буквами.

> stylelint: [`at-rule-name-case`](https://stylelint.io/user-guide/rules/at-rule-name-case#at-rule-name-case)

&nbsp;

 ❌ не надо так 👇
```css
@Charset "UTF-8";
@cHarSeT "UTF-8";
@CHARSET "UTF-8";
@Media (min-width: 50em) {}
@mEdIa (min-width: 50em) {}
@MEDIA (min-width: 50em) {}
```

&nbsp;

✅ надо так 👇
```css
@charset "UTF-8";
@media (min-width: 50em) {}
```
&nbsp;
#### 2. Называй функции строчными буквами.

> stylelint: [`function-name-case`](https://stylelint.io/user-guide/rules/function-name-case#function-name-case)

&nbsp;

 ❌ не надо так 👇
```css
a {
  width: Calc(5% - 10em);
}
a {
  width: cAlC(5% - 10em);
}
a {
  width: CALC(5% - 10em);
}
a {
  background: -WEBKIT-RADIAL-GRADIENT(red, green, blue);
}
```

&nbsp;

✅ надо так 👇
```css
a {
  width: calc(5% - 10em);
}
a {
  background: -webkit-radial-gradient(red, green, blue);
}
```
&nbsp;
#### 3. Для цветов в шестнадцетиричном формате используй строчные буквы.

> stylelint: [`color-hex-case`](https://stylelint.io/user-guide/rules/color-hex-case#color-hex-case)

&nbsp;

❌ не надо так 👇
```css
a { color: #FFF; }
```

&nbsp;

✅ надо так 👇
```css
a { color: #000; }
a { color: #fff; }
```
&nbsp;
#### 4. Для названий медиа-запрсов используй строчные буквы.

> stylelint: [`media-feature-name-case`](https://stylelint.io/user-guide/rules/media-feature-name-case#media-feature-name-case)

&nbsp;

❌ не надо так 👇
```css
@media (MIN-WIDTH: 700px) {}
@media not all and (MONOCHROME) {}
@media (min-width: 700px) and (ORIENTATION: landscape) {}
@media (WIDTH > 10em) {}
```

&nbsp;

✅ надо так 👇
```css
@media (min-width: 700px) {}
@media not all and (monochrome) {}
@media (min-width: 700px) and (orientation: landscape) {}
@media (width > 10em) {}
```
&nbsp;
#### 5. Пиши свойства строчными буквами.

> stylelint: [`property-case`](https://stylelint.io/user-guide/rules/property-case#property-case)

&nbsp;

❌ не надо так 👇
```css
a {
  Width: 1px
}
a {
  WIDTH: 1px
}
a {
  widtH: 1px
}
a {
  border-Radius: 5px;
}
a {
  -WEBKIT-animation-duration: 3s;
}
@media screen and (orientation: landscape) {
  WiDtH: 500px;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  width: 1px
}
a {
  border-radius: 5px;
}
a {
  -webkit-animation-duration: 3s;
}
@media screen and (orientation: landscape) {
  width: 500px;
}
```
&nbsp;
#### 6. Используй строчные буквы для селекоторов псевдоклассов.

> stylelint: [`selector-pseudo-class-case`](https://stylelint.io/user-guide/rules/selector-pseudo-class-case#selector-pseudo-class-case)

&nbsp;

❌ не надо так 👇
```css
a:Hover {}
a:hOvEr {}
a:HOVER {}
:ROOT {}
:-MS-INPUT-PLACEHOLDER {}
```

&nbsp;

✅ надо так 👇
```css
a:hover {}
:root {}
:-ms-input-placeholder {}
```
&nbsp;
#### 7. Используй строчные буквы для селекоторов псевдоэлементов.

> stylelint: [`selector-pseudo-element-case`](https://stylelint.io/user-guide/rules/selector-pseudo-element-case#selector-pseudo-element-case)

&nbsp;

❌ не надо так 👇
```css
a:Before {}
a:bEfOrE {}
a:BEFORE {}
a::Before {}
a::bEfOrE {}
a::BEFORE {}
input::-MOZ-PLACEHOLDER {}
```

&nbsp;

✅ надо так 👇
```css
a:before {}
a::before {}
input::-moz-placeholder {}
```
&nbsp;
#### 8. Используй строчные буквы для типов селекторов.

> stylelint: [`selector-type-case`](https://stylelint.io/user-guide/rules/selector-type-case#selector-type-case)

&nbsp;

❌ не надо так 👇
```css
A {}
LI {}
```

&nbsp;

✅ надо так 👇
```css
a {}
li {}
```
&nbsp;
#### 9. Используй строчные буквы для единиц измерени.

> stylelint: [`unit-case`](https://stylelint.io/user-guide/rules/unit-case#unit-case)

&nbsp;

❌ не надо так 👇
```css
a {
  width: 10PX;
}
a {
  width: 10Px;
}
a {
  width: 10pX;
}
a {
  width: 10PIXEL;
}
a {
  width: calc(10PX * 2);
}
```

&nbsp;

✅ надо так 👇
```css
a {
  width: 10px;
}
a {
  width: calc(10px * 2);
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Короткое или длинное название шестнадцатеричных цветов.

&nbsp;
#### Используй короткие обозначения шестнадцатеричных цветов.

> stylelint: [`color-hex-length`](https://stylelint.io/user-guide/rules/color-hex-length#color-hex-length)

&nbsp;

❌ не надо так 👇
```css
a { color: #ffffff; }
a { color: #ffffffaa; }
```

&nbsp;

✅ надо так 👇
```css
a { color: #fff; }
a { color: #fffa; }
a { color: #a4a4a4; }
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Пустая строка (Enter).

&nbsp;
#### 1. Пустая строка перед at-rules (правилами):

> stylelint: [`at-rule-empty-line-before`](https://stylelint.io/user-guide/rules/at-rule-empty-line-before#at-rule-empty-line-before)

&nbsp;
- всегда оставляй пустую строку.

&nbsp;  
  
❌ не надо так 👇
```css
a {} @media {}
a {}
@media {}
```

&nbsp;

✅ надо так 👇
```css
a {}

@media {}
```
&nbsp;

**Исключения:**

- можно группировать свой правила по имени в блоки;

&nbsp;

✅ надо так 👇
```css
@charset "UTF-8";

@import url(x.css);
@import url(y.css);

@charset "UTF-8";

@import url(x.css); /* comment */
@import url(y.css);

a {

  @extends .foo;
  @extends .bar;

  @include loop;
  @include doo;
}
```

&nbsp;
- если правило вложено в блок и стоит первым, то пустую строку не оставляем;

&nbsp;

❌ не надо так 👇
```css
a {

  @extend foo;
  color: pink;
}

b {
  color: pink;
  @extend foo;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  @extend foo;
  color: pink;
}

b {
  color: pink;

  @extend foo;
}
```
&nbsp;
- если правило следует за комментарием, то новую строку можно не ставить.

&nbsp;

✅ надо так 👇
```css
/* comment */
@media {}

@media {} /* comment */
```
&nbsp;
#### 2. Пустая строка перед комментарием:

> stylelint: [`comment-empty-line-before`](https://stylelint.io/user-guide/rules/comment-empty-line-before#comment-empty-line-before)

&nbsp;
- всегда оставлять пустую строку.

&nbsp;

❌ не надо так 👇
```css
a {}
/* comment */
```

&nbsp;

✅ надо так 👇
```css
a {}

/* comment */

a {} /* comment */
```
&nbsp;

**Исключения:**

- если комментарий вложен в блок и стоит первым в блоке, пустую строку оставлять не надо;

&nbsp;

❌ не надо так 👇
```css
a {

  /* comment */
  color: pink;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  /* comment */
  color: pink;
}
```

&nbsp;
- игнорируй комментарии, которые являются командами к stylelint.

&nbsp;

❌ не надо так 👇
```css
a {
  background: pink;
  /* не команда stylelint */
  color: #eee;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  background: pink;
  /* stylelint-disable color-no-hex */
  color: pink;
}
```
&nbsp;
#### 3. Пустая строка перед пользовательскими свойствами (CSS переменные):

> stylelint: [`custom-property-empty-line-before`](https://stylelint.io/user-guide/rules/custom-property-empty-line-before#custom-property-empty-line-before)

&nbsp;
- всегда оставляй пустую строку перед пользовательским свойствами.

&nbsp;

❌ не надо так 👇
```css
a {
  top: 10px;
  -foo: pink;
  -bar: red;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  top: 10px;

  -foo: pink;

  -bar: red;
}
```
&nbsp;

**Исключения:**

- если пользовательские свойства следуют друг за другом, то не нужно оставлять пустую строку;

&nbsp;

 ❌ не надо так 👇
```css
a {

  -foo: pink;

  -bar: red;
}

a {

  -foo: pink; /* comment */

  -bar: red;
}
```

&nbsp;

✅ надо так 👇
```css
a {

  -foo: pink;
  -bar: red;
}

a {

  -foo: pink; /* comment */
  -bar: red;
}
```
&nbsp;
- перед вложенными пользовательскими свойствами, которые стоят первыми в блоке свойств не нужно оставлять пустую строку;

&nbsp;

 ❌ не надо так 👇
```css
a {

  -foo: pink;

  -bar: red;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  -foo: pink;

  -bar: red;
}
```
&nbsp;
- не оставляй пустую строку, если свойство идет после комментария;

&nbsp;

✅ надо так 👇
```css
a {
  /* comment */
  -foo: pink;
}
```

&nbsp;
- данное правило игнорируется для пользовательских свойств, которые находятся внутри однострочных блоков.

&nbsp;

✅ надо так 👇
```css
a { -foo: pink; -bar: red; }
```
&nbsp;
#### 4. Пустая строка перед простыми свойствами:

> stylelint: [`declaration-empty-line-before`](https://stylelint.io/user-guide/rules/declaration-empty-line-before#declaration-empty-line-before)

&nbsp;

- оставляй пустую строку.

&nbsp;

❌ не надо так 👇
```css
a {
  -foo: pink;
  top: 5px;
}

a {
  bottom: 15px;
  top: 5px;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  -foo: pink;

  top: 5px;
}

a {

  bottom: 15px;

  top: 5px;
}
```
&nbsp;

**Исключения:**

- Если простое свойство следует за другим простым свойством, пустая строка не нужна. Комментарии не влияют на правило;

&nbsp;

❌ не надо так 👇
```css
a {

  bottom: 15px;

  top: 5px;
}

a {

  bottom: 15px; /* comment */

  top: 5px;
}
```

&nbsp;

✅ надо так 👇
```css
a {

  bottom: 15px;
  top: 5px;
}

a {

  bottom: 15px; /* comment */
  top: 5px;
}
```
&nbsp;
- перед вложенными блоками, которые идут первыми в блоке, пустая строка не требуется;

&nbsp;

 ❌ не надо так 👇
```css
a {

  bottom: 15px;

  top: 5px;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  bottom: 15px;

  top: 5px;
}
```
&nbsp;
- если свойство идет за комментарием, пустая строка не требуется;

&nbsp;

✅ надо так 👇
```css
a {
  /* comment */
  bottom: 15px;
}
```
&nbsp;
- правило игнорируется для свойств, написанных в строку.

&nbsp;

✅ надо так 👇
```css
a { bottom: 15px; top: 5px; }
```
&nbsp;
#### 5. Пустая строка перед блоками свойств:

> stylelint: [`rule-empty-line-before`](https://stylelint.io/user-guide/rules/rule-empty-line-before#rule-empty-line-before)

&nbsp;

- оставляй пустую строку перед многострочными блоками.

&nbsp;

 ❌ не надо так 👇
```css
a {
  color: red;
}
b {
  color: blue;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  color: red;
}

b {
  color: blue;
}
```
&nbsp;

**Исключения:**

- если блок вложен и стоит первым, то перед ним не нужно оставлять пустую строку;

&nbsp;

 ❌ не надо так 👇
```css
@media {

  a {}

  b {}
}
```

&nbsp;

✅ надо так 👇
```css
@media {
  a {}

  b {}
}
```
&nbsp;
- если блок стоит после комментария, то пустая строка не нужна.

&nbsp;

✅ надо так 👇
```css
/* comment */
a {}
```
&nbsp;
#### 6. Не оставляй пустую строку перед закрывающей фигурной скобкой.

> stylelint: [`block-closing-brace-empty-line-before`](https://stylelint.io/user-guide/rules/block-closing-brace-empty-line-before#block-closing-brace-empty-line-before)

&nbsp;

 ❌ не надо так 👇
```css
a {
  color: pink;

}
```

&nbsp;

✅ надо так 👇
```css
a {
  color: pink;
}

a { color: pink; }
```
&nbsp;
#### 7. Не ставь лишние  смежные пустые строки в функциях, селекторах, списках значений.

> stylelint: [`function-max-empty-lines`](https://stylelint.io/user-guide/rules/function-max-empty-lines#function-max-empty-lines),
>[`selector-max-empty-lines`](https://stylelint.io/user-guide/rules/selector-max-empty-lines#selector-max-empty-lines),
>[`value-list-max-empty-lines`](https://stylelint.io/user-guide/rules/value-list-max-empty-lines#value-list-max-empty-lines)

&nbsp;

 ❌ не надо так 👇
```css
a {
  transform:
    translate(

      1,
      1
    );
}

a,

b {
  color: red;
}
a {
  padding:
    10px
    10px
    10px

    10px
}
```

&nbsp;

✅ надо так 👇
```css
a {
  transform:
    translate(
      1,
      1
    );
}
a,
b {
  color: red;
}
a {
  padding: 10px
    10px
    10px
    10px
}
```
&nbsp;
#### 8. Ограничь число смежных пустых строк в таблице стилей.

> stylelint: [`max-empty-lines`](https://stylelint.io/user-guide/rules/max-empty-lines#max-empty-lines)

&nbsp;

 ❌ не надо так 👇
```css
a {}



b {}
//Также относится к комментариям
/*
 Call me Ishmael.



 Some years ago - never mind how log precisely - ...
 */
```

&nbsp;

✅ надо так 👇
```css
a {}
b {}

a {}

b {}
```
&nbsp;
#### 9. После открывающей фигурной скобки в многострочных блоках начинай писать свойства с новой строки.

> stylelint: [`block-opening-brace-newline-after`](https://stylelint.io/user-guide/rules/block-opening-brace-newline-after#block-opening-brace-newline-after)

&nbsp;

 ❌ не надо так 👇
```css
a{color: pink;
}
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }

a {
color: pink; }
```
&nbsp;
#### 10. После точки с запятой в at-rules (правила) начинай писать с новой строки.

> stylelint: [`at-rule-semicolon-newline-after`](https://stylelint.io/user-guide/rules/at-rule-semicolon-newline-after#at-rule-semicolon-newline-after)

&nbsp;

❌ не надо так 👇
```css
@import url("x.css"); @import url("y.css");
@import url("x.css"); a {}
```

&nbsp;

✅ надо так 👇
```css
@import url("x.css");
@import url("y.css");

@import url("x.css"); /* end-of-line comment */
a {}

@import url("x.css");

a {}
```
&nbsp;
#### 11. После закрывающей фигурной скобки в блоке начинай следующую запись с новой строки.

> stylelint: [`block-closing-brace-newline-after`](https://stylelint.io/user-guide/rules/block-closing-brace-newline-after#block-closing-brace-newline-after)

&nbsp;

❌ не надо так 👇
```css
a { color: pink; }b { color: red; }
a { color: pink;
} b { color: red; }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
b { color: red; }
```
&nbsp;
#### 12. В многострочных функциях в скобках ставь символ новой строки после открывающей и перед закрывающей скобкой.

> stylelint: [`function-parentheses-newline-inside`](https://stylelint.io/user-guide/rules/function-parentheses-newline-inside#function-parentheses-newline-inside)

&nbsp;

❌ не надо так 👇
```css
a { transform: translate(1,
  1) }
```

&nbsp;

✅ надо так 👇
```css
a { transform: translate(1, 1) }

a { transform: translate( 1, 1 ) }

a {
  transform: translate(
    1, 1
  );
}

a {
  transform: translate(
    1,
    1
  );
}
```
&nbsp;
#### 13. В многострочных функциях после запятой начинай писать с новой строки.

> stylelint: [`function-comma-newline-after`](https://stylelint.io/user-guide/rules/function-comma-newline-after#function-comma-newline-after)

&nbsp;

❌ не надо так 👇
```css
a { transform: translate(1
  ,1) }
```

&nbsp;

✅ надо так 👇
```css
a { transform: translate(1,1) }
a { transform: translate(1 ,1) }

a {
  transform: translate(1,
    1)
}
```
&nbsp;
#### 14. В многострочных списках медиа-запросов всегда должен быть символ новой строки после запятых.

> stylelint: [`media-query-list-comma-newline-after`](https://stylelint.io/user-guide/rules/media-query-list-comma-newline-after#media-query-list-comma-newline-after)

&nbsp;

❌ не надо так 👇
```css
@media screen and (color)
, projection and (color) {}
```

&nbsp;

✅ надо так 👇
```css
@media screen and (color), projection and (color) {}

@media screen and (color),
projection and (color) {}

@media screen and (color)
,
projection and (color) {}
```
&nbsp;
#### 15. В многострочных списках значений свойства начинай писать с новой строки после запятой.

> stylelint: [`value-list-comma-newline-after`](https://stylelint.io/user-guide/rules/value-list-comma-newline-after#value-list-comma-newline-after)

&nbsp;

❌ не надо так 👇
```css
a { background-size: 0
    , 0; }
```

&nbsp;

✅ надо так 👇
```css
a { background-size: 0, 0; }
a { background-size: 0,0; }
a { background-size: 0,
      0; }
```
&nbsp;
#### 16. В многострочных блоках свойств закрывающая фигурная скобка должна быть на новой строке.

> stylelint: [`block-closing-brace-newline-before`](https://stylelint.io/user-guide/rules/block-closing-brace-newline-before)

&nbsp;

❌ не надо так 👇
```css
a {
color: pink;}
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
a { color: pink;
}
```
&nbsp;
#### 16. Если свойство многострочное, после двоеточия начинай писать с новой строки.

> stylelint: [`declaration-colon-newline-after`](https://stylelint.io/user-guide/rules/declaration-colon-newline-after#declaration-colon-newline-after)

&nbsp;

❌ не надо так 👇
```css
a {
  box-shadow: 0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```

&nbsp;

✅ надо так 👇
```css
a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}

a {
  color: pink;
}
```
&nbsp;
#### 17. Не переноси непрерывные строки без использования экранирующего символа ‘\ ’.

> stylelint: [`string-no-newline`](https://stylelint.io/user-guide/rules/string-no-newline)

&nbsp;

❌ не надо так 👇
```css
a {
  content: "first
    second";
}

[title="something
is probably wrong"] {}

a {
  font-family: "Times
    New
    Roman";
}
```

&nbsp;

✅ надо так 👇
```css
a {
  content: "first\Asecond";
}

a {
  content: "first\\nsecond";
}

[title="nothing\
  is wrong"] {}

a {
  font-family: "Times New Roman";
}
```
&nbsp;
#### 18. Не оставляй пустые строки с пробелами, отступами, переносом строки.

> stylelint: [`no-empty-source`](https://stylelint.io/user-guide/rules/no-empty-source#no-empty-source)

&nbsp;

Строка, содержащая только пробелы является пустой.

&nbsp;

❌ не надо так 👇
```css


\t\t
\n
```

&nbsp;

✅ надо так 👇
```css
a {}
/* Only comments */
```
&nbsp;
#### 19. Оставляй пустую строку в конце блока.

> stylelint: [`no-missing-end-of-source-newline`](https://stylelint.io/user-guide/rules/no-missing-end-of-source-newline)

&nbsp;

❌ не надо так 👇
```css
a { color: pink; }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
\n
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Пробелы.

&nbsp;
#### 1. Не ставь пробелы в конце строки.

> stylelint: [`no-eol-whitespace`](https://stylelint.io/user-guide/rules/no-eol-whitespace#no-eol-whitespace)

&nbsp;

❌ не надо так 👇
```css
a { color: pink; }····
a { color: pink; }···
···

/* Также это относится и к многострочным комментариям */

/* something····
 * something else */
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }

/* something
 * something else */
```
&nbsp;
#### 2. Ставь один пробел между комбинаторами.

> stylelint: [`selector-descendant-combinator-no-non-space`](https://stylelint.io/user-guide/rules/selector-descendant-combinator-no-non-space#selector-descendant-combinator-no-non-space)

&nbsp;

❌ не надо так 👇
```css
.foo  .bar {}
.foo
.bar {}
```

&nbsp;

✅ надо так 👇
```css
.foo .bar {}
```
&nbsp;
#### 3. В calc функциях ставь пробел перед и после оператора.

> stylelint: [`function-calc-no-unspaced-operator`](https://stylelint.io/user-guide/rules/function-calc-no-unspaced-operator)

&nbsp;

Перед оператором должен быть один пробел.

После оператора должен быть один пробел.

&nbsp;

❌ не надо так 👇
```css
a { top: calc(1px+2px); }
a { top: calc(1px+ 2px); }
```

&nbsp;

✅ надо так 👇
```css
a { top: calc(1px + 2px); }
a { top: calc(calc(1em * 2) / 3); }
a {
  top: calc(var(-foo) +
    var(-bar));
}
a {
  top: calc(var(-foo)
    + var(-bar));
}
```
&nbsp;
#### 4. Не ставь пробел перед точкой с запятой в блоках со свойствами.

> stylelint: [`declaration-block-semicolon-space-before`](https://stylelint.io/user-guide/rules/declaration-block-semicolon-space-before#declaration-block-semicolon-space-before)

&nbsp;

❌ не надо так 👇
```css
a { color: pink ; }
a { color: pink ; top: 0 ; }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
a { color: pink; top: 0; }
```
&nbsp;
#### 5. Не ставь пробелы после открывающей квадратной скобки и перед закрывающей квадратной скобкой в селекторах атрибутов.

> stylelint: [`selector-attribute-brackets-space-inside`](https://stylelint.io/user-guide/rules/selector-attribute-brackets-space-inside#selector-attribute-brackets-space-inside)

&nbsp;

❌ не надо так 👇
```css
[ target] {}
[target ] {}
[ target ] {}
[ target=_blank] {}
[target=_blank ] {}
[ target=_blank ] {}
```

&nbsp;

✅ надо так 👇
```css
[target] {}
[target=_blank] {}
```
&nbsp;
#### 6. Не ставь пробелы после и перед круглой скобкой в однострочных функциях.

> stylelint: [`function-parentheses-space-inside`](https://stylelint.io/user-guide/rules/function-parentheses-space-inside#function-parentheses-space-inside)

&nbsp;

❌ не надо так 👇
```css
a { transform: translate( 1, 1 ) }
a { transform: translate(1, 1 ) }
```

&nbsp;

✅ надо так 👇
```css
a { transform: translate(1, 1) }
a { transform: translate( 1,
  1) }
a {
  transform: translate(
    1,
    1
  )
}
```
&nbsp;
#### 7. Не ставь пробелы внутри круглых скобок в медиа-запросах.

> stylelint: [`media-feature-parentheses-space-inside`](https://stylelint.io/user-guide/rules/media-feature-parentheses-space-inside#media-feature-parentheses-space-inside)

&nbsp;

❌ не надо так 👇
```css
@media ( max-width: 300px ) {}
@media ( max-width: 300px) {}
```

&nbsp;

✅ надо так 👇
```css
@media (max-width: 300px) {}
```
&nbsp;
#### 8. Всегда ставь пробел после функции.

> stylelint: [`function-whitespace-after`](https://stylelint.io/user-guide/rules/function-whitespace-after#function-whitespace-after)

&nbsp;

❌ не надо так 👇
```css
a { transform: translate(1, 1)scale(3); }
```

&nbsp;

✅ надо так 👇
```css
a { transform: translate(1, 1) scale(3); }
a { transform: translate(1, 1)     scale(3); }
a {
  transform:
    translate(1, 1)
    scale(3);
}

/* обратите внимание на две закрывающие скобки без пробела */
a { top: calc(1 * (1 + 3)); }

/* обратите внимание на ) без пробела после закрывающей скобки*/
a { padding: calc(1 * 2px), calc(2 * 5px); }
```
&nbsp;
#### 9. Не ставь пробелы внутри круглых скобок в селекторах псевдоклассов.

> stylelint: [`selector-pseudo-class-parentheses-space-inside`](https://stylelint.io/user-guide/rules/selector-pseudo-class-parentheses-space-inside#selector-pseudo-class-parentheses-space-inside)

&nbsp;

❌ не надо так 👇
```css
input:not( [type="submit"] ) {}
input:not( [type="submit"]) {}
```

&nbsp;

✅ надо так 👇
```css
input:not([type="submit"]) {}
```
&nbsp;
#### 10. Ставь один пробел перед и после оператора диапазона в медиа-запросах.

> stylelint: [`media-feature-range-operator-space-after`](https://stylelint.io/user-guide/rules/media-feature-range-operator-space-after#media-feature-range-operator-space-after),
>[`media-feature-range-operator-space-before`](https://stylelint.io/user-guide/rules/media-feature-range-operator-space-before#media-feature-range-operator-space-before)

&nbsp;

❌ не надо так 👇
```css
@media (width>=600px) {}
@media (width>= 600px) {}
```

&nbsp;

✅ надо так 👇
```css
@media (width >= 600px) {}
@media (width >= 600px) {}
```
&nbsp;
#### 11. В блоках свойств, объявленных в одну строку, ставь пробел после точки с запятой.

> stylelint: [`declaration-block-semicolon-space-after`](https://stylelint.io/user-guide/rules/declaration-block-semicolon-space-after#declaration-block-semicolon-space-after)

&nbsp;

❌ не надо так 👇
```css
a { color: pink;top: 0; }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; top: 0; }

a {
  color: pink;
  top: 0;
}
```
&nbsp;
#### 12. При использовании !important ставь один пробел перед восклицательным знаком, но не ставь пробел после восклицательного знака.

> stylelint: [`declaration-bang-space-after`](https://stylelint.io/user-guide/rules/declaration-bang-space-after#declaration-bang-space-after),
>[`declaration-bang-space-before`](https://stylelint.io/user-guide/rules/declaration-bang-space-before#declaration-bang-space-before)

&nbsp;

❌ не надо так 👇
```css
a { color: pink!important; }
a { color: pink  ! important; }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink !important; }
```
&nbsp;
#### 13. Не ставь пробел перед запятыми в функциях.

> stylelint: [`function-comma-space-before`](https://stylelint.io/user-guide/rules/function-comma-space-before#function-comma-space-before)

&nbsp;

❌ не надо так 👇
```css
a { transform: translate(1 ,1) }
a { transform: translate(1 , 1) }
```

&nbsp;

✅ надо так 👇
```css
a { transform: translate(1,1) }
a { transform: translate(1, 1) }
```
&nbsp;
#### 14. Не ставь пробел перед запятой в списке медиа-запросов.

> stylelint: [`media-query-list-comma-space-before`](https://stylelint.io/user-guide/rules/media-query-list-comma-space-before#media-query-list-comma-space-before)

&nbsp;

❌ не надо так 👇
```css
@media screen and (color) ,projection and (color) {}
@media screen and (color)
, projection and (color) {}
```

&nbsp;

✅ надо так 👇
```css
@media screen and (color),projection and (color) {}
@media screen and (color),
projection and (color) {}
```
&nbsp;
#### 15. Не ставь пробел перед запятой в списке селекторов.

> stylelint: [`selector-list-comma-space-before`](https://stylelint.io/user-guide/rules/selector-list-comma-space-before#selector-list-comma-space-before)

&nbsp;

❌ не надо так 👇
```css
a ,b { color: pink; }
a , b { color: pink; }
```

&nbsp;

✅ надо так 👇
```css
a,b { color: pink; }
a, b { color: pink; }
```
&nbsp;
#### 16. Не ставь пробел перед запятой при перечислении значений свойства.

> stylelint: [`value-list-comma-space-before`](https://stylelint.io/user-guide/rules/value-list-comma-space-before#value-list-comma-space-before)

&nbsp;

❌ не надо так 👇
```css
a { background-size: 0 ,0; }
a { background-size: 0 ,
      0; }
```

&nbsp;

✅ надо так 👇
```css
a { background-size: 0,0; }
a { background-size: 0,
      0; }
```
&nbsp;
#### 17. Ставь пробел после комбинатора и перед ним.

> stylelint: [`selector-combinator-space-after`](https://stylelint.io/user-guide/rules/selector-combinator-space-after#selector-combinator-space-after),
>[`selector-combinator-space-before`](https://stylelint.io/user-guide/rules/selector-combinator-space-before#selector-combinator-space-before)

&nbsp;

Комбинаторы используются для объединения нескольких различных селекторов в новые и более конкретные. Существует несколько типов комбинаторов, в том числе: child ( >), смежный sibling ( +), общий sibling ( ~) и потомок (который представлен пробелом между двумя селекторами).

&nbsp;

❌ не надо так 👇
```css
a +b { color: pink; }
a>b { color: pink; }
```

&nbsp;

✅ надо так 👇
```css
a + b { color: pink; }
a > b { color: pink; }
```
&nbsp;
#### 18. Не ставь пробел перед двоеточием в свойствах.

> stylelint: [`declaration-colon-space-before`](https://stylelint.io/user-guide/rules/declaration-colon-space-before#declaration-colon-space-before)

&nbsp;

❌ не надо так 👇
```css
a { color : pink }
a { color :pink }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink }
a { color:pink }
```
&nbsp;
#### 19. Не ставь пробел перед двоеточием в медиа-запросах.

> stylelint: [`media-feature-colon-space-before`](https://stylelint.io/user-guide/rules/media-feature-colon-space-before#media-feature-colon-space-before)

&nbsp;

❌ не надо так 👇
```css
@media (max-width :600px) {}
@media (max-width : 600px) {}
```

&nbsp;

✅ надо так 👇
```css
@media (max-width:600px) {}
@media (max-width: 600px) {}
```
&nbsp;
#### 20. Не ставь пробел после оператора и перед ним в селекторах атрибутов.

> stylelint: [`selector-attribute-operator-space-after`](https://stylelint.io/user-guide/rules/selector-attribute-operator-space-after#selector-attribute-operator-space-after),
>[`selector-attribute-operator-space-before`](https://stylelint.io/user-guide/rules/selector-attribute-operator-space-before#selector-attribute-operator-space-before)

&nbsp;

❌ не надо так 👇
```css
[target= _blank] {}
[target = _blank] {}
[target= '_blank'] {}
[target= "_blank"] {}
[target = '_blank'] {}
[target = "_blank"] {}
```

&nbsp;

✅ надо так 👇
```css
[target] {}
[target=_blank] {}
[target='_blank'] {}
[target="_blank"] {}
[target=_blank] {}
[target='_blank'] {}
[target="_blank"] {}
```
&nbsp;
#### 21. В однострочных блоках свойств ставь один пробел после открывающей фигурной скобки и перед закрывающей фигурной скобкой.

> stylelint: [`block-opening-brace-space-after`](https://stylelint.io/user-guide/rules/block-opening-brace-space-after#block-opening-brace-space-after),
>[`block-closing-brace-space-before`](https://stylelint.io/user-guide/rules/block-closing-brace-space-before#block-closing-brace-space-before)

&nbsp;

❌ не надо так 👇
```css
a { color: pink;}
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
a {
color: pink;}
```
&nbsp;
#### 22. Ставь один пробел перед открывающей фигурной скобкой после селектора.

> stylelint: [`block-opening-brace-space-before`](https://stylelint.io/user-guide/rules/block-opening-brace-space-before#block-opening-brace-space-before)

&nbsp;

❌ не надо так 👇
```css
a{ color: pink; }
a
{ color: pink; }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
a {
color: pink; }
```
&nbsp;
#### 23. В однострочных списках значений свойств ставь один пробел после запятой.

> stylelint: [`value-list-comma-space-after`](https://stylelint.io/user-guide/rules/value-list-comma-space-after#value-list-comma-space-after)

&nbsp;

❌ не надо так 👇
```css
a { background-size: 0,0; }
```

&nbsp;

✅ надо так 👇
```css
a { background-size: 0, 0; }

a { background-size: 0
    , 0; }

a { background-size: 0
      ,0; }
```
&nbsp;
#### 24. В однострочных медиа-запросах должен быть пробел после запятой.

> stylelint: [`media-query-list-comma-space-after`](https://stylelint.io/user-guide/rules/media-query-list-comma-space-after#media-query-list-comma-space-after)

&nbsp;

❌ не надо так 👇
```css
@media screen and (color),projection and (color) {}
```

&nbsp;

✅ надо так 👇
```css
@media screen and (color), projection and (color) {}

@media screen and (color)
, projection and (color) {}

@media screen and (color)
,projection and (color) {}
```
&nbsp;
#### 25. Ставь один пробел в однострочных функциях после запятой.

> stylelint: [`function-comma-space-after`](https://stylelint.io/user-guide/rules/function-comma-space-after#function-comma-space-after)

&nbsp;

❌ не надо так 👇
```css
a { transform: translate(1,1) }

a { transform: translate(1 ,1) }
```

&nbsp;

✅ надо так 👇
```css
a { transform: translate(1, 1) }

a { transform: translate(1 , 1) }

a {
  transform: translate(1
    ,1)
}
```
&nbsp;
#### 25. Если у свойства задано несколько значений и свойства записаны в строку, всегда ставь пробел после двоеточия.

> stylelint: [`declaration-colon-space-after`](https://stylelint.io/user-guide/rules/declaration-colon-space-after#declaration-colon-space-after)

&nbsp;

❌ не надо так 👇
```css
a {
  box-shadow:0 0 0 1px #5b9dd9, 0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```

&nbsp;

✅ надо так 👇
```css
a {
  box-shadow: 0 0 0 1px #5b9dd9, 0 0 2px 1px rgba(30, 140, 190, 0.8);
}

a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}

a {
  box-shadow:0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```
&nbsp;
#### 26. Всегда должен быть один пробел после имени правила в однострочных блоках.

> stylelint: [`at-rule-name-space-after`](https://stylelint.io/user-guide/rules/at-rule-name-space-after#at-rule-name-space-after)

&nbsp;

❌ не надо так 👇
```css
@charset"UTF-8";
@media(min-width: 700px) {}
@media  (min-width: 700px) {}
```

&nbsp;

✅ надо так 👇
```css
@charset "UTF-8";
@import url("x.css");
@media (min-width: 700px) {}

@media
(min-width: 700px) {}

@media(min-width: 700px) and
  (orientation: portrait) {}

@media
  (min-width: 700px) and
  (orientation: portrait) {}
```
&nbsp;
#### 27. В медиа-запросах ставь пробел после двоеточия в свойстве-условии.

> stylelint: [`media-feature-colon-space-after`](https://stylelint.io/user-guide/rules/media-feature-colon-space-after#media-feature-colon-space-after)

&nbsp;

❌ не надо так 👇
```css
@media (max-width:600px) {}
@media (max-width :600px) {
```

&nbsp;

✅ надо так 👇
```css
@media (max-width: 600px) {}
@media (max-width : 600px) {}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Дублирование.

&nbsp;
#### 1. Не дублируй селекторы.

> stylelint: [`no-duplicate-selectors`](https://stylelint.io/user-guide/rules/no-duplicate-selectors#no-duplicate-selectors)

&nbsp;

Один и тот же селектор может повторяться при следующих обстоятельствах:

* используется в разных списках селекторов:
  * ```a{}``` ;
  * ```a, b {}```  .

* дубликаты происходят из разных таблиц стилей;
* дубликаты находятся в правилах с различными родительскими узлами, например, внутри и снаружи медиа запроса.

&nbsp;

❌ не надо так 👇
```css
.foo, .bar, .foo {}

.foo {}
.bar {}
.foo {}

.foo .bar {}
.bar {}
.foo .bar {}

@media (min-width: 10px) {
  .foo {}
  .foo {}
}

.foo, .bar {}
.bar, .foo {}

a .foo, b + .bar {}
b+.bar, a .foo {}

a b {}
a {
  & b {}
}
```

&nbsp;

✅ надо так 👇
```css
.foo {}
@media (min-width: 10px) {
  .foo {}
}

.foo {
  .foo {}
}

.foo {}
.bar {}
.foo .bar {}
.bar .foo {}

a b {}
a {
  & b,
  & c {}
}
```
&nbsp;
#### 2. Не дублируй свойства в блоках;

> stylelint: [`declaration-block-no-duplicate-properties`](https://stylelint.io/user-guide/rules/declaration-block-no-duplicate-properties#declaration-block-no-duplicate-properties)

&nbsp;

- никогда не повторяй свойства.

&nbsp;

❌ не надо так 👇
```css
a { color: pink; color: orange; }
a { color: pink; background: orange; color: orange }
```

&nbsp;

✅ надо так 👇
```css
a { color: pink; }
a { color: pink; background: orange; }
```

&nbsp;

**Исключения:**

- можно повторять свойства с разными значениями, которые идут последовательно;

  Включение повторяющихся свойств (как запасных вариантов) полезно для поддержки свойств CSS в старых браузерах. Например, использование px единиц, когда rem единицы не поддерживаются.

&nbsp;

&nbsp;

❌ не надо так 👇
```css
/* одинаковые значения */
p {
  font-size: 16px;
  font-size: 16px;
  font-weight: 400;

/* непоследовательные дубликаты */
p {
  font-size: 16px;
  font-weight: 400;
  font-size: 1rem;
}
```

&nbsp;

✅ надо так 👇
```css
p {
  font-size: 16px;
  font-size: 1rem;
  font-weight: 400;
}
```
&nbsp;
#### 3. В таблице стилей не дублируй правила через @import.

> stylelint: [`no-duplicate-at-import-rules`](https://stylelint.io/user-guide/rules/no-duplicate-at-import-rules#no-duplicate-at-import-rules)

&nbsp;

❌ не надо так 👇
```css
@import 'a.css';
@import 'a.css';

@import url("a.css");
@import url("a.css");
	
@import "a.css";
@import 'a.css';

@import "a.css";
@import 'b.css';
@import url(a.css);
```

&nbsp;

✅ надо так 👇
```css
@import "a.css";
@import "b.css";

@import url('a.css') projection;
@import url('a.css') tv;
```
&nbsp;
#### 4. Не дублируй имена шрифтов.

> stylelint: [`font-family-no-duplicate-names`](https://stylelint.io/user-guide/rules/font-family-no-duplicate-names#font-family-no-duplicate-names)

&nbsp;

❌ не надо так 👇
```css
a { font-family: 'Times', Times, serif; }
a { font: 1em "Arial", 'Arial', sans-serif; }
a { font: normal 14px/32px -apple-system, BlinkMacSystemFont, sans-serif, sans-serif; }
```

&nbsp;

✅ надо так 👇
```css
a { font-family: Times, serif; }
a { font: 1em "Arial", "sans-serif", sans-serif; }
a { font: normal 14px/32px -apple-system, BlinkMacSystemFont, sans-serif; }
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

 ## Использование только известных названий/имен/свойств и тд.
 
&nbsp;
#### 1. Используй известные правила.

> stylelint: [`at-rule-no-unknown`](https://stylelint.io/user-guide/rules/at-rule-no-unknown#at-rule-no-unknown)

&nbsp;

❌ не надо так 👇
```css
@unknown {}
```

&nbsp;

✅ надо так 👇
```css
@charset "UTF-8";

@CHARSET "UTF-8";

@media (max-width: 960px) {}

@font-feature-values Font One {
  @styleset {}
}
```
&nbsp;
#### 2. Используй известные имена для медиа-запросов.

> stylelint: [`media-feature-name-no-unknown`](https://stylelint.io/user-guide/rules/media-feature-name-no-unknown#media-feature-name-no-unknown)

&nbsp;

❌ не надо так 👇
```css
@media screen and (unknown) {}
@media screen and (unknown: 10px) {}
@media screen and (unknown > 10px) {}
```

&nbsp;

✅ надо так 👇
```css
@media all and (monochrome) {}
@media (min-width: 700px) {}
@media (MIN-WIDTH: 700px) {}
@media (min-width: 700px) and (orientation: landscape) {}
@media (-webkit-min-device-pixel-ratio: 2) {}
```
&nbsp;
#### 3. Используй только известные свойства, селекторы псевдоклассов и псевдоэлементов, типы селекторов.

> stylelint: [`property-no-unknown`](https://stylelint.io/user-guide/rules/property-no-unknown#property-no-unknown),
>[`selector-pseudo-class-no-unknown`](https://stylelint.io/user-guide/rules/selector-pseudo-class-no-unknown#selector-pseudo-class-no-unknown),
>[`selector-pseudo-element-no-unknown`](https://stylelint.io/user-guide/rules/selector-pseudo-element-no-unknown#selector-pseudo-element-no-unknown),
>[`selector-type-no-unknown`](https://stylelint.io/user-guide/rules/selector-type-no-unknown#selector-type-no-unknown)

&nbsp;

Свойства, селекторы псевдоклассов и псевдоэлементов, определенные в Спецификациях CSS, и свойства, специфичные для браузера, считаются известными.

&nbsp;

❌ не надо так 👇
```css
a {
  colr: blue;
}
a:hoverr {}
a::element {}
tag {}
```

&nbsp;

✅ надо так 👇
```css
a {
  color: green;
}
a {
  -webkit-align-self: center;
}
a {
  align-self: center;
}
a:hover {}
a:before {}
input {}
ul li {}
```
&nbsp;
#### 4. Используй только известные единицы измерения, определенные в Спецификациях CSS.

> stylelint: [`unit-no-unknown`](https://stylelint.io/user-guide/rules/unit-no-unknown#unit-no-unknown)

&nbsp;

❌ не надо так 👇
```css
a {
  width: 10pixels;
}
a {
  width: calc(10px + 10pixels);
}
```

&nbsp;

✅ надо так 👇
```css
a {
  width: 10px;
}
a {
  width: 10Px;
}
a {
  width: 10pX;
}
a {
  width: calc(10px + 10px);
}
```
&nbsp;
#### 5. При использовании цветов в шестнадцатеричной форме не используй недопустимые значение.

> stylelint: [`color-no-invalid-hex`](https://stylelint.io/user-guide/rules/color-no-invalid-hex#color-no-invalid-hex)

&nbsp;

Длинные шестнадцатеричные цвета могут состоять из 6 или 8 (с альфа-каналом) шестнадцатеричных символов. И их сокращенные варианты - 3 и 4 символа соответственно.

&nbsp;

❌ не надо так 👇
```css
a { color: #00; }
a { color: #fff1a; }
a { color: #12345aa; }
```

&nbsp;

✅ надо так 👇
```css
a { color: #000; }
a { color: #000f; }
a { color: #fff1a0; }
a { color: #123450aa; }
```
&nbsp;
#### 6. При использовании linear-gradient() правильно пиши первый аргумент - позиция, от которой будет начинаться градиент.

> stylelint: [`function-linear-gradient-no-nonstandard-direction`](https://stylelint.io/user-guide/rules/function-linear-gradient-no-nonstandard-direction#function-linear-gradient-no-nonstandard-direction)

&nbsp;

Для позиции используются следующие значения:

* угол;

* **to**, а затем добавляются ключевые слова top, bottom и left, right.

&nbsp;

❌ не надо так 👇
```css
.foo { background: linear-gradient(top, #fff, #000); }

.foo { background: linear-gradient(bottom, #fff, #000); }

.foo { background: linear-gradient(45, #fff, #000); }

.foo { background: linear-gradient(to top top, #fff, #000); }
```

&nbsp;

✅ надо так 👇
```css
.foo { background: linear-gradient(to top, #fff, #000); }

.foo { background: linear-gradient(to bottom right, #fff, #000); }

.foo { background: linear-gradient(45deg, #fff, #000); }

.foo { background: linear-gradient(1.57rad, #fff, #000); }

/* Направление по умолчанию "to bottom" */
.foo { background: linear-gradient(#fff, #000); }
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Комментарии.

&nbsp;
#### 1. Не оставляй пустые комментарии.

> stylelint: [`comment-no-empty`](https://stylelint.io/user-guide/rules/comment-no-empty#comment-no-empty)

&nbsp;

❌ не надо так 👇
```css
/**/
/* */
/*

 */
```

&nbsp;

✅ надо так 👇
```css
/* comment */
/*
 * Multi-line Comment
**/
```

&nbsp;
#### 2. Не используй двойной слеш //...  для комментирования.

> stylelint: [`no-invalid-double-slash-comments`](https://stylelint.io/user-guide/rules/no-invalid-double-slash-comments#no-invalid-double-slash-comments)

&nbsp;

CSS не поддерживает комментарии двойным слешем (исключение: некоторые препроцессоры)

&nbsp;

❌ не надо так 👇
```css
a {
  //color: pink;
}
//a { color: pink; }

// Comment {}
a {
  color: pink;
}
```

&nbsp;

✅ надо так 👇
```css
a {
  /* color: pink; */
}
/* a { color: pink;  } */
```
&nbsp;
#### 3. Ставь пробелы внутри маркеров комментария.

> stylelint: [`comment-whitespace-inside`](https://stylelint.io/user-guide/rules/comment-whitespace-inside#comment-whitespace-inside)

&nbsp;

❌ не надо так 👇
```css
/*comment*/

/*comment */

/** comment**/
```

&nbsp;

✅ надо так 👇
```css
/* comment */

/** comment **/

/**
 * comment
 */

/*     comment
*/
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## !important в @keyframes.

&nbsp;
#### Не используй !important в объявлениях в ключевых кадрах.

> stylelint: [`keyframe-declaration-no-important`](https://stylelint.io/user-guide/rules/keyframe-declaration-no-important)

&nbsp;

Использование !important в объявлениях ключевых кадров полностью игнорируется в некоторых браузерах.

&nbsp;

❌ не надо так 👇
```css
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px !important;
  }
}
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px!important;
  }
}
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px ! important;
  }
}
```

&nbsp;

✅ надо так 👇
```css
a { color: pink !important; }
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px;
  }
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

&nbsp;

[![](https://webheroschool.ru/logo.png)](http://webheroschool.ru/)