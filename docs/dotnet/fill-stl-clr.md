---
title: 填充 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::fill
dev_langs:
- C++
helpviewer_keywords:
- fill function
ms.assetid: eb67241c-9bb3-497e-bec6-639900c60758
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2e1feaba4690bf64d28a7359b3be17d7e70a96f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107433"
---
# <a name="fill-stlclr"></a>fill (STL/CLR)
将相同的新值分配给指定范围中的每个元素。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _FwdIt, class _Ty> inline  
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`fill`。 有关详细信息，请参阅[填充](../standard-library/algorithm-functions.md#fill)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)