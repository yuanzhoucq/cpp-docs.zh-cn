---
title: "is_unsigned 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_unsigned
dev_langs: C++
helpviewer_keywords:
- is_unsigned class
- is_unsigned
ms.assetid: ba5bec3d-796b-4e54-8595-a3941ec6a8dc
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e08c0f8926ccf2c0e64753887fe67bc19b523c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="isunsigned-class"></a>is_unsigned 类
测试类型是否为无符号整数。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty>  
struct is_unsigned;  
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是无符号整型类型或 `cv-qualified` 无符号整型类型，则类型谓词的实例保持为 true，否则保持为 false。  
  
## <a name="example"></a>示例  
  
```cpp  
// std__type_traits__is_unsigned.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_unsigned<trivial> == " << std::boolalpha   
        << std::is_unsigned<trivial>::value << std::endl;   
    std::cout << "is_unsigned<int> == " << std::boolalpha   
        << std::is_unsigned<int>::value << std::endl;   
    std::cout << "is_unsigned<unsigned int> == " << std::boolalpha   
        << std::is_unsigned<unsigned int>::value << std::endl;   
    std::cout << "is_unsigned<float> == " << std::boolalpha   
        << std::is_unsigned<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_unsigned<trivial> == false  
is_unsigned<int> == false  
is_unsigned<unsigned int> == true  
is_unsigned<float> == false  
```  
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_signed 类](../standard-library/is-signed-class.md)
