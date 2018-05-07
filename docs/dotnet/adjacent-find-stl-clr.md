---
title: adjacent_find (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::adjacent_find
dev_langs:
- C++
helpviewer_keywords:
- adjacent_find function
ms.assetid: 48bf57ea-b128-4d16-97c5-01d8a378369f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ce62fd96954adb122176e02eb19c00b63d4ebbb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="adjacentfind-stlclr"></a>adjacent_find (STL/CLR)
搜索相等或满足指定条件的两个相邻元素。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _FwdIt> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`adjacent_find`。 有关详细信息，请参阅[adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)