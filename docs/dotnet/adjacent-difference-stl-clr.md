---
title: "adjacent_difference (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::adjacent_difference
dev_langs: C++
helpviewer_keywords: adjacent_difference function
ms.assetid: 2b462e2e-b8f2-4b2e-9b87-5f688d8da9f4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 97070578c9293eef3fa88e7094e2a90d25ad9ddd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adjacentdifference-stlclr"></a>adjacent_difference (STL/CLR)
计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`adjacent_difference`。 有关详细信息，请参阅[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/数字 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)