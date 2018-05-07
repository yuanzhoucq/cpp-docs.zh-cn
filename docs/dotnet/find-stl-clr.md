---
title: 查找 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::find
dev_langs:
- C++
helpviewer_keywords:
- find function [STL/CLR]
ms.assetid: 88391e24-1239-4087-b1c2-96efba0337c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 36447eaf3fb62bf5dedbe91213a98308599854f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="find-stlclr"></a>find (STL/CLR)
在范围中找到具有指定值的元素的第一个匹配项位置。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _Ty> inline  
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`find`。 有关详细信息，请参阅[查找](../standard-library/algorithm-functions.md#find)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)