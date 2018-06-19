---
title: fill_n (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::fill_n
dev_langs:
- C++
helpviewer_keywords:
- fill_n function
ms.assetid: bb9f2f71-ba1d-44ec-8b47-6ece149dd6b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 242061a23f7d3979daf717d0b6c34ee5176e0cce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105668"
---
# <a name="filln-stlclr"></a>fill_n (STL/CLR)
将新值分配给以特定元素开始的范围中指定数量的元素。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _OutIt, class _Diff, class _Ty> inline  
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`fill_n`。 有关详细信息，请参阅[fill_n](../standard-library/algorithm-functions.md#fill_n)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)