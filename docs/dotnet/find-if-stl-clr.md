---
title: find_if (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::find_if
dev_langs:
- C++
helpviewer_keywords:
- find_if function [STL/CLR]
ms.assetid: fd0db2be-a1e1-417e-8eea-653b08c9577e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b93718e2125d54852802170fd55cb2b5dd2840a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106266"
---
# <a name="findif-stlclr"></a>find_if (STL/CLR)
在范围中找到满足指定条件的元素的第一个匹配项位置。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _Pr> inline  
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`find_if`。 有关详细信息，请参阅[find_if](../standard-library/algorithm-functions.md#find_if)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)