---
title: "unchecked_array_iterator 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- stdext::unchecked_array_iterator
dev_langs:
- C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02d95c517f6e4af3cd519f05b0ab9c1469c63241
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator 类
通过 `unchecked_array_iterator` 类，可以将数组或指针包装到未经检查的迭代器。 使用此类作为原始指针或数组的包装器（使用 [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) 函数），可以有针对性地管理未经检查的指针警告，无需从全局静默处理这些警告。 如果可能，请优先使用此类的经检查版本 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。  
  
> [!NOTE]
>  此类为 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。  
  
## <a name="syntax"></a>语法  
  
```
template <class Iterator>  
class unchecked_array_iterator;
```  
  
## <a name="remarks"></a>备注  
 此类在 [stdext](../standard-library/stdext-namespace.md) 命名空间中定义。  
  
 此为 [checked_array_iterator 类](../standard-library/checked-array-iterator-class.md)的未经检查版本，支持所有相同重载和成员。 有关经过检查迭代器的功能的更多信息和代码示例，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<iterator>  
  
 **命名空间：** stdext  
  
## <a name="see-also"></a>请参阅  
 [\<iterator>](../standard-library/iterator.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)



