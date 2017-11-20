---
title: "replace_if (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::replace_if
dev_langs: C++
helpviewer_keywords: replace_if function [STL/CLR]
ms.assetid: 485ed698-551f-4808-8562-9e32b151786d
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 87e02b927e01ad1b5180c7b25b5192d370d4b009
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="replaceif-stlclr"></a>replace_if (STL/CLR)
检查范围中的每个元素，并替换满足指定谓词的元素。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _FwdIt, class _Pr, class _Ty> inline  
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,  
        const _Ty% _Val);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`replace_if`。 有关详细信息，请参阅[replace_if](../standard-library/algorithm-functions.md#replace_if)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)