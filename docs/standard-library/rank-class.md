---
title: "rank 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- rank
- type_traits/std::rank
dev_langs:
- C++
helpviewer_keywords:
- rank class
- rank
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
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
translationtype: Machine Translation
ms.sourcegitcommit: f0e7b22e4fbd6f54d390adfe70f7bfb99e4bc5df
ms.openlocfilehash: d5b88cb6002d0a96ea84c92877df1083d7e2c4f5
ms.lasthandoff: 02/24/2017

---
# <a name="rank-class"></a>rank 类
获取数组维度数。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty>  
struct rank;  
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 类型查询会保留数组类型 `Ty` 的维度数值，如果 `Ty` 不是数组类型，则为 0。  
  
## <a name="example"></a>示例  
  
```cpp  
// std__type_traits__rank.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "rank<int> == "   
        << std::rank<int>::value << std::endl;   
    std::cout << "rank<int[5]> == "   
        << std::rank<int[5]>::value << std::endl;   
    std::cout << "rank<int[5][10]> == "   
        << std::rank<int[5][10]>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
rank<int> == 0  
rank<int[5]> == 1  
rank<int[5][10]> == 2  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [extent 类](../standard-library/extent-class.md)

