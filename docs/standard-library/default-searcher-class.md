---
title: default_searcher类
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 2c8b93b83b271f787c993f789e1a68f84a60f016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368929"
---
# <a name="default_searcher-class"></a>default_searcher类

是`default_searcher`搜索对象构造函数中指定的序列的操作的函数对象类型。 搜索在提供给对象的函数调用运算符的另一个序列中完成。 调用`default_searcher` [std：：搜索](algorithm-functions.md#search)以执行搜索。

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
| **构造 函数** | |
| [default_searcher](#default-searcher-constructor) | |
| **运算符** | |
| [运算符（）](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>default_searcher构造函数

通过使用序列搜索`default_searcher`和相等谓词构造函数对象。

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

*Pred*\
序列元素的可选相等比较谓词。 如果未指定相等比较类型，则默认值为`std::equal_to`。

### <a name="remarks"></a>备注

引发*二进制谓词*或*转发器*类型的复制构造函数引发的任何异常。

此类在 C++17 中是新的。 C++20 使构造函数`constexpr`。

## <a name="operator"></a><a name="operator-call"></a>运算符（）

函数运算符的呼叫运算符。 在参数序列`[first, last)`中搜索指定给构造函数的序列。

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

*第一*\
要在其中搜索的序列的初始元素。

*最后*\
要在其中搜索的序列的末尾。

### <a name="remarks"></a>备注

返回一对迭代器。 初始迭代器*i*是以下有效结果：

`std::search( first, last, pat_first, pat_last, pred )`.

如果*i*= 是*最后*一个，则配对的第二个迭代器是*最后*一个。 否则，它是以下有效结果：

`std::next( i, std::distance( pat_first, pat_last ))`.

此类在 C++17 中是新的。 C++20使呼叫接线`constexpr`员。

## <a name="see-also"></a>另请参阅

[\<功能>](functional.md)\
[算法函数](algorithm-functions.md)\
[分：：搜索](algorithm-functions.md#search)
