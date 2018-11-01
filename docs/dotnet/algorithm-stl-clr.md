---
title: algorithm (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
ms.openlocfilehash: 6011aad0ef86bc0e633687a6d8e017e9b12771c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528721"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)

定义执行算法的 STL/CLR 容器模板函数。

## <a name="syntax"></a>语法

```cpp
#include <cliext/algorithm>
```

## <a name="requirements"></a>要求

**标头：** \<cliext/算法 >

**Namespace:** cliext

## <a name="declarations"></a>声明

|函数|描述|
|--------------|-----------------|
|[adjacent_find (STL/CLR)](#adjacent_find)|搜索相等的两个相邻元素。|
|[binary_search (STL/CLR)](#binary_search)|测试是否已排序的序列包含给定的值。|
|[copy (STL/CLR)](#copy)|副本源范围中的值复制到目标范围，在正向循环访问。|
|[copy_backward (STL/CLR)](#copy_backward)|副本源范围中的值复制到目标范围，向后循环访问。|
|[count (STL/CLR)](#count)|返回范围中其值与指定值匹配的元素的数量。|
|[count_if (STL/CLR)](#count_if)|返回范围中其值与指定条件匹配的元素的数量。|
|[equal (STL/CLR)](#equal)|比较两个范围，元素的元素。|
|[equal_range (STL/CLR)](#equal_range)|搜索值的有序的序列，并返回完全相等的给定元素的值的子序列分隔的两个位置。|
|[fill (STL/CLR)](#fill)|将相同的新值分配给指定范围中的每个元素。|
|[fill_n (STL/CLR)](#fill_n)|将新值分配给以特定元素开始的范围中指定数量的元素。|
|[find (STL/CLR)](#find)|返回指定值的第一个匹配项的位置。|
|[find_end (STL/CLR)](#find_end)|返回与指定序列相同范围中最后一个子序列。|
|[find_first_of (STL/CLR)](#find_first_of)|搜索任何一个给定的一系列元素的第一个匹配项的范围。|
|[find_if (STL/CLR)](#find_if)|返回的值序列中其中元素满足指定的条件的第一个元素的位置。|
|[for_each (STL/CLR)](#for_each)|将指定的函数对象应用于一系列值中的每个元素并返回函数对象。|
|[generate (STL/CLR)](#generate)|将分配到每个元素的值序列中的函数对象生成的值。|
|[generate_n (STL/CLR)](#generate_n)|将分配到指定数量的元素的函数对象生成的值。|
|[includes (STL/CLR)](#includes)|测试是否一个已排序的范围包含第二个已排序范围中的所有元素。|
|[inplace_merge (STL/CLR)](#inplace_merge)|将两个连续已排序范围中的元素合并为一个已排序范围。|
|[iter_swap (STL/CLR)](#iter_swap)|交换由一对指定迭代器引用的两个值。|
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|比较两个序列，元素的元素，标识哪些序列两个较小者。|
|[lower_bound (STL/CLR)](#lower_bound)|查找第一个元素的位置中的值大于或等于指定值的值的有序序列。|
|[make_heap (STL/CLR)](#make_heap)|指定范围中的元素转换为堆上的第一个元素是最大堆。|
|[最大值 (STL/CLR)](#max))|比较两个对象并返回两个更高版本。|
|[max_element (STL/CLR)](#max_element)|查找指定的值序列中的最大元素。|
|[merge (STL/CLR)](#merge))|将两个已排序的源范围中的所有元素都合并为一个已排序目标范围。|
|[min (STL/CLR)](#min)|比较两个对象并返回两个较小值。|
|[min_element (STL/CLR)](#min_element)|查找指定的值序列中的最小元素。|
|[mismatch (STL/CLR)](#mismatch)|比较两个范围元素的元素并返回第一个位置出现不同。|
|[next_permutation (STL/CLR)](#next_permutation)|重新排序范围中的元素，以便如果它存在的原始顺序将替换为按字典顺序下一个更大排列。|
|[nth_element (STL/CLR)](#nth_element)|分区一系列元素，正确找到`n`个元素序列，以便在它前面的所有元素都均小于或等于它和其后的所有元素都都都大于或等于它。|
|[partial_sort (STL/CLR)](#partial_sort)|按降序顺序排列指定的数量的范围中较小元素。|
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|将元素源范围中复制到目标范围，以便源范围中的元素进行排序。|
|[partition (STL/CLR)](#partition)|以便满足一元谓词的那些元素前加上一元满足该谓词的排列元素范围中。|
|[pop_heap (STL/CLR)](#pop_heap)|将最大元素从堆顶移至末尾，然后形成新堆的其余元素。|
|[prev_permutation (STL/CLR)](#prev_permutation)|重新排序的元素序列，以便如果它存在的原始顺序将替换为按字典顺序前一个更大排列。|
|[push_heap (STL/CLR)](#push_heap)|将范围末尾的元素添加到包括范围中前面元素的现有堆中。|
|[random_shuffle (STL/CLR)](#random_shuffle)|重新排列一系列`N`到某个范围内的元素`N`！ 可能排列之一。|
|[remove (STL/CLR)](#remove)|从给定范围中删除指定的值，而不影响剩余元素的顺序，并返回指定值的新范围的末尾。|
|[remove_copy (STL/CLR)](#remove_copy)|将元素从一个源范围复制到目标范围，只不过不复制指定的值的元素，而不影响剩余元素的顺序。|
|[remove_copy_if (STL/CLR)](#remove_copy_if)|副本源范围中的元素复制到目标范围，除了那些满足谓词，而不影响剩余元素的顺序。|
|[remove_if (STL/CLR)](#remove_if)|删除而不影响剩余元素的顺序满足给定范围中的谓词的元素。 .|
|[replace (STL/CLR)](#replace)|替换范围中具有新值的指定的值匹配的元素。|
|[replace_copy (STL/CLR)](#replace_copy)|副本源范围中的元素复制到目标范围，替换为新值的指定的值匹配的元素。|
|[replace_copy_if (STL/CLR)](#replace_copy_if)|检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。|
|[replace_if (STL/CLR)](#replace_if)|检查范围中的每个元素，并替换满足指定谓词的元素。|
|[reverse (STL/CLR)](#reverse)|反转范围中元素的顺序。|
|[reverse_copy (STL/CLR)](#reverse_copy)|同时将它们复制到目标范围反转源范围内元素的顺序。|
|[rotate (STL/CLR)](#rotate)|交换两个相邻范围中的元素。|
|[rotate_copy (STL/CLR)](#rotate_copy)|交换源范围中两个相邻范围内的元素，并将结果复制到目标范围。|
|[search (STL/CLR)](#search_)|在目标范围中搜索其元素与给定序列中的元素相等或在二元谓词指定的意义上等效于给定序列中的元素的序列的第一个匹配项。|
|[search_n (STL/CLR)](#search_n)|在范围中搜索具有特定值或按二元谓词的指定与此值相关的指定数量的元素。|
|[set_difference (STL/CLR)](#set_difference)|将属于一个排序的源范围、但不属于另一排序的源范围的所有元素相并到一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[set_intersection (STL/CLR)](#set_intersection)|将属于两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|将属于一个而不是两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[set_union (STL/CLR)](#set_union))|将至少属于两个排序的源范围之一的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[sort (STL/CLR)](#sort)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。|
|[sort_heap (STL/CLR)](#sort_heap)|将堆转换为排序的范围。|
|[stable_partition (STL/CLR)](#stable_partition)|将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前，并保留等效元素的相对顺序。|
|[stable_sort (STL/CLR)](#stable_sort)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列，并保留等效元素的相对顺序。|
|[swap (STL/CLR)](#swap)|在两种类型的对象之间交换元素值，将第一个对象的内容分配给第二个对象，将第二个对象的内容分配给第一个对象。|
|[swap_ranges (STL/CLR)](#swap_ranges)|将一个范围中的元素与另一大小相等的范围中的元素交换。|
|[transform (STL/CLR)](#transform)|将指定的函数对象应用于源范围中的每个元素或两个源范围中的元素对，并将函数对象的返回值复制到目标范围。|
|[unique (STL/CLR)](#unique)|移除指定范围中彼此相邻的重复元素。|
|[unique_copy (STL/CLR)](#unique_copy)|将源范围中的元素复制到目标范围，彼此相邻的重复元素除外。|
|[upper_bound (STL/CLR)](#upper_bound)|在排序的范围中查找其值大于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。|

## <a name="members"></a>成员

## <a name="adjacent_find"></a> adjacent_find (STL/CLR)

搜索相等或满足指定条件的两个相邻元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`adjacent_find`。 有关详细信息，请参阅[adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)。

## <a name="binary_search"></a> binary_search (STL/CLR)

测试已排序的范围中是否有等于指定值的元素，或在二元谓词指定的意义上与指定值等效的元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Ty> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`binary_search`。 有关详细信息，请参阅[binary_search](../standard-library/algorithm-functions.md#binary_search)。

## <a name="copy"></a> 复制 (STL/CLR)

将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向前方向的新位置。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`copy`。 有关详细信息，请参阅[复制](../standard-library/algorithm-functions.md#copy)。

## <a name="copy_backward"></a> copy_backward (STL/CLR)

将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向后方向的新位置。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt1, class _BidIt2> inline
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,
        _BidIt2 _Dest);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`copy_backward`。 有关详细信息，请参阅[copy_backward](../standard-library/algorithm-functions.md#copy_backward)。

## <a name="count"></a> count (STL/CLR)

返回范围中其值与指定值匹配的元素的数量。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _Ty> inline
    typename iterator_traits<_InIt>::difference_type
        count(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`count`。 有关详细信息，请参阅[计数](../standard-library/algorithm-functions.md#count)。

## <a name="count_if"></a> count_if (STL/CLR)

返回范围中其值与指定条件匹配的元素的数量。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _Pr> inline
    typename iterator_traits<_InIt>::difference_type
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`count_if`。 有关详细信息，请参阅[count_if](../standard-library/algorithm-functions.md#count_if)。

## <a name="equal"></a> 等于 (STL/CLR)

逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`equal`。 有关详细信息，请参阅[等于](../standard-library/algorithm-functions.md#equal)。

## <a name="equal_range"></a> equal_range (STL/CLR)

在排序的范围中查找符合以下条件的位置对：第一个位置小于或等效于指定元素的位置，第二个位置大于此元素位置，等效意义或用于在序列中建立位置的排序可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Ty> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`equal_range`。 有关详细信息，请参阅[equal_range](../standard-library/algorithm-functions.md#equal_range)。

## <a name="fill"></a> 填充 (STL/CLR)

将相同的新值分配给指定范围中的每个元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Ty> inline
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`fill`。 有关详细信息，请参阅[填充](../standard-library/algorithm-functions.md#fill)。

## <a name="fill_n"></a> fill_n (STL/CLR)

将新值分配给以特定元素开始的范围中指定数量的元素。

### <a name="syntax"></a>语法

```cpp
template<class _OutIt, class _Diff, class _Ty> inline
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`fill_n`。 有关详细信息，请参阅[fill_n](../standard-library/algorithm-functions.md#fill_n)。

## <a name="find"></a> find (STL/CLR)

在范围中找到具有指定值的元素的第一个匹配项位置。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _Ty> inline
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`find`。 有关详细信息，请参阅[查找](../standard-library/algorithm-functions.md#find)。

## <a name="find_end"></a> find_end (STL/CLR)

在范围中查找与指定序列相同的最后一个序列，或在二元谓词指定的意义上等效的最后一个序列。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`find_end`。 有关详细信息，请参阅[find_end](../standard-library/algorithm-functions.md#find_end)。

## <a name="find_first_of"></a> find_first_of (STL/CLR)

在目标范围中搜索若干值中任意值的第一个匹配项，或搜索在二元谓词指定的意义上等效于指定元素集的若干元素中任意元素的第一个匹配项。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`find_first_of`。 有关详细信息，请参阅[find_first_of](../standard-library/algorithm-functions.md#find_first_of)。

## <a name="find_if"></a> find_if (STL/CLR)

在范围中找到满足指定条件的元素的第一个匹配项位置。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _Pr> inline
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`find_if`。 有关详细信息，请参阅[find_if](../standard-library/algorithm-functions.md#find_if)。

## <a name="for_each"></a> for_each (STL/CLR)

将指定的函数对象按向前顺序应用于范围中的每个元素并返回此函数对象。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _Fn1> inline
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`for_each`。 有关详细信息，请参阅[for_each](../standard-library/algorithm-functions.md#for_each)。

## <a name="generate"></a> 生成 (STL/CLR)

将函数对象生成的值分配给范围中的每个元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Fn0> inline
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`generate`。 有关详细信息，请参阅[生成](../standard-library/algorithm-functions.md#generate)。

## <a name="generate_n"></a> generate_n (STL/CLR)

将函数对象生成的值分配给范围中指定数量的元素，并返回到超出最后一个分配值的下一位置。

### <a name="syntax"></a>语法

```cpp
template<class _OutIt, class _Diff, class _Fn0> inline
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`generate_n`。 有关详细信息，请参阅[generate_n](../standard-library/algorithm-functions.md#generate_n)。

## <a name="includes"></a> 包括 (STL/CLR)

测试一个排序的范围是否包含另一排序范围中的所有元素，其中元素之间的排序或等效条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`includes`。 有关详细信息，请参阅[包括](../standard-library/algorithm-functions.md#includes)。

## <a name="inplace_merge"></a> inplace_merge (STL/CLR)

将两个连续的排序范围中的元素合并为一个排序范围，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`inplace_merge`的详细信息，请参阅[inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)。

## <a name="iter_swap"></a> iter_swap (STL/CLR)

交换由一对指定迭代器引用的两个值。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`iter_swap`。 有关详细信息，请参阅[iter_swap](../standard-library/algorithm-functions.md#iter_swap)。

## <a name="lexicographical_compare"></a> lexicographical_compare (STL/CLR)

逐个元素比较两个序列以确定其中的较小序列。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`lexicographical_compare`。 有关详细信息，请参阅[lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare)。

## <a name="lower_bound"></a> lower_bound (STL/CLR)

第一个元素的位置中查找排序的范围的值小于或等效项指定值，其中排序条件可能会通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`lower_bound`。 有关详细信息，请参阅[lower_bound](../standard-library/algorithm-functions.md#lower_bound)。

## <a name="make_heap"></a> make_heap (STL/CLR)

将指定范围中的元素转换到第一个元素是最大元素的堆中，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void make_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`make_heap`。 有关详细信息，请参阅[make_heap](../standard-library/algorithm-functions.md#make_heap)。

## <a name="max"></a> 最大值 (STL/CLR)

比较两个对象并返回较大对象，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _Ty> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`max`。 有关详细信息，请参阅[最大](../standard-library/algorithm-functions.md#max)。

## <a name="max_element"></a> max_element (STL/CLR)

在指定范围中查找最大元素的第一个匹配项，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`max_element`。 有关详细信息，请参阅[max_element](../standard-library/algorithm-functions.md#max_element)。

## <a name="merge"></a> merge (STL/CLR)

将两个排序的源范围中的所有元素合并为一个排序的目标范围，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`merge`。 有关详细信息，请参阅[合并](../standard-library/algorithm-functions.md#merge)。

## <a name="min"></a> 最小值 (STL/CLR)

比较两个对象并返回较小对象，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _Ty> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`min`。 有关详细信息，请参阅[min](../standard-library/algorithm-functions.md#min)。

## <a name="min_element"></a> min_element (STL/CLR)

在指定范围中查找最小元素的第一个匹配项，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`min_element`。 有关详细信息，请参阅[min_element](../standard-library/algorithm-functions.md#min_element)。

## <a name="mismatch"></a> 不匹配 (STL/CLR)

逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效，并找到出现不同的第一个位置。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
            _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`mismatch`。 有关详细信息，请参阅[不匹配](../standard-library/algorithm-functions.md#mismatch)。

## <a name="next_permutation"></a> next_permutation (STL/CLR)

重新排序范围中的元素，以便使用按字典顺序的下一个更大排列（如果有）替换原有排序，其中“下一个”的意义可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt> inline
    bool next_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`next_permutation`。 有关详细信息，请参阅[next_permutation](../standard-library/algorithm-functions.md#next_permutation)。

## <a name="nth_element"></a> nth_element (STL/CLR)

分区的一系列元素，正确找到`n`个元素的范围中序列，以便它的前面的所有元素都均小于或等于它并按照序列中的所有元素都是大于或等于它。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`nth_element`。 有关详细信息，请参阅[nth_element](../standard-library/algorithm-functions.md#nth_element)。

## <a name="partial_sort"></a> partial_sort (STL/CLR)

将范围中指定数量的较小元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`partial_sort`。 有关详细信息，请参阅[partial_sort](../standard-library/algorithm-functions.md#partial_sort)。

## <a name="partial_sort_copy"></a> partial_sort_copy (STL/CLR)

将源范围中的元素复制到目标范围，其中源元素按降序或二元谓词指定的其他顺序排序。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _RanIt> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2);
template<class _InIt, class _RanIt, class _Pr> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`partial_sort_copy`。 有关详细信息，请参阅[partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy)。

## <a name="partition"></a> 分区 (STL/CLR)

将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`partition`。 有关详细信息，请参阅[分区](../standard-library/algorithm-functions.md#partition)。

## <a name="pop_heap"></a> pop_heap (STL/CLR)

移除从堆顶到范围中倒数第二个位置之间的最大元素，然后将剩余元素形成新堆。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void pop_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`pop_heap`。 有关详细信息，请参阅[pop_heap](../standard-library/algorithm-functions.md#pop_heap)。

## <a name="prev_permutation"></a> prev_permutation (STL/CLR)

重新排序范围中的元素，以便使用按字典顺序的下一个更大排列（如果有）替换原有排序，其中“下一个”的意义可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`prev_permutation`。 有关详细信息，请参阅[prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)。

## <a name="push_heap"></a> push_heap (STL/CLR)

将范围末尾的元素添加到包括范围中前面元素的现有堆中。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void push_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`push_heap`。 有关详细信息，请参阅[push_heap](../standard-library/algorithm-functions.md#push_heap)。

## <a name="random_shuffle"></a> random_shuffle (STL/CLR)

重新排列一系列`N`到某个范围内的元素`N`！ 可能排列之一。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void random_shuffle(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Fn1> inline
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`random_shuffle`。 有关详细信息，请参阅[random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)。

## <a name="remove"></a> 删除 (STL/CLR)

从给定范围中消除指定值，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`remove`。 有关详细信息，请参阅[删除](../standard-library/algorithm-functions.md#remove)。

## <a name="remove_copy"></a> remove_copy (STL/CLR)

将源范围中的元素复制到目标范围（不复制具有指定值的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt remove_copy(_InIt _First, _InIt _Last,
        _OutIt _Dest, const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`remove_copy`。 有关详细信息，请参阅[remove_copy](../standard-library/algorithm-functions.md#remove_copy)。

## <a name="remove_copy_if"></a> remove_copy_if (STL/CLR)

将源范围中的元素复制到目标范围（不复制满足谓词的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`remove_copy_if`。 有关详细信息，请参阅[remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)。

## <a name="remove_if"></a> remove_if (STL/CLR)

从给定范围中消除满足谓词的元素，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Pr> inline
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`remove_if`。 有关详细信息，请参阅[remove_if](../standard-library/algorithm-functions.md#remove_if)。

## <a name="replace"></a> replace (STL/CLR)

检查范围中的每个元素，并替换与指定值匹配的元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Ty> inline
    void replace(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`replace`。 有关详细信息，请参阅[替换为](../standard-library/algorithm-functions.md#replace)。

## <a name="replace_copy"></a> replace_copy (STL/CLR)

检查源范围中的每个元素，并替换与指定值匹配的元素，同时将结果复制到新的目标范围。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`replace_copy`。 有关详细信息，请参阅[replace_copy](../standard-library/algorithm-functions.md#replace_copy)。

## <a name="replace_copy_if"></a> replace_copy_if (STL/CLR)

检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred, const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`replace_copy_if`。 有关详细信息，请参阅[replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)。

## <a name="replace_if"></a> replace_if (STL/CLR)

检查范围中的每个元素，并替换满足指定谓词的元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Pr, class _Ty> inline
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,
        const _Ty% _Val);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`replace_if`。 有关详细信息，请参阅[replace_if](../standard-library/algorithm-functions.md#replace_if)。

## <a name="reverse"></a> reverse (STL/CLR)

反转范围中元素的顺序。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt> inline
    void reverse(_BidIt _First, _BidIt _Last);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`reverse`。 有关详细信息，请参阅[反向](../standard-library/algorithm-functions.md#reverse)。

## <a name="reverse_copy"></a> reverse_copy (STL/CLR)

同时将它们复制到目标范围反转源范围内元素的顺序。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt, class _OutIt> inline
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`reverse_copy`。 有关详细信息，请参阅[reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)。

## <a name="rotate"></a> 旋转 (STL/CLR)

交换两个相邻范围中的元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt> inline
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`rotate`。 有关详细信息，请参阅[旋转](../standard-library/algorithm-functions.md#rotate)。

## <a name="rotate_copy"></a> rotate_copy (STL/CLR)

交换源范围中两个相邻范围内的元素，并将结果复制到目标范围。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _OutIt> inline
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,
        _OutIt _Dest);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`rotate_copy`。 有关详细信息，请参阅[rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)。

## <a name="search_"></a> 搜索 (STL/CLR)

在目标范围中搜索其元素与给定序列中的元素相等或在二元谓词指定的意义上等效于给定序列中的元素的序列的第一个匹配项。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`search`。 有关详细信息，请参阅[搜索](../standard-library/algorithm-functions.md#search)。

## <a name="search_n"></a> search_n (STL/CLR)

在范围中搜索具有特定值或按二元谓词的指定与此值相关的指定数量的元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt1, class _Diff2, class _Ty> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val);
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`search_n`。 有关详细信息，请参阅[search_n](../standard-library/algorithm-functions.md#search_n)。

## <a name="set_difference"></a> set_difference (STL/CLR)

将属于一个排序的源范围、但不属于另一排序的源范围的所有元素相并到一个排序的目标范围，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`set_difference`。 有关详细信息，请参阅[set_difference](../standard-library/algorithm-functions.md#set_difference)。

## <a name="set_intersection"></a> set_intersection (STL/CLR)

将属于两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`set_intersection`。 有关详细信息，请参阅[set_intersection](../standard-library/algorithm-functions.md#set_intersection)。

## <a name="set_symmetric_difference"></a> set_symmetric_difference (STL/CLR)

将属于一个而不是两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`set_symmetric_difference`。 有关详细信息，请参阅[set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference)。

## <a name="set_union"></a> set_union (STL/CLR)

将至少属于两个排序的源范围之一的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`set_union`。 有关详细信息，请参阅[set_union](../standard-library/algorithm-functions.md#set_union)。

## <a name="sort"></a> 排序 (STL/CLR)

将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void sort(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`sort`。 有关详细信息，请参阅[排序](../mfc/reference/cmfclistctrl-class.md#sort)。

## <a name="sort_heap"></a> sort_heap (STL/CLR)

将堆转换为排序的范围。

### <a name="syntax"></a>语法

```cpp
template<class _RanIt> inline
    void sort_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`sort_heap`。 有关详细信息，请参阅[sort_heap](../standard-library/algorithm-functions.md#sort_heap)。

## <a name="stable_partition"></a> stable_partition (STL/CLR)

将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前，并保留等效元素的相对顺序。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`stable_partition`。 有关详细信息，请参阅[stable_partition](../standard-library/algorithm-functions.md#stable_partition)。

## <a name="stable_sort"></a> stable_sort (STL/CLR)

将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列，并保留等效元素的相对顺序。

### <a name="syntax"></a>语法

```cpp
template<class _BidIt> inline
    void stable_sort(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`stable_sort`。 有关详细信息，请参阅[stable_sort](../standard-library/algorithm-functions.md#stable_sort)。

## <a name="swap"></a> 交换 (STL/CLR)

在两种类型的对象之间交换元素值，将第一个对象的内容分配给第二个对象，将第二个对象的内容分配给第一个对象。

### <a name="syntax"></a>语法

```cpp
<class _Ty> inline
    void swap(_Ty% _Left, _Ty% _Right);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`swap`。 有关详细信息，请参阅[交换](../standard-library/algorithm-functions.md#swap)。

## <a name="swap_ranges"></a> swap_ranges (STL/CLR)

将一个范围中的元素与另一大小相等的范围中的元素交换。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`swap_ranges`。 有关详细信息，请参阅[swap_ranges](../standard-library/algorithm-functions.md#swap_ranges)。

## <a name="transform"></a> 转换 (STL/CLR)

将指定的函数对象应用于源范围中的每个元素或两个源范围中的元素对，并将函数对象的返回值复制到目标范围。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _OutIt, class _Fn1> inline
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Fn1 _Func);
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`transform`。 有关详细信息，请参阅[转换](../standard-library/algorithm-functions.md#transform)。

## <a name="unique"></a> 唯一 (STL/CLR)

移除指定范围中彼此相邻的重复元素。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`unique`。 有关详细信息，请参阅[唯一](../standard-library/algorithm-functions.md#unique)。

## <a name="unique_copy"></a> unique_copy (STL/CLR)

将源范围中的元素复制到目标范围，彼此相邻的重复元素除外。

### <a name="syntax"></a>语法

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`unique_copy`。 有关详细信息，请参阅[unique_copy](../standard-library/algorithm-functions.md#unique_copy)。

## <a name="upper_bound"></a> upper_bound (STL/CLR)

在排序的范围中查找其值大于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。

### <a name="syntax"></a>语法

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>备注

此函数的行为与 c + + 标准库函数相同`upper_bound`。 有关详细信息，请参阅[upper_bound](../standard-library/algorithm-functions.md#upper_bound)。