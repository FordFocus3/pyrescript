# PureScript - Что это?

PureScript - это строго типизированный, чисто функциональный язык программирования, который компилируется в JavaScript.
Его можно использовать для разработки веб-приложений, серверных приложений, а также настольных приложений с использованием Electron.
Его синтаксис в основном сопоставим с синтаксисом Haskell. В эдиторе, он предстовляет ряд полиформизмов и расширяемых записей.
Кроме того, в отличие от Haskell, PureScript придерживается строгой стратегии оценки.

# Особенности

PureScript отличается строгой оценкой, постоянными структурами данных и выводом типов.
Система типов PureScript имеет много общих функций с аналогичными функциональными языками, такими как Haskell: 
алгебраические типы данных и сопоставление с образцом, типы с более высоким родом, 
классы типов и функциональные зависимости и полиморфизм более высокого ранга. 
Система типов PureScript добавляет поддержку полиморфизма строк и расширяемых записей. 
Однако в PureScript отсутствует поддержка некоторых более продвинутых функций Haskell, таких как GADT и семейства типов.

# Как начать?

Во-первых, нам нужен NPM. Purescript - это его собственный язык, но мы хотим скомпилировать его в Javascript, который мы можем использовать в браузере, поэтому нам нужен Node.js. Затем мы установим библиотеки Purescript. Pulp будет нашим инструментом для сборки, таким как Cabal.
Bower - это хранилище пакетов, подобное Hackage. Чтобы добавить дополнительные библиотеки в нашу программу, вы должны использовать команду bower. Например, нам нужны целые числа purescript для нашего решения позже в этой статье. Чтобы получить это, запустите команду:
```
bower install --save purescript-integers
```
# Прстой пример
Как только вы всё настроили - время побаловаться с языком. В то время как Purescript компилируется в Javascript, сам язык на самом деле больше похож на Haskell! Мы рассмотрим это в сравнении. Предположим, мы хотим найти все пифагорские тройки, чья сумма меньше 100. Вот как мы можем написать это решение на Хаскеле:
```
sourceList :: [Int]
sourceList = [1..100]
allTriples :: [(Int, Int, Int)]
allTriples =
  [(a, b, c) | a <- sourceList, b <- sourceList, c <- sourceList]
isPythagorean :: (Int, Int, Int) -> Bool
isPythagorean (a, b, c) = a ^ 2 + b ^ 2 == c ^ 2
isSmallEnough :: (Int, Int, Int) -> Bool
isSmallEnough (a, b, c) = a + b + c < 100
finalAnswer :: [(Int, Int, Int)]
finalAnswer = filter 
  (\t -> isPythagorean t && isSmallEnough t)
    allTriples
```
Давайте создадим модуль в Purescript, который позволит нам решить эту же проблему. Начнем с написания модуля ```Pythagoras.purs```. Вот код, который мы напишем, чтобы он соответствовал описанному выше Haskell. Мы рассмотрим детали по частям ниже.
```
module Pythagoras where
import Data.List (List, range, filter)
import Data.Int (pow)
import Prelude
sourceList :: List Int
sourceList = range 1 100
data Triple = Triple
  { a :: Int
  , b :: Int
  , c :: Int
  }
allTriples :: List Triple
allTriples = do
  a <- sourceList
  b <- sourceList
  c <- sourceList
  pure $ Triple {a: a, b: b, c: c}
isPythagorean :: Triple -> Boolean
isPythagorean (Triple triple) =
  (pow triple.a 2) + (pow triple.b 2) == (pow triple.c 2)
isSmallEnough :: Triple -> Boolean
isSmallEnough (Triple triple) =
  (triple.a) + (triple.b) + (triple.c) < 100
finalAnswer :: List Triple
finalAnswer = filter
  (\triple -> isPythagorean triple && isSmallEnough triple) 
  allTriples
```
