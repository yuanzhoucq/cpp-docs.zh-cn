---
title: "搜索和排序 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- sorting data
- data [CRT], searching
- searching [C++], CRT search functions
- searching [C++]
ms.assetid: 15e984f0-e155-46f5-8542-51c458792f54
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 5ba605d61ddcf1ae6bd2adc24c41737536fa2ce9
ms.lasthandoff: 02/24/2017

---
# <a name="searching-and-sorting"></a>搜索和排序
可使用下列函数进行搜索和排序。  
  
### <a name="searching-and-sorting-functions"></a>搜索和排序函数  
  
|函数|搜索或排序|.NET Framework 等效项|  
|--------------|--------------------|-------------------------------|  
|[bsearch](../c-runtime-library/reference/bsearch.md)|二进制搜索|[System::Collections::ArrayList::BinarySearch](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.binarysearch.aspx)|  
|[bsearch_s](../c-runtime-library/reference/bsearch-s.md)|`bsearch` 的更安全版本。|[System::Collections::ArrayList::BinarySearch](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.binarysearch.aspx)|  
|[_lfind](../c-runtime-library/reference/lfind.md)|线性搜索给定值|[System::Collections::ArrayList::Contains](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.contains.aspx)|  
|[_lfind_s](../c-runtime-library/reference/lfind-s.md)|`_lfind` 的更安全版本|[System::Collections::ArrayList::Contains](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.contains.aspx)|  
|[_lsearch](../c-runtime-library/reference/lsearch.md)|线性搜索给定值，如果找不到，则已添加至数组|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_lsearch_s](../c-runtime-library/reference/lsearch-s.md)|`_lsearch` 的更安全版本|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[qsort](../c-runtime-library/reference/qsort.md)|快速排序|[System::Collections::ArrayList::Sort](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)|  
|[qsort_s](../c-runtime-library/reference/qsort-s.md)|`qsort` 的更安全版本|[System::Collections::ArrayList::Sort](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
