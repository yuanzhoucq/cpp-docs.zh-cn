---
title: "aligned_union 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::aligned_union
dev_langs: C++
helpviewer_keywords: aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d217ee9687320e89f4c63469ab0dfff48e633ce9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="alignedunion-class"></a>aligned_union 类
提供足够大并适当对齐的 POD 类型，以存储所需大小的联合类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <std::size_t Len, class... Types>  
struct aligned_union;  
 
template <std::size_t Len, class... Types>  
using aligned_union_t = typename aligned_union<Len, Types...>::type;  
```  
  
#### <a name="parameters"></a>参数  
 `Len`  
 联合中的最大类型的对齐值。  
  
 `Types`  
 基础联合中的不同类型。  
  
## <a name="remarks"></a>备注  
 使用此模板类来获取对齐方式和在未初始化的存储中存储一个联合所需的大小。 成员 typedef `type` 为 `Types` 中列出的任何类型的存储命名一个合适的 POD 类型；最小大小为 `Len`。 类型 `std::size_t` 的静态成员 `alignment_value` 包含 `Types` 中列出的所有类型所要求的最严格的对齐方式。  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 `aligned_union` 来分配对齐的堆栈缓冲区以放置联合。  
  
```  
// std__type_traits__aligned_union.cpp  
#include <iostream>  
#include <type_traits>  
  
union U_type  
{  
    int i;  
    float f;  
    double d;  
    U_type(float e) : f(e) {}  
};  
  
typedef std::aligned_union<16, int, float, double>::type aligned_U_type;  
  
int main()  
{  
    // allocate memory for a U_type aligned on a 16-byte boundary  
    aligned_U_type au;  
    // do placement new in the aligned memory on the stack  
    U_type* u = new (&au) U_type(1.0f);  
    if (nullptr != u)  
    {  
        std::cout << "value of u->i is " << u->i << std::endl;  
        // must clean up placement objects manually!  
        u->~U_type();  
    }  
}  
```  
  
```Output  
value of u->i is 1065353216  
```  
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [alignment_of Class](../standard-library/alignment-of-class.md)
