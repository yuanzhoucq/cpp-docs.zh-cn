---
title: "remove_copy_if (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::remove_copy_if
dev_langs: C++
helpviewer_keywords: remove_copy_if function [STL/CLR]
ms.assetid: 5307f5fe-b6bb-4968-8da1-fea84ab96655
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 199ee8f04fbc62d9251ebe77ae63715328fcfe20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="removecopyif-stlclr"></a>remove_copy_if (STL/CLR)
将源范围中的元素复制到目标范围（不复制满足谓词的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`remove_copy_if`。 有关详细信息，请参阅[remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)