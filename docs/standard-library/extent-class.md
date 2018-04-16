---
title: "extent 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4be9ccb62e4229f2672a8dae0637796c9ce68fc5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_all_extents 类](../standard-library/remove-all-extents-class.md)   
 [remove_extent 类](../standard-library/remove-extent-class.md)
