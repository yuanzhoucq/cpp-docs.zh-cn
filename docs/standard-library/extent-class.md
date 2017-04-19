---
title: "extent 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- extent
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: 20
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
ms.openlocfilehash: 23cf8230cd5b8adb7975ec21a249d9efc4d66c71
ms.lasthandoff: 02/24/2017

---
# <a name="extent-class"></a>extent 类
获取数组维度。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty, unsigned I = 0>  
struct extent;  
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
 `I`  
 绑定到查询的数组。  
  
## <a name="remarks"></a>备注  
 如果 `Ty` 是至少具有 `I` 维度的数组类型，则类型查询保留在由 `I` 指定的维度中的元素数。 如果 `Ty` 不是数组类型或它的级别小于 `I`，或者如果 `I` 为零且 `Ty` 属于类型“`U` 的未知绑定的数组”，则类型查询保留值 0。  
  
## <a name="example"></a>示例  
  
```cpp  
// std__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
extent 0 == 5  
extent 1 == 10  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_all_extents 类](../standard-library/remove-all-extents-class.md)   
 [remove_extent 类](../standard-library/remove-extent-class.md)

