# WebHero CSS Style Guide
---

В данном руководстве описаны подходы по оформлению CSS.


## Содержание
---

1. [Отступы, 2 или 4 пробела](#отступы-2-или-4-пробела)
2. [Точка с запятой](#точка-с-запятой)
3. [В строку или в столбик](#в-строку-или-в-столбик)
4. [: или :: для псевдоэлементов](#-или--для-псевдоэлементов)
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




### Отступы, 2 или 4 пробела

Всегда делай отступ в два пробела. (если ты пользуешься табом, то его можно также настроить на отступ в два пробела)

❌
```
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
✅
 ```
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

### Точка с запятой

* Всегда ставь точку с запятой у последнего свойства в блоке

❌
```
a { color: pink }
a { background: orange; color: pink }
a { @include foo }
```
✅
```
a { color: pink; }
a { background: orange; color: pink; }
a { @include foo; }
```

* Не ставь лишние точки с запятой

❌
```
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
✅
```
@import "x.css";

a {
  color: pink;
}
```

### В строку или в столбик

* Если свойств несколько, лучше писать их в столбик
Такая запись более удобна для восприятия.

❌
```
a { color: pink; top: 3px; }

a,
b { color: pink; top: 3px; }
```
✅
```
b { color: pink; }

a {
  color: pink;
  top: 3px;
}
```

* В многострочных блоках пиши каждое свойство с новой строки(в столбик)

❌
```
a {
  color: pink; top: 0;
}
```
✅
```
a {
  color: pink;
  top: 0;
}
```

* Перечисляй селекторы в столбик (после запятой начинай с новой строки)

❌
```
a, b { color: pink; }

a
, b { color: pink; }
```
✅
```
a,
b { color: pink; }

a
,
b { color: pink; }
```

### : или :: для псевдоэлементов

Используй двойное двоеточие для псевдоэлементов

❌
```
a:before { color: pink; }
a:after { color: pink; }
a:first-letter { color: pink; }
a:first-line { color: pink; }
```
✅
```
a::before { color: pink; }
a::after { color: pink; }
a::first-letter { color: pink; }
a::first-line { color: pink; }
input::placeholder { color: pink; }
li::marker { font-variant-numeric: tabular-nums; }
```

### Пустые блоки

Не оставляй блоки со стилями пустыми с комментарием внутри, которые рассматриваются как содержимое

❌
```
a {
  /* foo */
}

@media print {
  a {
    /* foo */
  }
}

a {
}
```

### Ноль, что с ним делать

* Не ставь ведущий ноль у дробных чисел

❌
```
a { line-height: 0.5; }
a { transform: translate(2px, 0.4px); }
```
✅
```
a { line-height: .5; }
a { transform: translate(2px, .4px); }

```

* Не ставь единицы измерения длины, если значение нулевое

    Длина - это измерение , которое представляет собой число, за которым сразу следует идентификатор единицы измерения . Однако для нулевой длины идентификатор единицы является необязательным. Единицы длины: em, ex, ch, vw, vh, cm, mm, in, pt, pc, px, rem, vmin, и vmax.
    
❌
```
a { top: 0px }
a { top: 0.000em }
```
✅
```
a { top: 0 } /* нет единицы */
a { transition-delay: 0s; } /* измерение*/
a { top: 2in; }
a { top: 1.001vh }
```

* Не ставь нули в конце чисел, если они не несут смысла

❌
```
a { top: 1.0px }
a { top: 1.01000px }
```
✅
```
a { top: 1px }
a { top: 1.01px }
```

### Специфичность

* Не пиши селекторы с меньшей специфичностью после селекторов с большей специфичностью

    Когда два селектора имеют одинаковую специфичность, приоритет имеет тот , который появляется последним . Однако ситуация отличается, когда один из селекторов имеет более высокую специфичность. В этом случае исходный порядок не имеет значения: селектор с более высокой специфичностью победит, даже если он появится первым.
    
❌
```
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
✅
```
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

* Не пиши сокращенные свойства  после связных свойств

    Сокращенные свойства могут переопределить связные свойства
    
 ❌
``` 
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
✅
```
a { padding: 10px; padding-left: 20px; }
 
a { transition-property: opacity; } a { transition: opacity 1s linear; }
 
a { transition-property: opacity; -webkit-transition: opacity 1s linear; }
```

### Шрифты

Ставь всегда тип шрифта(serif, sans-serif, cursive, fantasy или monospace)
Тип шрифта:
- может стоять в любом месте в списке шрифтов
- может быть опущен, если используется ключевое слово, связанное с наследованием свойств или системным шрифтом

 ❌
```
a { font-family: Helvetica, Arial, Verdana, Tahoma; }
a { font: 1em/1.3 Times; }
```
✅
```
a { font-family: Helvetica, Arial, Verdana, Tahoma, sans-serif; }
a { font: 1em/1.3 Times, serif, Apple Color Emoji; }
a { font: inherit; }
a { font: caption; }
```

### Строчные или заглавные буквы

* Называй правила строчными буквами

 ❌
```
@Charset 'UTF-8';
@cHarSeT 'UTF-8';
@CHARSET 'UTF-8';
@Media (min-width: 50em) {}
@mEdIa (min-width: 50em) {}
@MEDIA (min-width: 50em) {}
```
✅
```
@charset 'UTF-8';
@media (min-width: 50em) {}
```

* Называй функции строчными буквами

 ❌
```
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
✅
```
a {
  width: calc(5% - 10em);
}
a {
  background: -webkit-radial-gradient(red, green, blue);
}
```

* Для цветов в шестнадцетиричном формате используй строчные буквы

❌
```
a { color: #FFF; }
```
✅
```
a { color: #000; }
a { color: #fff; }
```

* Для названий медиа запрсов используй строчные буквы

❌
```
@media (MIN-WIDTH: 700px) {}
@media not all and (MONOCHROME) {}
@media (min-width: 700px) and (ORIENTATION: landscape) {}
@media (WIDTH > 10em) {}
```
✅
```
@media (min-width: 700px) {}
@media not all and (monochrome) {}
@media (min-width: 700px) and (orientation: landscape) {}
@media (width > 10em) {}
```

* Пиши свойства строчными буквами

❌
```
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
✅
```
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

* Используй строчные буквы для селекоторов псевдоклассов

❌
```
a:Hover {}
a:hOvEr {}
a:HOVER {}
:ROOT {}
:-MS-INPUT-PLACEHOLDER {}
```
✅
```
a:hover {}
:root {}
:-ms-input-placeholder {}
```

* Используй строчные буквы для селекоторов псевдоэлементов

❌
```
a:Before {}
a:bEfOrE {}
a:BEFORE {}
a::Before {}
a::bEfOrE {}
a::BEFORE {}
input::-MOZ-PLACEHOLDER {}
```
✅
```
a:before {}
a::before {}
input::-moz-placeholder {}
```

* Используй строчные буквы для типов селекторов

❌
```
A {}
LI {}
```
✅
```
a {}
li {}
```

* Используй строчные буквы для единиц измерени

❌
```
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
✅
```
a {
  width: 10px;
}
a {
  width: calc(10px * 2);
}
```

### Короткое или длинное название шестнадцатеричных цветов

Используй короткие обозначения шестнадцатеричных цветов

❌
```
a { color: #ffffff; }
a { color: #ffffffaa; }
```
✅
```
a { color: #fff; }
a { color: #fffa; }
a { color: #a4a4a4; }
```

### Пустая строка (Enter)

* Пустая строка перед at-rules (правилами)

-- всегда оставляй пустую строку
    
❌
```
a {} @media {}
a {}
@media {}
```
✅
```
a {}
@media {}
```

**Исключения**
-- можно группировать свой правила по имени в блоки

✅
```
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

-- если правило вложено в блок и стоит первым, то пустую строку не оставляем

❌
```
a {

  @extend foo;
  color: pink;
}

b {
  color: pink;
  @extend foo;
}
```
✅
```
a {
  @extend foo;
  color: pink;
}

b {
  color: pink;

  @extend foo;
}
```

-- если правило следует за комментарием, то новую строку можно не ставить

✅
```
/* comment */
@media {}

@media {} /* comment */
```

* Пустая строка перед комментарием

-- всегда оставлять пустую строку

❌
```
a {}
/* comment */
```
✅
```
a {}

/* comment */

a {} /* comment */
```

**Исключения**

-- если комментарий вложен в блок и стоит первым в блоке, пустую строку оставлять не надо

❌
```
a {

  /* comment */
  color: pink;
}
```
✅
```
a {
  /* comment */
  color: pink;
}
```

-- игнорируй комментарии, которые являются командами к stylelint

❌
```
a {
  background: pink;
  /* not a stylelint command */
  color: #eee;
}
```
✅
```
a {
  background: pink;
  /* stylelint-disable color-no-hex */
  color: pink;
}
```

* Пустая строка перед пользовательскими свойствами (CSS переменные)

-- всегда оставляй пустую строку перед пользовательским свойствами

 ❌
```
a {
  top: 10px;
  --foo: pink;
  --bar: red;
}
```
✅
```
a {
  top: 10px;

  --foo: pink;

  --bar: red;
}
```

**Исключения**

-- если пользовательские свойства следуют друг за другом, то не нужно оставлять пустую строку

 ❌
```
a {

  --foo: pink;

  --bar: red;
}

a {

  --foo: pink; /* comment */

  --bar: red;
}
```
✅
```
a {

  --foo: pink;
  --bar: red;
}

a {

  --foo: pink; /* comment */
  --bar: red;
}
```

-- перед вложенными пользовательскими свойствами, которые стоят первыми в блоке свойств не нужно оставлять пустую строку

 ❌
```
a {

  --foo: pink;

  --bar: red;
}
```
✅
```
a {
  --foo: pink;

  --bar: red;
}
```

-- не оставляй пустую строку, если свойство идет после комментария

✅
```
a {
  /* comment */
  --foo: pink;
}
```

-- данное правило игнорируется для пользовательских свойств, которые находятся внутри однострочных блоков

✅
```
a { --foo: pink; --bar: red; }
```

* Пустая строка перед простыми свойствами

-- оставляй пустую строку

 ❌
```
a {
  --foo: pink;
  top: 5px;
}

a {
  bottom: 15px;
  top: 5px;
}
```
✅
```
a {
  --foo: pink;

  top: 5px;
}

a {

  bottom: 15px;

  top: 5px;
}
```

**Исключения**

-- Если простое свойство следует за другим простым свойством, пустая строка не нужна. Комментарии не влияют на правило

 ❌
```
a {

  bottom: 15px;

  top: 5px;
}

a {

  bottom: 15px; /* comment */

  top: 5px;
}
```
✅
```
a {

  bottom: 15px;
  top: 5px;
}

a {

  bottom: 15px; /* comment */
  top: 5px;
}
```

-- перед вложенными блоками, которые идут первыми в блоке, пустая строка не требуется

 ❌
```
a {

  bottom: 15px;

  top: 5px;
}
```
✅
```
a {
  bottom: 15px;

  top: 5px;
}
```

-- если свойство идет за комментарием, пустая строка не требуется

✅
```
a {
  /* comment */
  bottom: 15px;
}
```

-- правило игнорируется для свойств, написанных в строку

✅
```
a { bottom: 15px; top: 5px; }
```

* Пустая строка перед блоками свойств

-- оставляй пустую строку перед многострочными блоками

 ❌
```
a {
  color: red;
}
b {
  color: blue;
}
```
✅
```
a {
  color: red;
}

b {
  color: blue;
}
```

**Исключения**

-- если блок вложен и стоит первым, то перед ним не нужно оставлять пустую строку

 ❌
```
@media {

  a {}

  b {}
}
```
✅
```
@media {
  a {}

  b {}
}
```

-- если блок стоит после комментария, то пустая строка не нужна

✅
```
/* comment */
a {}
```

* Не оставляй пустую строку перед закрывающей фигурной скобкой

 ❌
```
a {
  color: pink;

}
```
✅
```
a {
  color: pink;
}

a { color: pink; }
```

* Не ставь лишние  смежные пустые строки в функциях, селекторах, списках значений

 ❌
```
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
✅
```
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

* Ограничь число смежных пустых строк в таблице стилей

 ❌
```
a {}



b {}
//Также относится к комментариям
/*
 Call me Ishmael.



 Some years ago -- never mind how log precisely -- ...
 */
```
✅
```
a {}
b {}

a {}

b {}
```

* После открывающей фигурной скобки блока начинай писать свойства с новой строки

 ❌
```
a{ color: pink; }
a{ color: pink;
}
// также относится к комментариям
a{ /* end-of-line comment
  	with a newline */
  	color: pink;
}
```
✅
```
a {
color: pink; }
a
{
color: pink; }
a { /* end-of-line comment */
  	color: pink;
}
```

* После точки с запятой в at-rules (правила) начинай писать с новой строки

❌
```
@import url("x.css"); @import url("y.css");
@import url("x.css"); a {}
```
✅
```
@import url("x.css");
@import url("y.css");

@import url("x.css"); /* end-of-line comment */
a {}

@import url("x.css");

a {}
```

* После закрывающей фигурной скобки в блоке начинай следующую запись с новой строки

❌
```
a { color: pink; }b { color: red; }
a { color: pink;
} b { color: red; }
```
✅
```
a { color: pink; }
b { color: red; }
```

* В многострочных функциях в скобках ставь символ новой строки после открывающей и перед закрывающей скобкой

❌
```
a { transform: translate(1,
  1) }
```
✅
```
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

* В многострочных функциях после запятой начинай писать с новой строки

❌
```
a { transform: translate(1
  ,1) }
```
✅
```
a { transform: translate(1,1) }
a { transform: translate(1 ,1) }

a {
  transform: translate(1,
    1)
}
```

* В многострочных списках медиа-запросов всегда должен быть символ новой строки после запятых

❌
```
@media screen and (color)
, projection and (color) {}
```
✅
```
@media screen and (color), projection and (color) {}

@media screen and (color),
projection and (color) {}

@media screen and (color)
,
projection and (color) {}
```

* В многострочных списках значений свойства начинай писать с новой строки после запятой

❌
```
a { background-size: 0
    , 0; }
```
✅
```
a { background-size: 0, 0; }
a { background-size: 0,0; }
a { background-size: 0,
      0; }
```

* В многострочных блоках свойств закрывающая фигурная скобка должна быть на новой строке

❌
```
a {
color: pink;}
```
✅
```
a { color: pink; }
a { color: pink;
}
```

* Если свойство многострочное, после двоеточия начинай писать с новой строки

❌
```
a {
  box-shadow: 0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```
✅
```
a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}

a {
  color: pink;
}
```

* Не переноси непрерывные строки без использования экранирующего символа ‘\ ’

❌
```
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
✅
```
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

### Пробелы

* Не ставь пробелы в конце строки

❌
```
a { color: pink; }·
a { color: pink; }

/* Также это относится и к многострочным комментариям */

/* something····
 * something else */
```
✅
```
a { color: pink; }

/* something
 * something else */
```

* Ставь один пробел между комбинаторами

❌
```
.foo  .bar {}
.foo
.bar {}
```
✅
```
.foo .bar {}
```

* В calc функциях ставь пробел перед и после оператора
Перед оператором должен быть один пробел
После оператора должен быть один пробел

❌
```
a { top: calc(1px+2px); }
a { top: calc(1px+ 2px); }
```
✅
```
a { top: calc(1px + 2px); }
a { top: calc(calc(1em * 2) / 3); }
a {
  top: calc(var(--foo) +
    var(--bar));
}
a {
  top: calc(var(--foo)
    + var(--bar));
}
```

* Не ставь пробел перед точкой с запятой в блоках со свойствами

❌
```
a { color: pink ; }
a { color: pink ; top: 0 ; }
```
✅
```
a { color: pink; }
a { color: pink; top: 0; }
```

* Не ставь пробелы после квадратной скобки и перед ней в селекторах атрибутов

❌
```
[ target] {}
[target ] {}
[ target ] {}
[ target=_blank] {}
[target=_blank ] {}
[ target=_blank ] {}
```
✅
```
[target] {}
[target=_blank] {}
```

* Не ставь пробелы после и перед круглой скобкой в однострочных функциях

❌
```
a { transform: translate( 1, 1 ) }
a { transform: translate(1, 1 ) }
```
✅
```
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

* Не ставь пробелы внутри круглых скобок в медиа запросах

❌
```
@media ( max-width: 300px ) {}
@media ( max-width: 300px) {}
```
✅
```
@media (max-width: 300px) {}
```

* Не ставь пробелы внутри круглых скобок в селекторах псевдоклассов

❌
```
a { transform: translate(1, 1)scale(3); }
```
✅
```
input:not([type="submit"]) {}
```

* Всегда ставь пробел после функции

❌
```
input:not( [type="submit"] ) {}
input:not( [type="submit"]) {}
```
✅
```
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

* Ставь один пробел перед и после оператора диапазона в медиа запросах

❌
```
@media (width>=600px) {}
@media (width>= 600px) {}
```
✅
```
@media (width >= 600px) {}
@media (width >= 600px) {}
```

* В блоках свойств, объявленных в одну строку, ставь пробел после точки с запятой

❌
```
a { color: pink;top: 0; }
```
✅
```
a { color: pink; top: 0; }

a {
  color: pink;
  top: 0;
}
```

* При использовании !important ставь один пробел перед восклицательным знаком
Но не ставь пробел после восклицательного знака

❌
```
a { color: pink!important; }
a { color: pink  ! important; }
```
✅
```
a { color: pink !important; }
```

* Не ставь пробел перед запятыми в функциях

❌
```
a { transform: translate(1 ,1) }
a { transform: translate(1 , 1) }
```
✅
```
a { transform: translate(1,1) }
a { transform: translate(1, 1) }
```

* Не ставь пробел перед запятой в списке медиа запросов

❌
```
@media screen and (color) ,projection and (color) {}
@media screen and (color)
, projection and (color) {}
```
✅
```
@media screen and (color),projection and (color) {}
@media screen and (color),
projection and (color) {}
```

* Не ставь пробел перед запятой в списке селекторов

❌
```
a ,b { color: pink; }
a , b { color: pink; }
```
✅
```
a,b { color: pink; }
a, b { color: pink; }
```

* Не ставь пробел перед запятой при перечислении значений свойства

❌
```
a { background-size: 0 ,0; }
a { background-size: 0 ,
      0; }
```
✅
```
a { background-size: 0,0; }
a { background-size: 0,
      0; }
```

* Ставь пробел после комбинатора и перед ним
Комбинаторы используются для объединения нескольких различных селекторов в новые и более конкретные. Существует несколько типов комбинаторов, в том числе: child ( >), смежный sibling ( +), общий sibling ( ~) и потомок (который представлен пробелом между двумя селекторами).

❌
```
a +b { color: pink; }
a>b { color: pink; }
```
✅
```
a + b { color: pink; }
a > b { color: pink; }
```

* Не ставь пробел перед двоеточием в свойствах

❌
```
a { color : pink }
a { color :pink }
```
✅
```
a { color: pink }
a { color:pink }
```

* Не ставь пробел перед двоеточием в медиа запросах

❌
```
@media (max-width :600px) {}
@media (max-width : 600px) {}
```
✅
```
@media (max-width:600px) {}
@media (max-width: 600px) {}
```

* Не ставь пробел после оператора и перед ним в селекторах атрибутов

❌
```
[target= _blank] {}
[target = _blank] {}
[target= '_blank'] {}
[target= "_blank"] {}
[target = '_blank'] {}
[target = "_blank"] {}
```
✅
```
[target] {}
[target=_blank] {}
[target='_blank'] {}
[target="_blank"] {}
[target=_blank] {}
[target='_blank'] {}
[target="_blank"] {}
```

* В однострочных блоках свойств ставь один пробел после открывающей фигурной скобки и перед закрывающей фигурной скобкой

❌
```
a { color: pink;}
```
✅
```
a { color: pink; }
a {
color: pink;}
```

* Ставь один пробел перед открывающей фигурной скобкой после селектора

❌
```
a{ color: pink; }
a
{ color: pink; }
```
✅
```
a { color: pink; }
a {
color: pink; }
```

* В однострочных списках значений свойств ставь один пробел после запятой

❌
```
a { background-size: 0,0; }
```
✅
```
a { background-size: 0, 0; }

a { background-size: 0
    , 0; }

a { background-size: 0
      ,0; }
```

* В однострочных медиа запросах должен быть пробел после запятой

❌
```
@media screen and (color),projection and (color) {}
```
✅
```
@media screen and (color), projection and (color) {}

@media screen and (color)
, projection and (color) {}

@media screen and (color)
,projection and (color) {}
```

* Ставь один пробел в однострочных функциях после запятой

❌
```
a { transform: translate(1,1) }

a { transform: translate(1 ,1) }
```
✅
```
a { transform: translate(1, 1) }

a { transform: translate(1 , 1) }

a {
  transform: translate(1
    ,1)
}
```

* Если у свойства задано несколько значений и свойства записаны в строку, всегда ставь пробел после двоеточия

❌
```
a {
  box-shadow:0 0 0 1px #5b9dd9, 0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```
✅
```
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

* Всегда должен быть один пробел после имени правила в однострочных блоках

❌
```
@charset"UTF-8";
@media(min-width: 700px) {}
@media  (min-width: 700px) {}
```
✅
```
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

* В медиа запросах ставь пробел после двоеточия в свойстве-условии

❌
```
@media (max-width:600px) {}
@media (max-width :600px) {
```
✅
```
@media (max-width: 600px) {}
@media (max-width : 600px) {}
```

### Дублирование

* Не дублируй селекторы
Один и тот же селектор может повторяться при следующих обстоятельствах:
    -- используется в разных списках селекторов:
    * a{}
    * a, b {}

    -- дубликаты происходят из разных таблиц стилей
    -- дубликаты находятся в правилах с различными родительскими узлами, например, внутри и снаружи медиа запроса

❌
```
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
✅
```
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

* Не дублируй свойства в блоках

❌
```
a { 
color: pink;
color: orange;
}
a {
color: pink;
background: orange;
color: orange
}
```
✅
```
a {
color: pink;
}
a {
color: pink;
background: orange;
}

/* Такая ситуация допустима при поддержке старых браузеров (единицы rem поддерживаются не всеми старыми браузерами) */
p {
  font-size: 16px;
  font-size: 1rem;
  font-weight: 400;
}
```

* В таблице стилей не дублируй правила через @import

❌
```
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
✅
```
@import "a.css";
@import "b.css";

@import url('a.css') projection;
@import url('a.css') tv;
```

* Не дублируй имена шрифтов

❌
```
a { font-family: 'Times', Times, serif; }
a { font: 1em "Arial", 'Arial', sans-serif; }
a { font: normal 14px/32px -apple-system, BlinkMacSystemFont, sans-serif, sans-serif; }
```
✅
```
a { font-family: Times, serif; }
a { font: 1em "Arial", "sans-serif", sans-serif; }
a { font: normal 14px/32px -apple-system, BlinkMacSystemFont, sans-serif; }
```

 ### Использование только известных названий/имен/свойств и тд

* Используй известные правила

❌
```
@unknown {}
```
✅
```
@charset "UTF-8";

@CHARSET "UTF-8";

@media (max-width: 960px) {}

@font-feature-values Font One {
  @styleset {}
}
```

* Используй известные имена для медиа запросов

❌
```
@media screen and (unknown) {}
@media screen and (unknown: 10px) {}
@media screen and (unknown > 10px) {}
```
✅
```
@media all and (monochrome) {}
@media (min-width: 700px) {}
@media (MIN-WIDTH: 700px) {}
@media (min-width: 700px) and (orientation: landscape) {}
@media (-webkit-min-device-pixel-ratio: 2) {}
```

* Используй только известные свойства, селекторы псевдоклассов и псевдоэлементов, типы селекторов
Свойства, селекторы псевдоклассов и псевдоэлементов, определенные в Спецификациях CSS, и свойства, специфичные для браузера, считаются известными.

❌
```
a {
  colr: blue;
}
a:hoverr {}
a::element {}
tag {}
```
✅
```
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

* Используй только известные единицы измерения, определенные в Спецификациях CSS

❌
```
a {
  width: 10pixels;
}
a {
  width: calc(10px + 10pixels);
}
```
✅
```
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

* При использовании цветов в шестнадцатеричной форме не используй недопустимые значение
Длинные шестнадцатеричные цвета могут состоять из 6 или 8 (с альфа-каналом) шестнадцатеричных символов. И их сокращенные варианты - 3 и 4 символа соответственно.

❌
```
a { color: #00; }
a { color: #fff1a; }
a { color: #12345aa; }
```
✅
```
a { color: #000; }
a { color: #000f; }
a { color: #fff1a0; }
a { color: #123450aa; }
```

* При использовании linear-gradient() правильно пиши первый аргумент - позиция, от которой будет начинаться градиент
Для позиции используются следующие значения:
-- угол;
-- **to**, а затем добавляются ключевые слова top, bottom и left, right.

❌
```
.foo { background: linear-gradient(top, #fff, #000); }

.foo { background: linear-gradient(bottom, #fff, #000); }

.foo { background: linear-gradient(45, #fff, #000); }

.foo { background: linear-gradient(to top top, #fff, #000); }
```
✅
```
.foo { background: linear-gradient(to top, #fff, #000); }

.foo { background: linear-gradient(to bottom right, #fff, #000); }

.foo { background: linear-gradient(45deg, #fff, #000); }

.foo { background: linear-gradient(1.57rad, #fff, #000); }

/* Направление по умолчанию "to bottom" */
.foo { background: linear-gradient(#fff, #000); }
```

### Комментарии

* Не оставляй пустые комментарии

❌
```
/**/
/* */
/*

 */
```
✅
```
/* comment */
/*
 * Multi-line Comment
**/
```

* Не используй двойной слеш //...  для комментирования
CSS не поддерживает комментарии двойным слешем (исключение: некоторые препроцессоры)

❌
```
a {
  //color: pink;
}
//a { color: pink; }

// Comment {}
a {
  color: pink;
}
```
✅
```
a {
  /* color: pink; */
}
/* a { color: pink;  } */
```

* Ставь пробелы внутри маркеров комментария

❌
```
/*comment*/

/*comment */

/** comment**/
```
✅
```
/* comment */

/** comment **/

/**
 * comment
 */

/*     comment
*/
```


[![](https://webheroschool.ru/logo.png)](http://webheroschool.ru/)