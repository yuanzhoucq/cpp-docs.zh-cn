---
title: for_each (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::for_each
dev_langs:
- C++
helpviewer_keywords:
- for_each function [STL/CLR]
ms.assetid: 4c391ecf-cd35-499e-a3f5-35b965e0da9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 54ce400f02e0b9fa04ab0e051234fa3eaef3182a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="foreach-stlclr"></a>for_each (STL/CLR)
将指定的函数对象按向前顺序应用于范围中的每个元素并返回此函数对象。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _Fn1> inline  
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`for_each`。 有关详细信息，请参阅[for_each](../standard-library/algorithm-functions.md#for_each)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)