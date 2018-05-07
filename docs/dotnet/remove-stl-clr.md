---
title: 删除 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::remove
dev_langs:
- C++
helpviewer_keywords:
- remove function [STL/CLR]
ms.assetid: 85a11883-3e25-49aa-b4a0-b2cffd6dc110
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9ef7b6039a3243c52f4c2de56ef73f3afc13b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="remove-stlclr"></a>remove (STL/CLR)
从给定范围中消除指定值，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`remove`。 有关详细信息，请参阅[删除](http://msdn.microsoft.com/Library/77e2585c-441e-448d-bd1d-c893d1356ed8)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)