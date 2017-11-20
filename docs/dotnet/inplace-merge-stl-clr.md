---
title: "inplace_merge (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::inplace_merge
dev_langs: C++
helpviewer_keywords: inplace_merge function [STL/CLR]
ms.assetid: e6948c03-8c5b-4a7c-915c-0a531946a321
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad06f2b7917413617adef6a151e75fb848e8da3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="inplacemerge-stlclr"></a>inplace_merge (STL/CLR)
将两个连续的排序范围中的元素合并为一个排序范围，其中排序条件可通过二元谓词指定。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _BidIt> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`inplace_merge`详细信息，请参阅[inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)