---
title: 算法 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
dev_langs:
- C++
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 30e347905c6802e544cb9f81c045f9cc881f29fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111323"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
定义执行算法的 STL/CLR 容器模板函数。  
  
## <a name="syntax"></a>语法  
  
```  
#include <cliext/algorithm>  
```  
  
## <a name="functions"></a>函数  
  
|函数|描述|  
|--------------|-----------------|  
|[adjacent_find (STL/CLR)](../dotnet/adjacent-find-stl-clr.md)|搜索相等的两个相邻元素。|  
|[binary_search (STL/CLR)](../dotnet/binary-search-stl-clr.md)|测试是否已排序的序列包含一个给定的值。|  
|[copy (STL/CLR)](../dotnet/copy-stl-clr.md)|副本源范围中的值复制到目标范围，循环中的向前方向。|  
|[copy_backward (STL/CLR)](../dotnet/copy-backward-stl-clr.md)|副本源范围中的值复制到目标范围，循环中的向后方向。|  
|[count (STL/CLR)](../dotnet/count-stl-clr.md)|返回范围中其值与指定值匹配的元素的数量。|  
|[count_if (STL/CLR)](../dotnet/count-if-stl-clr.md)|返回范围中其值与指定条件匹配的元素的数量。|  
|[equal (STL/CLR)](../dotnet/equal-stl-clr.md)|比较两个范围，元素的元素。|  
|[equal_range (STL/CLR)](../dotnet/equal-range-stl-clr.md)|搜索值的有序并返回所有等于给定元素的值的子序列分隔的两个位置。|  
|[fill (STL/CLR)](../dotnet/fill-stl-clr.md)|将相同的新值分配给指定范围中的每个元素。|  
|[fill_n (STL/CLR)](../dotnet/fill-n-stl-clr.md)|将新值分配给以特定元素开始的范围中指定数量的元素。|  
|[find (STL/CLR)](../dotnet/find-stl-clr.md)|返回指定值的第一个匹配项的位置。|  
|[find_end (STL/CLR)](../dotnet/find-end-stl-clr.md)|返回范围中与指定序列相同的最后一个子序列。|  
|[find_first_of (STL/CLR)](../dotnet/find-first-of-stl-clr.md)|搜索任何一种给定的一系列元素的第一个匹配项的范围。|  
|[find_if (STL/CLR)](../dotnet/find-if-stl-clr.md)|其中元素满足指定的条件的值序列中返回的第一个元素的位置。|  
|[for_each (STL/CLR)](../dotnet/for-each-stl-clr.md)|将指定的函数对象应用到的值序列中每个元素，并返回函数的对象。|  
|[generate (STL/CLR)](../dotnet/generate-stl-clr.md)|将分配到每个元素值序列中的函数对象生成的值。|  
|[generate_n (STL/CLR)](../dotnet/generate-n-stl-clr.md)|将分配到指定数量的元素的函数对象生成的值。|  
|[includes (STL/CLR)](../dotnet/includes-stl-clr.md)|测试是否包含一排序的范围的第二个已排序的范围中的所有元素。|  
|[inplace_merge (STL/CLR)](../dotnet/inplace-merge-stl-clr.md)|将两个连续的排序范围中的元素合并为一个排序范围中。|  
|[iter_swap (STL/CLR)](../dotnet/iter-swap-stl-clr.md)|交换由一对指定迭代器引用的两个值。|  
|[lexicographical_compare (STL/CLR)](../dotnet/lexicographical-compare-stl-clr.md)|比较两个序列，元素的元素，识别哪个序列两个较小者。|  
|[lower_bound (STL/CLR)](../dotnet/lower-bound-stl-clr.md)|在值的有序序列，其值大于或等于指定的值中查找第一个元素的位置。|  
|[make_heap (STL/CLR)](../dotnet/make-heap-stl-clr.md)|将指定范围中的元素转换到堆上的第一个元素是最大的堆中。|  
|[max (STL/CLR)](../dotnet/max-stl-clr.md)|比较两个对象并返回两个更高版本。|  
|[max_element (STL/CLR)](../dotnet/max-element-stl-clr.md)|指定的值序列中查找最大的元素。|  
|[merge (STL/CLR)](../dotnet/merge-stl-clr.md)|将两个排序的源范围中的所有元素都合并为一个已排序目标范围。|  
|[min (STL/CLR)](../dotnet/min-stl-clr.md)|比较两个对象并返回的两个较小者。|  
|[min_element (STL/CLR)](../dotnet/min-element-stl-clr.md)|查找的值指定序列中的最小元素。|  
|[mismatch (STL/CLR)](../dotnet/mismatch-stl-clr.md)|比较两个范围元素的元素，并返回出现不同的第一个位置。|  
|[next_permutation (STL/CLR)](../dotnet/next-permutation-stl-clr.md)|重新排序范围中的元素，以便如果它存在原有的排序将替换为按字典顺序的下一步的更大排列。|  
|[nth_element (STL/CLR)](../dotnet/nth-element-stl-clr.md)|分区的元素，正确找到序列`n`th 元素的序列，以便前面遮挡它的所有元素都均小于或等于它并在其后的所有元素都都都大于或等于它。|  
|[partial_sort (STL/CLR)](../dotnet/partial-sort-stl-clr.md)|排列指定的大量的范围中的较小元素按非降序顺序排列。|  
|[partial_sort_copy (STL/CLR)](../dotnet/partial-sort-copy-stl-clr.md)|将元素源范围中复制到目标范围，以便源范围中的元素进行排序。|  
|[partition (STL/CLR)](../dotnet/partition-stl-clr.md)|这样，满足一元谓词的元素之前满足一元谓词的请将范围中的元素。|  
|[pop_heap (STL/CLR)](../dotnet/pop-heap-stl-clr.md)|将最大的元素从堆顶移到末尾，然后将剩余元素形成新堆。|  
|[prev_permutation (STL/CLR)](../dotnet/prev-permutation-stl-clr.md)|重新排序的元素序列，以便如果它存在原有的排序将替换为按字典顺序以前的更大排列。|  
|[push_heap (STL/CLR)](../dotnet/push-heap-stl-clr.md)|将范围末尾的元素添加到包括范围中前面元素的现有堆中。|  
|[random_shuffle (STL/CLR)](../dotnet/random-shuffle-stl-clr.md)|重新排列的序列`N`插入其中一个范围中的元素`N`！ 可能排列之一。|  
|[remove (STL/CLR)](../dotnet/remove-stl-clr.md)|从给定范围中删除指定的值，而不影响剩余元素的顺序，并返回指定值的新范围的末尾。|  
|[remove_copy (STL/CLR)](../dotnet/remove-copy-stl-clr.md)|将元素源范围中复制到目标范围，只不过不复制具有指定值的元素，而不影响剩余元素的顺序。|  
|[remove_copy_if (STL/CLR)](../dotnet/remove-copy-if-stl-clr.md)|将源范围中的元素复制到目标范围，除了那些满足谓词，而不影响剩余元素的顺序。|  
|[remove_if (STL/CLR)](../dotnet/remove-if-stl-clr.md)|删除而不影响剩余元素的顺序满足从给定范围谓词的元素。 .|  
|[replace (STL/CLR)](../dotnet/replace-stl-clr.md)|替换范围中与指定的值替换为新值匹配的元素。|  
|[replace_copy (STL/CLR)](../dotnet/replace-copy-stl-clr.md)|将源范围中的元素复制到目标范围，替换与指定的值替换为新值匹配的元素。|  
|[replace_copy_if (STL/CLR)](../dotnet/replace-copy-if-stl-clr.md)|检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。|  
|[replace_if (STL/CLR)](../dotnet/replace-if-stl-clr.md)|检查范围中的每个元素，并替换满足指定谓词的元素。|  
|[reverse (STL/CLR)](../dotnet/reverse-stl-clr.md)|反转范围中元素的顺序。|  
|[reverse_copy (STL/CLR)](../dotnet/reverse-copy-stl-clr.md)|反转源范围中的元素的顺序，同时将它们复制到目标范围。|  
|[rotate (STL/CLR)](../dotnet/rotate-stl-clr.md)|交换两个相邻范围中的元素。|  
|[rotate_copy (STL/CLR)](../dotnet/rotate-copy-stl-clr.md)|交换源范围中两个相邻范围内的元素，并将结果复制到目标范围。|  
|[search (STL/CLR)](../dotnet/search-stl-clr.md)|在目标范围中搜索其元素与给定序列中的元素相等或在二元谓词指定的意义上等效于给定序列中的元素的序列的第一个匹配项。|  
|[search_n (STL/CLR)](../dotnet/search-n-stl-clr.md)|在范围中搜索具有特定值或按二元谓词的指定与此值相关的指定数量的元素。|  
|[set_difference (STL/CLR)](../dotnet/set-difference-stl-clr.md)|将属于一个排序的源范围、但不属于另一排序的源范围的所有元素相并到一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[set_intersection (STL/CLR)](../dotnet/set-intersection-stl-clr.md)|将属于两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[set_symmetric_difference (STL/CLR)](../dotnet/set-symmetric-difference-stl-clr.md)|将属于一个而不是两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[set_union (STL/CLR)](../dotnet/set-union-stl-clr.md)|将至少属于两个排序的源范围之一的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[sort (STL/CLR)](../dotnet/sort-stl-clr.md)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。|  
|[sort_heap (STL/CLR)](../dotnet/sort-heap-stl-clr.md)|将堆转换为排序的范围。|  
|[stable_partition (STL/CLR)](../dotnet/stable-partition-stl-clr.md)|将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前，并保留等效元素的相对顺序。|  
|[stable_sort (STL/CLR)](../dotnet/stable-sort-stl-clr.md)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列，并保留等效元素的相对顺序。|  
|[swap (STL/CLR)](../dotnet/swap-stl-clr.md)|在两种类型的对象之间交换元素值，将第一个对象的内容分配给第二个对象，将第二个对象的内容分配给第一个对象。|  
|[swap_ranges (STL/CLR)](../dotnet/swap-ranges-stl-clr.md)|将一个范围中的元素与另一大小相等的范围中的元素交换。|  
|[transform (STL/CLR)](../dotnet/transform-stl-clr.md)|将指定的函数对象应用于源范围中的每个元素或两个源范围中的元素对，并将函数对象的返回值复制到目标范围。|  
|[unique (STL/CLR)](../dotnet/unique-stl-clr.md)|移除指定范围中彼此相邻的重复元素。|  
|[unique_copy (STL/CLR)](../dotnet/unique-copy-stl-clr.md)|将源范围中的元素复制到目标范围，彼此相邻的重复元素除外。|  
|[upper_bound (STL/CLR)](../dotnet/upper-bound-stl-clr.md)|在排序的范围中查找其值大于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。|  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)