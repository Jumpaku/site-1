# BOOST_PP_ENUM_PARAMS_WITH_A_DEFAULT

`BOOST_PP_ENUM_PARAMS_WITH_A_DEFAULT` マクロはコンマで区切られた一種類のデフォルト引数付きのパラメータリストを生成する。

## Usage

```cpp
BOOST_PP_ENUM_PARAMS_WITH_A_DEFAULT(count, param, def)
```

## Arguments

- `count` :
	生成するパラメータの個数。
	有効な値の範囲は `0` から `BOOST_PP_LIMIT_REPEAT` まで。

- `param` :
	パラメータのテキスト部。
	`BOOST_PP_ENUM_PARAMS_WITH_A_DEFAULT` は生成したパラメータと `0` から `count - 1` までの範囲の数字とを結合する。

- `def` :
	全てのパラメータにかかるデフォルト値。

## Remarks

このマクロはコンマ区切りのシーケンスに展開される:

```cpp
param ## 0 = def, param ## 1 = def, ... param ## count - 1 = def
```

以前、このマクロは `BOOST_PP_REPEAT` の中で再帰的に使うことは出来なかった。
この制限はもう存在しない。
ライブラリは自動的に実行可能な次の再帰の深さを発見できるからである。

このマクロは廃止された。
これは後方互換性のためにのみ存在する。
代わりに `BOOST_PP_INTERCEPT` を使用した `BOOST_PP_ENUM_BINARY_PARAMS` を用いよ。

```cpp
BOOST_PP_ENUM_BINARY_PARAMS(count, param, = def BOOST_PP_INTERCEPT)
```

## See Also

- [`BOOST_PP_ENUM_BINARY_PARAMS`](enum_binary_params.md)
- [`BOOST_PP_INTERCEPT`](intercept.md)
- [`BOOST_PP_LIMIT_REPEAT`](limit_repeat.md)

## Requirements

Header: &lt;boost/preprocessor/repetition/enum_params_with_a_default.hpp&gt;

## Sample Code

```cpp
#include <boost/preprocessor/repetition/enum_params_with_a_default.hpp>

BOOST_PP_ENUM_PARAMS_WITH_A_DEFAULT(3, class T, int)
	// T0 = int, T1 = int, T2 = int に展開される

BOOST_PP_ENUM_BINARY_PARAMS(3, class T, = int BOOST_PP_INTERCEPT)
	// T0 = int, T1 = int, T2 = int に展開される
```
* BOOST_PP_ENUM_PARAMS_WITH_A_DEFAULT[link enum_params_with_a_default.md]
* BOOST_PP_ENUM_BINARY_PARAMS[link enum_binary_params.md]
* BOOST_PP_INTERCEPT[link intercept.md]

