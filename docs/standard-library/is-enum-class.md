---
title: "is_enum 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_enum
dev_langs: C++
helpviewer_keywords:
- is_enum class
- is_enum
ms.assetid: df3b00b7-4f98-4b3a-96ce-10ad958ee69c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8782ef2f2e8e1499b54043436ba95b821b8e21f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="isenum-class"></a>is_enum 类
测试类型是否为枚举。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty>  
struct is_enum;  
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是枚举类型或枚举类型的 `cv-qualified` 形式，则类型谓词的实例保留为 true，否则保留为 false。  
  
## <a name="example"></a>示例  
  
```cpp  
// std__type_traits__is_enum.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
enum color {   
    red, greed, blue};   
  
int main()   
    {   
    std::cout << "is_enum<trivial> == " << std::boolalpha   
        << std::is_enum<trivial>::value << std::endl;   
    std::cout << "is_enum<color> == " << std::boolalpha   
        << std::is_enum<color>::value << std::endl;   
    std::cout << "is_enum<int> == " << std::boolalpha   
        << std::is_enum<int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_enum<trivial> == false  
is_enum<color> == true  
is_enum<int> == false  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_integral 类](../standard-library/is-integral-class.md)
