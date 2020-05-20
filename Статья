#PureScript - Что это?

PureScript - это строго типизированный, чисто функциональный язык программирования, который компилируется в JavaScript.
Его можно использовать для разработки веб-приложений, серверных приложений, а также настольных приложений с использованием Electron.
Его синтаксис в основном сопоставим с синтаксисом Haskell. В эдиторе, он предстовляет ряд полиформизмов и расширяемых записей.
Кроме того, в отличие от Haskell, PureScript придерживается строгой стратегии оценки.

#Особенности

PureScript отличается строгой оценкой, постоянными структурами данных и выводом типов.
Система типов PureScript имеет много общих функций с аналогичными функциональными языками, такими как Haskell: 
алгебраические типы данных и сопоставление с образцом, типы с более высоким родом, 
классы типов и функциональные зависимости и полиморфизм более высокого ранга. 
Система типов PureScript добавляет поддержку полиморфизма строк и расширяемых записей. 
Однако в PureScript отсутствует поддержка некоторых более продвинутых функций Haskell, таких как GADT и семейства типов.

#Примеры кода

Здесь представлен самый простой вариант программы - "Hello world".
```
module Main where

import Effect.Console (log)

main = log "Hello World!"
```
Here, the type of the program is inferred and checked by the PureScript compiler. 
A more verbose version of the same program might include explicit type annotations:
```
module Main where

import Prelude

import Effect (Effect)
import Effect.Console (log)

main :: Effect Unit
main = log "Hello World!"
```
