---
title: "add_const 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- add_const
- type_traits/std::add_const
dev_langs:
- C++
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: cb3ac9b9a7d25d129e1faa1b98cac176153c3966
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="addconst-class"></a>add_const 类
从类型设置常量类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty>  
struct add_const;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要修改的类型。  
  
## <a name="remarks"></a>备注  
 类型修饰符的实例会保留修改后的类型，当 `Ty` 为引用、函数或常量限定类型时，修改后的类型为 `Ty`，否则为 `const Ty`。  
  
## <a name="example"></a>示例  
  
```cpp  
// std__type_traits__add_const.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_const<int>::type *p = (const int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_const<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
add_const<int> == int  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_const 类](../standard-library/remove-const-class.md)

