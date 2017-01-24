---
title: "&lt;algorithm&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<algorithm>"
  - "std::<algorithm>"
  - "algorithm/std::<algorithm>"
  - "std.<algorithm>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<algorithm> 标头"
  - "algorithm 标头 [C++]"
  - "标准 C++ 库, 算法"
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
caps.latest.revision: 23
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;algorithm&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义执行算法的标准模板库 \(STL\) 容器模板函数。  
  
## 语法  
  
```  
(see relevant links below for specific algorithm syntax)  
```  
  
## 备注  
 STL 算法可在多个数据结构上运行，因此是一般算法。  可运行 STL 算法的数据结构不仅包括 STL 容器类（例如 `vector` 和 `list`），还包括程序定义的数据结构和满足特定算法要求的元素数组。  STL 算法通过迭代器间接访问并遍历容器元素来实现此一般性级别。  
  
 STL 算法处理通常由开始或末尾位置指定的迭代器范围。  引用的范围必须有效，即范围中的所有指针必须可以取消引用，并且在每个范围的序列中，可从第一个位置递增到达最后一个位置。  
  
 STL 算法可扩展每个 STL 容器的运算和成员函数支持的操作，并允许同时处理不同类型的容器对象等操作。  两个后缀已用于传递与算法目的相关的信息。  
  
-   `_if` 后缀指示将算法用于对元素的值（而非元素本身的值）产生作用的函数对象。  `find_if` 算法查找其值满足函数对象指定的条件的元素，`find` 算法搜索特定值。  
  
-   \_copy 后缀指示算法不仅操作元素的值，还将修改的值复制到目标范围。  `reverse` 算法反向排序范围中的元素，`reverse_copy` 算法还将结果复制到目标范围。  
  
 STL 算法通常分类到指示与其目的或要求相关的信息的组。  这些包括更改元素值的修改算法和不更改元素值的非修改算法。  改变算法将更改元素顺序，但不更改其元素的值。  移除算法可将元素从范围或范围副本中消除。  排序算法将以各种方式对范围中的元素重新排序，已排序范围算法只作用于已按特定方式排序元素的算法。  
  
 为数值处理提供的 STL 数值算法具有自己的标头文件 [\<numeric\>](../standard-library/numeric.md)，并且函数对象和适配器在标头 [\<functional\>](../standard-library/functional.md) 中定义，返回布尔值的函数对象称为谓词。  默认二元谓词是比较 `operator<`。  通常，排序的元素需小于比较元素，因此，给定任意两个元素，可以确定它们是等效的（即两者均不小于对方）或其中一个小于另一个。  这将导致在非等效元素之间进行排序。  
  
### 函数  
  
