---
title: "replace_copy_if (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::replace_copy_if
dev_langs: C++
helpviewer_keywords: replace_copy_if function [STL/CLR]
ms.assetid: 60edf9b8-34e6-4d94-a611-363ef7b7fb80
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ce24d602eb5ba24cee4d196c19e1e70cb38ae207
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="replacecopyif-stlclr"></a>replace_copy_if (STL/CLR)
检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline  
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`replace_copy_if`。 有关详细信息，请参阅[replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)