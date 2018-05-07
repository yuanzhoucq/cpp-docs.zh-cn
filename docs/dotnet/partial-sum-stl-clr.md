---
title: partial_sum (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::partial_sum
dev_langs:
- C++
helpviewer_keywords:
- partial_sum function [STL/CLR]
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c8141e93d7c8101c9bbfaea08c317748cd44f87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="partialsum-stlclr"></a>partial_sum (STL/CLR)
计算一系列从第一个元素到输入范围中的总和`i`th 元素，并将存储在每个此类总和的结果`i`个元素的目标范围，或计算结果的一般化程序的其中求和运算是替换为其他指定二元运算。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`partial_sum`。 有关详细信息，请参阅[partial_sum](../standard-library/numeric-functions.md#partial_sum)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/数字 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)