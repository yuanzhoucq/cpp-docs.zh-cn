---
title: "aligned_storage 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- aligned_storage
- type_traits/std::aligned_storage
dev_langs:
- C++
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 0da44c2fb505b2edbce9e5ccb028a6e167b4cf17
ms.lasthandoff: 02/24/2017

---
# <a name="alignedstorage-class"></a>aligned_storage 类
生成适当对齐的类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <std::size_t Len, std::size_t Align>  
struct aligned_storage;  
 
template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>  
using aligned_storage_t = typename aligned_storage<Len, Align>::type;  
```  
  
#### <a name="parameters"></a>参数  
 `Len`  
 对象大小。  
  
 `Align`  
 对象对齐方式。  
  
## <a name="remarks"></a>备注  
 模板成员 typedef `type` 与对齐方式为 `Align`、大小为 `Len` 的 POD 类型为同义词。 对于某些类型 `T`，`Align` 必须等于 `alignment_of<T>::value`，或为默认对齐方式。  
  
## <a name="example"></a>示例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
typedef std::aligned_storage<sizeof (int),   
    std::alignment_of<double>::value>::type New_type;   
int main()   
    {   
    std::cout << "alignment_of<int> == "   
        << std::alignment_of<int>::value << std::endl;   
    std::cout << "aligned to double == "   
        << std::alignment_of<New_type>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
alignment_of<int> == 4  
aligned to double == 8  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [alignment_of Class](../standard-library/alignment-of-class.md)

