---
title: "algorithm (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "<cliext/algorithm>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<algorithm> 标头 [STL/CLR]"
  - "<cliext/algorithm> 标头 [STL/CLR]"
  - "算法函数 [STL/CLR]"
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# algorithm (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义 STL\/CLR 容器执行算法的模板函数。  
  
## 语法  
  
```  
#include <cliext/algorithm>  
```  
  
## 函数  
  
|功能|说明|  
|--------|--------|  
|[adjacent\_find](../dotnet/adjacent-find-stl-clr.md)|相等的两个相邻元素的搜索。|  
|[binary\_search](../dotnet/binary-search-stl-clr.md)|测试的已排序序列是否包含特定值。|  
|[copy](../dotnet/copy-stl-clr.md)|从一个源区的值复制到目标数组，循环访问在向前的方向。|  
|[copy\_backward](../dotnet/copy-backward-stl-clr.md)|从一个源区的值复制到目标数组，循环访问在中向后移动方向。|  
|[count](../dotnet/count-stl-clr.md)|返回中元素的数目。值与某个指定的范围的。|  
|[count\_if](../dotnet/count-if-stl-clr.md)|返回中元素的数目。值满足指定条件范围的。|  
|[equal](../dotnet/equal-stl-clr.md)|比较两范围，由元素的元素。|  
|[equal\_range](../dotnet/equal-range-stl-clr.md)|搜索值的已排序序列并返回分隔值 subsequence 都等于给定元素的两个位置。|  
|[fill](../dotnet/fill-stl-clr.md)|新分配相同的值设置为在指定的范围内的每个元素。|  
|[fill\_n](../dotnet/fill-n-stl-clr.md)|将新值分配给以特定元素开始的范围中的指定数量的元素。|  
|[find](../dotnet/find-stl-clr.md)|返回一个指定的第一次出现的位置。|  
|[find\_end](../dotnet/find-end-stl-clr.md)|返回中与指定的顺序相同的范围内的最后 subsequence。|  
|[find\_first\_of](../dotnet/find-first-of-stl-clr.md)|搜索第一次出现的范围任一特定范围元素。|  
|[find\_if](../dotnet/find-if-stl-clr.md)|返回首个元素的位置。元素满足指定条件值的序列。|  
|[for\_each](../dotnet/for-each-stl-clr.md)|应用于每个元素的指定函数对象在值序列并返回函数对象。|  
|[generate](../dotnet/generate-stl-clr.md)|为每个元素的函数生成的值。对象值序列。|  
|[generate\_n](../dotnet/generate-n-stl-clr.md)|为元素指定数量的对象的函数生成的值。|  
|[includes](../dotnet/includes-stl-clr.md)|测试一排序的范围是在另排序的范围包含的所有元素。|  
|[inplace\_merge](../dotnet/inplace-merge-stl-clr.md)|将两个连续的范围的元素分为单个订单的范围。|  
|[iter\_swap](../dotnet/iter-swap-stl-clr.md)|交换两个值是由一对值指定的迭代器是引用。|  
|[lexicographical\_compare](../dotnet/lexicographical-compare-stl-clr.md)|比较两个序列，该序列是较小者两个元素的元素，标识。|  
|[lower\_bound](../dotnet/lower-bound-stl-clr.md)|查找第一个元素在的位置有一个值是否大于或等于指定值值的有序序列。|  
|[make\_heap](../dotnet/make-heap-stl-clr.md)|转换从指定范围的元素在堆的第一个元素最大堆。|  
|[max](../dotnet/max-stl-clr.md)|对两个对象进行比较并返回的两个。|  
|[max\_element](../dotnet/max-element-stl-clr.md)|在找到值指定序列中的最大值的元素。|  
|[merge](../dotnet/merge-stl-clr.md)|合并两个排序的源区的所有元素放入单个，排序的目标范围。|  
|[min](../dotnet/min-stl-clr.md)|对两个对象进行比较并返回较小者两个。|  
|[min\_element](../dotnet/min-element-stl-clr.md)|查找在值的指定序列中的元素。|  
|[mismatch](../dotnet/mismatch-stl-clr.md)|通过元素比较两范围元素并返回差异生成的第一个位置。|  
|[next\_permutation](../dotnet/next-permutation-stl-clr.md)|重新排序的范围中的原始元素，以便按照字典。下更大的范围替换，如果该文件存在。|  
|[nth\_element](../dotnet/nth-element-stl-clr.md)|分区，正确定位 `n`的元素序列的元素，以便前面的所有元素是否小于或等于它，并按照它的任何元素大于或等于其。|  
|[partial\_sort](../dotnet/partial-sort-stl-clr.md)|具有较小的指定数量的元素范围中的为 nondescending 的顺序。|  
|[partial\_sort\_copy](../dotnet/partial-sort-copy-stl-clr.md)|从一个源区的元素复制到目标范围中源区从这样的元素顺序。|  
|[partition](../dotnet/partition-stl-clr.md)|排列范围的元素会满足一元谓词的元素之前无法满足它的那些。|  
|[pop\_heap](../dotnet/pop-heap-stl-clr.md)|从堆上的移动最大的元素移至结束然后窗体从剩余的元素的新堆。|  
|[prev\_permutation](../dotnet/prev-permutation-stl-clr.md)|重新排列元素序列，以便按照原始字典的以前更大的范围替换，如果该文件存在。|  
|[push\_heap](../dotnet/push-heap-stl-clr.md)|添加在范围的末尾与在包含范围的现有堆的元素的元素。|  
|[random\_shuffle](../dotnet/random-shuffle-stl-clr.md)|重新排列 `N` 元素序列。范围中为一个 `N`。随机的排列方式。|  
|[remove](../dotnet/remove-stl-clr.md)|删除特定范围的一个值，而不干扰其余元素的顺序并返回新范围的末尾释放指定值。|  
|[remove\_copy](../dotnet/remove-copy-stl-clr.md)|从一个源区的元素复制到目标数组，但某个指定的元素不会复制它们，而其余元素的顺序。|  
|[remove\_copy\_if](../dotnet/remove-copy-if-stl-clr.md)|从一个源区的元素复制到目标数组，除非满足某一谓词的，因此，不干扰剩余的元素的顺序。|  
|[remove\_if](../dotnet/remove-if-stl-clr.md)|删除满足给定范围中的谓词，而不干扰剩余的元素的元素。.|  
|[替换](../dotnet/replace-stl-clr.md)|替换匹配一个指定用新值在范围的元素。|  
|[replace\_copy](../dotnet/replace-copy-stl-clr.md)|从一个源区的元素复制到目标数组，替换匹配一个指定用新值的元素。|  
|[replace\_copy\_if](../dotnet/replace-copy-if-stl-clr.md)|检查在源区的每个元素并替换它，如果其满足指定的谓词，则结果复制到新的目标范围时。|  
|[replace\_if](../dotnet/replace-if-stl-clr.md)|如果其满足指定的谓词，在范围的每个元素并替换它。|  
|[reverse](../dotnet/reverse-stl-clr.md)|撤消的元素顺序范围内的。|  
|[reverse\_copy](../dotnet/reverse-copy-stl-clr.md)|撤消元素的排序。源区中，则将其复制到目标范围时。|  
|[rotate](../dotnet/rotate-stl-clr.md)|交换是在两个相邻范围的元素。|  
|[rotate\_copy](../dotnet/rotate-copy-stl-clr.md)|交换是在两个相邻范围的元素。源区中复制结果与目标范围。|  
|[search](../dotnet/search-stl-clr.md)|为序列中的第一个匹配项的搜索。事实上谓词二进制等效的指定这些元素与相等在元素特定顺序或元素与元素位于给定序列的目标范围中。|  
|[search\_n](../dotnet/search-n-stl-clr.md)|第一 subsequence 的搜索范围有指定数量的元素特定值或一关系。该值根据二进制谓词。|  
|[set\_difference](../dotnet/set-difference-stl-clr.md)|相并属于一个排序的源区的所有元素，但是，不为一秒源区顺序，为单个，排序的目标范围，排序的标准可能是按二进制谓词指定。|  
|[set\_intersection](../dotnet/set-intersection-stl-clr.md)|相并属于两个排序的源区到单个的所有元素，排序的目标范围，排序的标准可能是按二进制谓词指定。|  
|[set\_symmetric\_difference](../dotnet/set-symmetric-difference-stl-clr.md)|相并属于一个所有元素，但是，不是两者，排序的源区到单个，排序的目标范围，排序的标准可能是按二进制谓词指定。|  
|[set\_union](../dotnet/set-union-stl-clr.md)|相并属于两个排序的源区至少一个成单个的所有元素，排序的目标范围，排序的标准可能是按二进制谓词指定。|  
|[sort](../dotnet/sort-stl-clr.md)|将位于指定范围的元素到 nondescending 的订单或根据二进制谓词指定一个排序的标准。|  
|[sort\_heap](../dotnet/sort-heap-stl-clr.md)|转换堆到排序的范围。|  
|[stable\_partition](../dotnet/stable-partition-stl-clr.md)|在分类范围的元素分为两相交集，并且这些元素满足前面无法满足该类型的一元谓词，保持等效元素相关命令。|  
|[stable\_sort](../dotnet/stable-sort-stl-clr.md)|将位于指定范围的元素到 nondescending 的订单或根据二进制谓词指定一个排序的标准并保持相对顺序相同的元素。|  
|[swap](../dotnet/swap-stl-clr.md)|交换元素的值对象之间的两种类型的分配，第一个对象到第二个对象的内容和内容第二个到第一个。|  
|[swap\_ranges](../dotnet/swap-ranges-stl-clr.md)|交换个范围的元素与另的元素，调整相同的范围。|  
|[transform](../dotnet/transform-stl-clr.md)|应用指定的函数对象为源区的每个元素或一个对两个源区的元素复制函数对象返回的值。目标范围。|  
|[unique](../dotnet/unique-stl-clr.md)|移除相互靠近的位于指定范围的元素复制。|  
|[unique\_copy](../dotnet/unique-copy-stl-clr.md)|从一个源区的元素复制到目标数组中除靠近彼此周围的元素复制。|  
|[upper\_bound](../dotnet/upper-bound-stl-clr.md)|在有序的范围内（具有大于指定值的值）查找第一个元素的位置，该排序标准可由二进制谓词指定。|  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)