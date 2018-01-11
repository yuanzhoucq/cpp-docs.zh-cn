---
title: "删除 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::remove
dev_langs: C++
helpviewer_keywords: remove function [STL/CLR]
ms.assetid: 85a11883-3e25-49aa-b4a0-b2cffd6dc110
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c866d920451cd9ae21d161630520813b699a3eff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)