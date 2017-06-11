# コレクション - Haskell レシピ集

リストとマップの操作を中心に扱います。

## マップ

マップは`containers`の`Data.Map`に定義されています。

`Prelude`の関数と同じ名前の関数が多いので、`qualified`でインポートするとよいです。

```haskell
-- containers
import Data.Map (Map)
import qualified Data.Map as Map
```

このレシピ集では`Data.Map`モジュールを、このようにインポートしたものとして扱います。

以下の例では`Data.Map.empty`と`Data.Map.singlton`を参照しているものと読んでください。

```haskell
> Map.empty
fromList []
> Map.singleton 1 'a'
fromList [(1,'a')]
```
