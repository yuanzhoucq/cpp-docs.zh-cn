---
title: boyer_moore_searcher类
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_searcher
helpviewer_keywords:
- std::boyer_moore_searcher [C++]
ms.openlocfilehash: 54e5c4b7c9fe27d6df32f56d57eb1207fa09332c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366773"
---
# <a name="boyer_moore_searcher-class"></a>boyer_moore_searcher类

类`boyer_moore_searcher`是一种函数对象类型，它使用 Boyer-Moore 算法来搜索对象构造函数中指定的序列。 搜索在提供给对象的函数调用运算符的另一个序列中完成。 类作为参数传递给[std：：search](algorithm-functions.md#search)的重载之一。

## <a name="syntax"></a>语法

```cpp
template <
    class RandomAccessIterator1,
    class Hash = hash<typename iterator_traits<RandomAccessIterator1>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_searcher
{
    boyer_moore_searcher(
        RandomAccessIterator1 pat_first,
        RandomAccessIterator1 pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>成员

| | |
| - | - |
| **构造 函数** | |
|[boyer_moore_searcher](#boyer-moore-searcher-constructor)||
| **运算符** | |
| [运算符（）](#operator-call) | |

## <a name="boyer_moore_searcher-constructor"></a><a name="boyer-moore-searcher-constructor"></a>boyer_moore_searcher构造函数

通过使用序列搜索`boyer_moore_searcher`、哈希函数对象和相等谓词来构造函数对象。

```cpp
boyer_moore_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>参数

*pat_first*\
要搜索的序列的初始元素。

*pat_last*\
要搜索的序列的末尾。

*高频*\
用于哈希序列元素的可调用对象。

*Pred*\
序列元素的可选相等比较谓词。 如果未指定相等比较类型，则默认值为`std::equal_to`。

### <a name="remarks"></a>备注

引发*BinaryPredicate、**哈希*或*随机访问迭代器*类型的复制构造函数或*BinaryPredicate*或*哈希*的调用运算符引发的任何异常。

此类在 C++17 中是新的。

## <a name="operator"></a><a name="operator-call"></a>运算符（）

函数对象的调用运算符。 在参数序列`[first, last)`中搜索指定给构造函数的序列。

```cpp
template <class ForwardIterator2>
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>参数

*第一*\
要在其中搜索的序列的初始元素。

*最后*\
要在其中搜索的序列的末尾。

### <a name="remarks"></a>备注

如果搜索模式`[pat_first, pat_last)`为空，则返回`make_pair(first, first)`。 如果未找到搜索模式，则返回`make_pair(last, last)`。 否则，将一对迭代器返回到序列的开始和结束`[first, last)`，该序列等于`[pat_first, pat_last)`谓词 *。*

此类在 C++17 中是新的。

## <a name="see-also"></a>另请参阅

[\<功能>](functional.md)\
[算法函数](algorithm-functions.md)\
[boyer_moore_horspool_searcher类](boyer-moore-horspool-searcher-class.md)\
[分：：搜索](algorithm-functions.md#search)
