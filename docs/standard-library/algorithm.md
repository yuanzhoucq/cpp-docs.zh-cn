---
title: '&lt;算法&gt; | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <algorithm>
dev_langs:
- C++
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9de7d5606d2bb178dd786d22bb0e5ab890fd16ff
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964231"
---
# <a name="ltalgorithmgt"></a>&lt;算法&gt;

定义执行算法的 C++ 标准库容器模板函数。

## <a name="syntax"></a>语法

```cpp
(see relevant links below for specific algorithm syntax)
```

## <a name="remarks"></a>备注

C++ 标准库算法可在多种数据结构上运算，因此属于通用算法。 可用 C++ 标准库运算的数据结构不仅包括 C++ 标准库容器类（例如 `vector` 和 `list`），还包括程序定义的数据结构和满足特定算法要求的元素数组。 C++ 标准库算法通过迭代器间接访问并遍历容器元素来实现这种通用性。

C++ 标准库算法处理迭代器范围通常是由其开始或末尾位置指定。 引用的范围必须有效，即范围中的所有指针必须可以取消引用，并且在每个范围的序列中，可从第一个位置递增到达最后一个位置。

C++ 标准库算法扩展了由每个 C++ 标准库容器的运算和成员函数支持的操作，并允许同时处理不同类型的容器对象。 两个后缀已用于传递与算法目的相关的信息。

- `_if` 后缀指示将算法用于对元素的值（而非元素本身的值）产生作用的函数对象。 `find_if` 算法查找其值满足函数对象指定的条件的元素，`find` 算法搜索特定值。

- _copy 后缀指示算法不仅操作元素的值，还将修改的值复制到目标范围。 `reverse` 算法反向排序范围中的元素，`reverse_copy` 算法还将结果复制到目标范围。

C++ 标准库算法通常会按照其目的或需求相关指示信息进行分组。 这些包括更改元素值的修改算法和不更改元素值的非修改算法。 改变算法将更改元素顺序，但不更改其元素的值。 移除算法可将元素从范围或范围副本中消除。 排序算法重新排序以各种方式范围中的元素，并已排序的范围算法只作用于其元素具有以特定方式排序的范围。

为数值处理提供的 C++ 标准库数值算法具有自己的标头文件 [\<numeric>](../standard-library/numeric.md)，而函数对象和适配器则在标头 [\<functional>](../standard-library/functional.md) 中定义。返回布尔值的函数对象称为谓词。 默认二元谓词是比较 `operator<`。 通常，排序的元素需小于比较元素，因此，给定任意两个元素，可以确定它们是等效的（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。

### <a name="function-templates"></a>函数模板

