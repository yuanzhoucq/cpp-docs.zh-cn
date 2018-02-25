---
title: "remove_reference 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::remove_reference
dev_langs:
- C++
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ba826580bd06c83a735899f298574fab353445a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="removereference-class"></a>remove_reference 类
从类型设定非引用类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <class T>  
struct remove_reference;  
 
template <class T>  
using remove_reference_t = typename remove_reference<T>::type;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要修改的类型。  
  
## <a name="remarks"></a>备注  
 `remove_reference<T>` 的实例保留修改后的类型，当 `T1` 为 `T` 形式时，此类型为 `T1&`，否则为 `T`。  
  
## <a name="example"></a>示例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_reference_t<int&> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_reference_t<int&> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_reference_t<int&> == int  
```  
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [add_lvalue_reference 类](../standard-library/add-lvalue-reference-class.md)
