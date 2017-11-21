---
title: "remove_all_extents 类 |Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::remove_all_extents
dev_langs: C++
helpviewer_keywords:
- remove_all_extents class
- remove_all_extents
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f1440cc02c7f86582f702fe3fab14820837bc0fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="removeallextents-class"></a>remove_all_extents 类
从数组类型设置非数组类型。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>
struct remove_all_extents;

template <class T>  
using remove_all_extents_t = typename remove_all_extents<T>::type;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要修改的类型。  
  
## <a name="remarks"></a>备注  
 `remove_all_extents<T>` 的实例包含修改类型，即移除了所有数组维度的数组类型 `T` 的元素类型，如果 `T` 不是数组类型，则此实例包含 `T`。  
  
## <a name="example"></a>示例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "remove_all_extents<int> == "   
        << typeid(std::remove_all_extents_t<int>).name()   
        << std::endl;   
    std::cout << "remove_all_extents_t<int[5]> == "   
        << typeid(std::remove_all_extents_t<int[5]>).name()   
        << std::endl;   
    std::cout << "remove_all_extents_t<int[5][10]> == "   
        << typeid(std::remove_all_extents_t<int[5][10]>).name()   
        << std::endl;   
  
    return (0);   
    }  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_extent 类](../standard-library/remove-extent-class.md)