|函数模板|描述|
|-|-|
|[adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)|搜索相等或满足指定条件的两个相邻元素。|
|[all_of](../standard-library/algorithm-functions.md#all_of)|返回 **，则返回 true**位于给定范围中的每个元素满足条件时。|
|[any_of](../standard-library/algorithm-functions.md#any_of)|返回 **，则返回 true**满足条件时指定的元素范围中的至少一次。|
|[binary_search](../standard-library/algorithm-functions.md#binary_search)|测试已排序的范围中是否有等于指定值的元素，或在二元谓词指定的意义上与指定值等效的元素。|
|[copy](../standard-library/algorithm-functions.md#copy)|将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向前方向的新位置。|
|[copy_backward](../standard-library/algorithm-functions.md#copy_backward)|将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向后方向的新位置。|
|[copy_if](../standard-library/algorithm-functions.md#copy_if)|测试某个给定范围内复制所有元素 **，则返回 true**针对指定的条件|
|[copy_n](../standard-library/algorithm-functions.md#copy_n)|复制指定数量的元素。|
|[count](../standard-library/algorithm-functions.md#count)|返回范围中其值与指定值匹配的元素的数量。|
|[count_if](../standard-library/algorithm-functions.md#count_if)|返回范围中其值与指定条件匹配的元素的数量。|
|[equal](../standard-library/algorithm-functions.md#equal)|逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效。|
|[equal_range](../standard-library/algorithm-functions.md#equal_range)|在排序的范围中查找符合以下条件的位置对：第一个位置小于或等效于指定元素的位置，第二个位置大于此元素位置，等效意义或用于在序列中建立位置的排序可通过二元谓词指定。|
|[fill](../standard-library/algorithm-functions.md#fill)|将相同的新值分配给指定范围中的每个元素。|
|[fill_n](../standard-library/algorithm-functions.md#fill_n)|将新值分配给以特定元素开始的范围中的指定数量的元素。|
|[find](../standard-library/algorithm-functions.md#find)|在范围中找到具有指定值的元素的第一个匹配项位置。|
|[find_end](../standard-library/algorithm-functions.md#find_end)|在范围中查找与指定序列相同的最后一个序列，或在二元谓词指定的意义上等效的最后一个序列。|
|[find_first_of](../standard-library/algorithm-functions.md#find_first_of)|在目标范围中搜索若干值中任意值的第一个匹配项，或搜索在二元谓词指定的意义上等效于指定元素集的若干元素中任意元素的第一个匹配项。|
|[find_if](../standard-library/algorithm-functions.md#find_if)|在范围中找到满足指定条件的元素的第一个匹配项位置。|
|[find_if_not](../standard-library/algorithm-functions.md#find_if_not)|返回指示的范围中不满足条件的第一个元素。|
|[for_each](../standard-library/algorithm-functions.md#for_each)|将指定的函数对象按向前顺序应用于范围中的每个元素并返回此函数对象。|
|[generate](../standard-library/algorithm-functions.md#generate)|将函数对象生成的值分配给范围中的每个元素。|
|[generate_n](../standard-library/algorithm-functions.md#generate_n)|将函数对象生成的值分配给范围中指定数量的元素，并返回到超出最后一个分配值的下一位置。|
|[includes](../standard-library/algorithm-functions.md#includes)|测试一个排序的范围是否包含另一排序范围中的所有元素，其中元素之间的排序或等效条件可通过二元谓词指定。|
|[inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)|将两个连续的排序范围中的元素合并为一个排序范围，其中排序条件可通过二元谓词指定。|
|[is_heap](../standard-library/algorithm-functions.md#is_heap)|返回 **，则返回 true**如果指定范围中的元素形成堆。|
|[is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)|返回 **，则返回 true**如果指定的范围形成一个堆，直到最后一个元素。|
|[is_partitioned](../standard-library/algorithm-functions.md#is_partitioned)|返回 **，则返回 true**如果给定范围中的所有元素的都测试**true**对某个条件都测试的所有元素之前**false**。|
|[is_permutation](../standard-library/algorithm-functions.md#is_permutation)|确定给定范围的元素是否形成有效排列。|
|[is_sorted](../standard-library/algorithm-functions.md#is_sorted)|返回 **，则返回 true**如果指定范围中的元素按顺序排序。|
|[is_sorted_until](../standard-library/algorithm-functions.md#is_sorted_until)|返回 **，则返回 true**如果指定范围中的元素按顺序排序。|
|[iter_swap](../standard-library/algorithm-functions.md#iter_swap)|交换由一对指定迭代器引用的两个值。|
|[lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare)|逐个元素比较两个序列以确定其中的较小序列。|
|[lower_bound](../standard-library/algorithm-functions.md#lower_bound)|在排序的范围中查找其值大于或等效于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。|
|[make_heap](../standard-library/algorithm-functions.md#make_heap)|将指定范围中的元素转换到第一个元素是最大元素的堆中，其中排序条件可通过二元谓词指定。|
|[max](../standard-library/algorithm-functions.md#max)|比较两个对象并返回较大对象，其中排序条件可通过二元谓词指定。|
|[max_element](../standard-library/algorithm-functions.md#max_element)|在指定范围中查找最大元素的第一个匹配项，其中排序条件可通过二元谓词指定。|
|[merge](../standard-library/algorithm-functions.md#merge)|将两个排序的源范围中的所有元素合并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[min](../standard-library/algorithm-functions.md#min)|比较两个对象并返回较小对象，其中排序条件可通过二元谓词指定。|
|[min_element](../standard-library/algorithm-functions.md#min_element)|在指定范围中查找最小元素的第一个匹配项，其中排序条件可通过二元谓词指定。|
|[minmax](../standard-library/algorithm-functions.md#minmax)|比较两个输入参数，并按最小到最大的顺序将它们作为参数对返回。|
|[minmax_element](../standard-library/algorithm-functions.md#minmax_element)|在一次调用中执行 [min_element](../standard-library/algorithm-functions.md#min_element) 和 [max_element](../standard-library/algorithm-functions.md#max_element) 执行的操作。|
|[mismatch](../standard-library/algorithm-functions.md#mismatch)|逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效，并找到出现不同的第一个位置。|
|[&lt;alg&gt; move](../standard-library/algorithm-functions.md#alg_move)|移动与指定范围关联的元素。|
|[move_backward](../standard-library/algorithm-functions.md#move_backward)|将一个迭代器的元素移动到另一迭代器。 移动从指定范围的最后一个元素开始，并在此范围的第一个元素结束。|
|[next_permutation](../standard-library/algorithm-functions.md#next_permutation)|重新排序范围中的元素，以便使用按字典顺序的下一个更大排列（如果有）替换原有排序，其中“下一个”的意义可通过二元谓词指定。|
|[none_of](../standard-library/algorithm-functions.md#none_of)|返回 **，则返回 true**满足条件时永远不会在给定范围中没有元素。|
|[nth_element](../standard-library/algorithm-functions.md#nth_element)|对范围内的元素分区，正确找到范围中序列的第 *n* 个元素，以使序列中位于此元素之前的所有元素小于或等于此元素，位于此元素之后的所有元素大于或等于此元素。|
|[partial_sort](../standard-library/algorithm-functions.md#partial_sort)|将范围中指定数量的较小元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。|
|[partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy)|将源范围中的元素复制到目标范围，其中源元素按降序或二元谓词指定的其他顺序排序。|
|[partition](../standard-library/algorithm-functions.md#partition)|将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前。|
|[partition_copy](../standard-library/algorithm-functions.md#partition_copy)|是的条件的元素复制 **，则返回 true**到一个目标和条件为**false**到另一个。 元素必须来自于指定范围。|
|[partition_point](../standard-library/algorithm-functions.md#partition_point)|返回给定范围中不满足条件的第一个元素。 元素经过排序，满足条件的元素在不满足条件的元素之前。|
|[pop_heap](../standard-library/algorithm-functions.md#pop_heap)|移除从堆顶到范围中倒数第二个位置之间的最大元素，然后将剩余元素形成新堆。|
|[prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)|重新排序范围中的元素，以便使用按字典顺序的下一个更大排列（如果有）替换原有排序，其中“下一个”的意义可通过二元谓词指定。|
|[push_heap](../standard-library/algorithm-functions.md#push_heap)|将范围末尾的元素添加到包括范围中前面元素的现有堆中。|
|[random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)|将范围中 *N* 个元素的序列重新排序为随机 *N*! 种序列中的 可能排列之一。|
|[remove](../standard-library/algorithm-functions.md#remove)|从给定范围中消除指定值，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。|
|[remove_copy](../standard-library/algorithm-functions.md#remove_copy)|将源范围中的元素复制到目标范围（不复制具有指定值的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。|
|[remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)|将源范围中的元素复制到目标范围（不复制满足谓词的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。|
|[remove_if](../standard-library/algorithm-functions.md#remove_if)|从给定范围中消除满足谓词的元素，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。|
|[replace](../standard-library/algorithm-functions.md#replace)|检查范围中的每个元素，并替换与指定值匹配的元素。|
|[replace_copy](../standard-library/algorithm-functions.md#replace_copy)|检查源范围中的每个元素，并替换与指定值匹配的元素，同时将结果复制到新的目标范围。|
|[replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)|检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。|
|[replace_if](../standard-library/algorithm-functions.md#replace_if)|检查范围中的每个元素，并替换满足指定谓词的元素。|
|[reverse](../standard-library/algorithm-functions.md#reverse)|反转范围中元素的顺序。|
|[reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)|反转源范围中元素的顺序，同时将这些元素复制到目标范围|
|[rotate](../standard-library/algorithm-functions.md#rotate)|交换两个相邻范围中的元素。|
|[rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)|交换源范围中两个相邻范围内的元素，并将结果复制到目标范围。|
|[search](../standard-library/algorithm-functions.md#search)|在目标范围中搜索其元素与给定序列中的元素相等或在二元谓词指定的意义上等效于给定序列中的元素的序列的第一个匹配项。|
|[search_n](../standard-library/algorithm-functions.md#search_n)|在范围中搜索具有特定值或按二元谓词的指定与此值相关的指定数量的元素。|
|[set_difference](../standard-library/algorithm-functions.md#set_difference)|将属于一个排序的源范围、但不属于另一排序的源范围的所有元素相并到一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[set_intersection](../standard-library/algorithm-functions.md#set_intersection)|将属于两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference)|将属于一个而不是两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[set_union](../standard-library/algorithm-functions.md#set_union)|将至少属于两个排序的源范围之一的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|
|[sort](../standard-library/algorithm-functions.md#sort)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。|
|[shuffle](../standard-library/algorithm-functions.md#shuffle)|使用随机数生成器重新排列给定范围中的元素。|
|[sort_heap](../standard-library/algorithm-functions.md#sort_heap)|将堆转换为排序的范围。|
|[stable_partition](../standard-library/algorithm-functions.md#stable_partition)|将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前，并保留等效元素的相对顺序。|
|[stable_sort](../standard-library/algorithm-functions.md#stable_sort)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列，并保留等效元素的相对顺序。|
|[swap](../standard-library/algorithm-functions.md#swap)|在两种类型的对象之间交换元素值，将第一个对象的内容分配给第二个对象，将第二个对象的内容分配给第一个对象。|
|[swap_ranges](../standard-library/algorithm-functions.md#swap_ranges)|将一个范围中的元素与另一大小相等的范围中的元素交换。|
|[transform](../standard-library/algorithm-functions.md#transform)|将指定的函数对象应用于源范围中的每个元素或两个源范围中的元素对，并将函数对象的返回值复制到目标范围。|
|[unique](../standard-library/algorithm-functions.md#unique)|移除指定范围中彼此相邻的重复元素。|
|[unique_copy](../standard-library/algorithm-functions.md#unique_copy)|将源范围中的元素复制到目标范围，彼此相邻的重复元素除外。|
|[upper_bound](../standard-library/algorithm-functions.md#upper_bound)|在排序的范围中查找其值大于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