|||  
|-|-|  
|[adjacent\_find](../Topic/adjacent_find.md)|搜索相等或满足指定条件的两个相邻元素。|  
|[all\_of](../Topic/all_of.md)|当给定范围中的每个元素均满足条件时返回 `true`。|  
|[any\_of](../Topic/any_of.md)|当指定元素范围中至少有一个元素满足条件时返回 `true`。|  
|[binary\_search](../Topic/binary_search.md)|测试已排序的范围中是否有等于指定值的元素，或在二元谓词指定的意义上与指定值等效的元素。|  
|[copy](../Topic/copy.md)|将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向前方向的新位置。|  
|[copy\_backward](../Topic/copy_backward.md)|将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向后方向的新位置。|  
|[copy\_if](../Topic/copy_if.md)|复制给定范围中对于指定条件为 `true` 的所有元素。|  
|[copy\_n](../Topic/copy_n.md)|复制指定数量的元素。|  
|[count](../Topic/count.md)|返回范围中其值与指定值匹配的元素的数量。|  
|[count\_if](../Topic/count_if.md)|返回范围中其值与指定条件匹配的元素的数量。|  
|[equal](../Topic/equal.md)|逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效。|  
|[equal\_range](../Topic/equal_range.md)|在排序的范围中查找符合以下条件的位置对：第一个位置小于或等效于指定元素的位置，第二个位置大于此元素位置，等效意义或用于在序列中建立位置的排序可通过二元谓词指定。|  
|[fill](../Topic/fill.md)|将相同的新值分配给指定范围中的每个元素。|  
|[fill\_n](../Topic/fill_n.md)|将新值分配给以特定元素开始的范围中的指定数量的元素。|  
|[find](../Topic/find%20\(STL\).md)|在范围中找到具有指定值的元素的第一个匹配项位置。|  
|[find\_end](../Topic/find_end.md)|在范围中查找与指定序列相同的最后一个序列，或在二元谓词指定的意义上等效的最后一个序列。|  
|[find\_first\_of](../Topic/find_first_of.md)|在目标范围中搜索若干值中任意值的第一个匹配项，或搜索在二元谓词指定的意义上等效于指定元素集的若干元素中任意元素的第一个匹配项。|  
|[find\_if](../Topic/find_if.md)|在范围中找到满足指定条件的元素的第一个匹配项位置。|  
|[find\_if\_not](../Topic/find_if_not.md)|返回指示的范围中不满足条件的第一个元素。|  
|[for\_each](../Topic/for_each.md)|将指定的函数对象按向前顺序应用于范围中的每个元素并返回此函数对象。|  
|[generate](../Topic/generate.md)|将函数对象生成的值分配给范围中的每个元素。|  
|[generate\_n](../Topic/generate_n.md)|将函数对象生成的值分配给范围中指定数量的元素，并返回到超出最后一个分配值的下一位置。|  
|[includes](../Topic/includes.md)|测试一个排序的范围是否包含另一排序范围中的所有元素，其中元素之间的排序或等效条件可通过二元谓词指定。|  
|[inplace\_merge](../Topic/inplace_merge.md)|将两个连续的排序范围中的元素合并为一个排序范围，其中排序条件可通过二元谓词指定。|  
|[is\_heap](../Topic/is_heap.md)|如果指定范围中的元素形成堆，则返回 `true`。|  
|[is\_heap\_until](../Topic/is_heap_until.md)|如果指定范围形成直到最后一个元素的堆，则返回 `true`。|  
|[is\_partitioned](../Topic/is_partitioned.md)|如果给定范围中对某个条件测试为 `true` 的所有元素在测试为 `false` 的所有元素之前，则返回 `true`。|  
|[is\_permutation](../Topic/is_permutation.md)|确定给定范围的元素是否形成有效排列。|  
|[is\_sorted](../Topic/is_sorted.md)|如果指定范围中的元素按顺序排序，则返回 `true`。|  
|[is\_sorted\_until](../Topic/is_sorted_until.md)|如果指定范围中的元素按顺序排序，则返回 `true`。|  
|[iter\_swap](../Topic/iter_swap.md)|交换由一对指定迭代器引用的两个值。|  
|[lexicographical\_compare](../Topic/lexicographical_compare.md)|逐个元素比较两个序列以确定其中的较小序列。|  
|[lower\_bound](../Topic/lower_bound.md)|在排序的范围中查找其值大于或等效于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。|  
|[make\_heap](../Topic/make_heap.md)|将指定范围中的元素转换到第一个元素是最大元素的堆中，其中排序条件可通过二元谓词指定。|  
|[max](../Topic/max.md)|比较两个对象并返回较大对象，其中排序条件可通过二元谓词指定。|  
|[max\_element](../Topic/max_element.md)|在指定范围中查找最大元素的第一个匹配项，其中排序条件可通过二元谓词指定。|  
|[merge](../Topic/merge.md)|将两个排序的源范围中的所有元素合并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[min](../Topic/min.md)|比较两个对象并返回较小对象，其中排序条件可通过二元谓词指定。|  
|[min\_element](../Topic/min_element.md)|在指定范围中查找最小元素的第一个匹配项，其中排序条件可通过二元谓词指定。|  
|[minmax](../Topic/minmax.md)|比较两个输入参数，并按最小到最大的顺序将它们作为参数对返回。|  
|[minmax\_element](../Topic/minmax_element.md)|在一次调用中执行 [min\_element](../Topic/min_element.md) 和 [max\_element](../Topic/max_element.md) 执行的操作。|  
|[mismatch](../Topic/mismatch.md)|逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效，并找到出现不同的第一个位置。|  
|[移动](../Topic/%3Calg%3E%20move.md)|移动与指定范围关联的元素。|  
|[move\_backward](../Topic/move_backward.md)|将一个迭代器的元素移动到另一迭代器。  移动从指定范围的最后一个元素开始，并在此范围的第一个元素结束。|  
|[next\_permutation](../Topic/next_permutation.md)|重新排序范围中的元素，以便使用按字典顺序的下一个更大排列（如果有）替换原有排序，其中“下一个”的意义可通过二元谓词指定。|  
|[none\_of](../Topic/none_of.md)|当给定范围中没有元素满足条件时返回 `true`。|  
|[nth\_element](../Topic/nth_element.md)|分区元素范围，正确找到范围中序列的第 *n* 个元素，以使序列中位于此元素之前的所有元素小于或等于此元素，位于此元素之后的所有元素大于或等于此元素。|  
|[partial\_sort](../Topic/partial_sort.md)|将范围中指定数量的较小元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。|  
|[partial\_sort\_copy](../Topic/partial_sort_copy.md)|将源范围中的元素复制到目标范围，其中源元素按降序或二元谓词指定的其他顺序排序。|  
|[partition](../Topic/partition.md)|将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前。|  
|[partition\_copy](../Topic/partition_copy.md)|将条件为 `true` 的元素复制到一个目标，将条件为 `false` 的元素复制到另一目标。  元素必须来自于指定范围。|  
|[partition\_point](../Topic/partition_point.md)|返回给定范围中不满足条件的第一个元素。  元素经过排序，满足条件的元素在不满足条件的元素之前。|  
|[pop\_heap](../Topic/pop_heap.md)|移除从堆顶到范围中倒数第二个位置之间的最大元素，然后将剩余元素形成新堆。|  
|[prev\_permutation](../Topic/prev_permutation.md)|重新排序范围中的元素，以便使用按字典顺序的下一个更大排列（如果有）替换原有排序，其中“下一个”的意义可通过二元谓词指定。|  
|[push\_heap](../Topic/push_heap.md)|将范围末尾的元素添加到包括范围中前面元素的现有堆中。|  
|[random\_shuffle](../Topic/random_shuffle.md)|将范围中 *N* 个元素的序列重新排列为随机选择的 *N*\! 个  可能排列之一。|  
|[remove](../Topic/remove.md)|从给定范围中消除指定值，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。|  
|[remove\_copy](../Topic/remove_copy.md)|将源范围中的元素复制到目标范围（不复制具有指定值的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。|  
|[remove\_copy\_if](../Topic/remove_copy_if.md)|将源范围中的元素复制到目标范围（不复制满足谓词的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。|  
|[remove\_if](../Topic/remove_if.md)|从给定范围中消除满足谓词的元素，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。|  
|[replace](../Topic/replace.md)|检查范围中的每个元素，并替换与指定值匹配的元素。|  
|[replace\_copy](../Topic/replace_copy.md)|检查源范围中的每个元素，并替换与指定值匹配的元素，同时将结果复制到新的目标范围。|  
|[replace\_copy\_if](../Topic/replace_copy_if.md)|检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。|  
|[replace\_if](../Topic/replace_if.md)|检查范围中的每个元素，并替换满足指定谓词的元素。|  
|[reverse](../Topic/reverse.md)|反转范围中元素的顺序。|  
|[reverse\_copy](../Topic/reverse_copy.md)|反转源范围中元素的顺序，同时将这些元素复制到目标范围|  
|[rotate](../Topic/rotate.md)|交换两个相邻范围中的元素。|  
|[rotate\_copy](../Topic/rotate_copy.md)|交换源范围中两个相邻范围内的元素，并将结果复制到目标范围。|  
|[search](../Topic/search.md)|在目标范围中搜索其元素与给定序列中的元素相等或在二元谓词指定的意义上等效于给定序列中的元素的序列的第一个匹配项。|  
|[search\_n](../Topic/search_n.md)|在范围中搜索具有特定值或按二元谓词的指定与此值相关的指定数量的元素。|  
|[set\_difference](../Topic/set_difference.md)|将属于一个排序的源范围、但不属于另一排序的源范围的所有元素相并到一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[set\_intersection](../Topic/set_intersection.md)|将属于两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[set\_symmetric\_difference](../Topic/set_symmetric_difference.md)|将属于一个而不是两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[set\_union](../Topic/set_union.md)|将至少属于两个排序的源范围之一的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。|  
|[sort](../Topic/sort.md)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。|  
|[shuffle](../Topic/std::shuffle.md)|使用随机数生成器重新排列给定范围中的元素。|  
|[sort\_heap](../Topic/sort_heap.md)|将堆转换为排序的范围。|  
|[stable\_partition](../Topic/stable_partition.md)|将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前，并保留等效元素的相对顺序。|  
|[stable\_sort](../Topic/stable_sort.md)|将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列，并保留等效元素的相对顺序。|  
|[swap](../Topic/swap.md)|在两种类型的对象之间交换元素值，将第一个对象的内容分配给第二个对象，将第二个对象的内容分配给第一个对象。|  
|[swap\_ranges](../Topic/swap_ranges.md)|将一个范围中的元素与另一大小相等的范围中的元素交换。|  
|[transform](../Topic/transform.md)|将指定的函数对象应用于源范围中的每个元素或两个源范围中的元素对，并将函数对象的返回值复制到目标范围。|  
|[unique](../Topic/unique%20\(%3Calgorithm%3E\).md)|移除指定范围中彼此相邻的重复元素。|  
|[unique\_copy](../Topic/unique_copy.md)|将源范围中的元素复制到目标范围，彼此相邻的重复元素除外。|  
|[upper\_bound](../Topic/upper_bound.md)|在排序的范围中查找其值大于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)