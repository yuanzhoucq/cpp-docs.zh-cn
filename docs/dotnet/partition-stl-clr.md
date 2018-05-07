---
title: 分区 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::partition
dev_langs:
- C++
helpviewer_keywords:
- partition function [STL/CLR]
ms.assetid: 3f551eb3-31ec-4b1d-b585-07718d6a1bd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 91da41eee64ca5f818cb8dfcbc9a7517f3aed144
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="partition-stlclr"></a>partition (STL/CLR)
将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`partition`。 有关详细信息，请参阅[分区](../standard-library/algorithm-functions.md#partition)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)