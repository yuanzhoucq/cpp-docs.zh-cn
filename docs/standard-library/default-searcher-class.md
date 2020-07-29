---
title: default_searcher 类
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 3b5b05dfa2613f9eeaaa18fa8066bcd44f57d1be
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203723"
---
# <a name="default_searcher-class"></a>default_searcher 类

`default_searcher`是用于搜索在对象的构造函数中指定的序列的操作的函数对象类型。 搜索是在提供给对象的函数调用运算符的另一序列中完成的。 `default_searcher`调用[std：： search](algorithm-functions.md#search)来执行搜索。

## <a name="syntax"></a>语法

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>成员

| | |
| - | - |
| **构造函数** | |
| [default_searcher](#default-searcher-constructor) | |
| **运算符** | |
| [operator （）](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>default_searcher 构造函数

`default_searcher`使用序列搜索和相等谓词来构造函数对象。

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>参数

*pat_first*\
要搜索的序列的初始元素。

*pat_last*\
要搜索的序列的末尾。

*pred*\
序列元素的可选相等比较谓词。 如果未指定相等比较类型，则默认值为 `std::equal_to` 。

### <a name="remarks"></a>备注

引发*BinaryPredicate*或*ForwardIterator*类型的复制构造函数引发的任何异常。

此类是 c + + 17 中新增的。 C + + 20 生成构造函数 **`constexpr`** 。

## <a name="operator"></a><a name="operator-call"></a>operator （）

函数运算符的调用运算符。 在参数序列内搜索 `[first, last)` 指定给构造函数的序列。

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>参数

*1*\
要在其中进行搜索的序列的初始元素。

*时间*\
要在其中进行搜索的序列的末尾。

### <a name="remarks"></a>备注

返回一对迭代器。 初始迭代器*i*是的有效结果：

`std::search( first, last, pat_first, pat_last, pred )`.

如果*i** 是*最后*一个，则对的第二个迭代器是*最后一个*。 否则，结果为：

`std::next( i, std::distance( pat_first, pat_last ))`.

此类是 c + + 17 中新增的。 C + + 20 已成为调用运算符 **`constexpr`** 。

## <a name="see-also"></a>另请参阅

[\<functional>](functional.md)\
[算法函数](algorithm-functions.md)\
[std：： search](algorithm-functions.md#search)
