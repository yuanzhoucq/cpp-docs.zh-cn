---
title: "add_volatile 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- add_volatile
- type_traits/std::add_volatile
dev_langs:
- C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
caps.latest.revision: 21
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
ms.sourcegitcommit: 8630a5c0b97b85e0dc75e8b470974bb7d223a511
ms.openlocfilehash: c770950bfb69eaee2fde9aca63b0010f5a2da26a
ms.lasthandoff: 02/24/2017

---
# <a name="addvolatile-class"></a>add_volatile 类
从指定类型创建可变类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty>  
struct add_volatile;  
 
template <class T>
using add_volatile_t = typename add_volatile<T>::type;  
```  
  
### <a name="parameters"></a>参数  
*T*  
要修改的类型。  
  
## <a name="remarks"></a>备注  
`add_volatile<T>` 的实例具有成员 typedef `type`，如果 *T* 为引用、函数或可变限定类型时，则为 *T*，否则为 `volatile` *T*。别名 `add_volatile_t` 是访问成员 typedef `type` 的快捷方式。 
  
## <a name="example"></a>示例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_volatile_t<int> *p = (volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_volatile<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
} 
```  
  
```Output  
add_volatile<int> == int  
```  
  
## <a name="requirements"></a>要求  

**标头：**\<type_traits>  
  
**命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
[<type_traits>](../standard-library/type-traits.md)   
[remove_volatile 类](../standard-library/remove-volatile-class.md)

