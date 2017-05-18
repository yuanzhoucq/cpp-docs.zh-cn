---
title: "integral_constant 类、bool_constant 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- integral_constant
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- bool_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs:
- C++
helpviewer_keywords:
- integral_constant class
- integral_constant
- bool_constant
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: b64b3ef25622a61fd10bca9d49d527ff232d5c1b
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant 类、bool_constant 类
从类型和值生成整型常量。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, T v>
struct integral_constant {  
   static constexpr T value = v;  
   typedef T value_type;  
   typedef integral_constant<T, v> type;  
   constexpr operator value_type() const noexcept;  
   constexpr value_type operator()() const noexcept;  
   };  
```
  
### <a name="parameters"></a>参数  
*T*  
常量的类型。  
  
*v*  
常量的值。  
  
## <a name="remarks"></a>备注  
使用整型类型 *T* 和该类型的值 *v* 进行专用化的 `integral_constant` 模板类表示一个对象，该对象保留该整型类型的常量以及指定的值。 名为 `type` 的成员是生成的模板专用化类型的别名，`value` 成员具有用于创建此专用化的值 *v*。  
  
`bool_constant` 模板类是将 `bool` 用作 *T* 参数的 `integral_constant` 的显式部分专用化。  
  
## <a name="example"></a>示例  
  
```cpp  
// std__type_traits__integral_constant.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "integral_constant<int, 5> == "   
        << std::integral_constant<int, 5>::value << std::endl;   
    std::cout << "integral_constant<bool, false> == " << std::boolalpha   
        << std::integral_constant<bool, false>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
integral_constant<int, 5> == 5  
integral_constant<bool, false> == false  
```  
  
## <a name="requirements"></a>要求  

**标头：**\<type_traits>
  
**命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [false_type](../standard-library/type-traits-typedefs.md#false_type)   
 [true_type](../standard-library/type-traits-typedefs.md#true_type)


