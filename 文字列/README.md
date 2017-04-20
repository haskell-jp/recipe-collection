# 文字列 - Haskell レシピ集

文字や文字列の処理を扱います。

## 文字列の表現

文字列を表す型は``String``は文字を表す型の値を要素とするリストとして表現するのが一般的でした．
標準``Prelude``モジュールでは，

```haskell
type String = [Char]
```

と定義されています．
``String``を使う利点は，リスト上の多相関数であれば ``String`` の対する関数としてそのまま使えることが多いことです．

しかし，最近では，主に入出力における性能改善のために，GHC では``String``型の代りに``Text``型を使うことも多くなりました．
このレシピでは``String``を使う場合と``Text``を使う場合をともに示すことにします．

## ``Text`` を使うときの一般的な設定

``Text``型とその上の便利なライブラリ関数を提供するモジュールは[``text``パッケージ](http://hackage.haskell.org/package/text)で提供されています．
``Text``型を使う場合にはモジュールファイルの先頭に言語拡張``OverloadedString``を指定しておくと，文字列リテラルを``Text``型に対しても使えるので便利です．
また，``text``パッケージが提供するAPIには，標準``Prelude``が提供するAPIと同名のものが多くあるので衝突を避けるために，修飾付きの名前を使うようにすると良いでしょう．

```haskell
{-# LANGUAGE OverloadedStrings #-}
module Foo where

import Data.Text (Text)
import qualified Data.Text as T
import qualified Data.Text.IO as T

main :: IO () 
main = T.interact (T.unlines . map foo . T.lines)

foo :: Text -> Text
foo = const "あらそうですか．"
```
