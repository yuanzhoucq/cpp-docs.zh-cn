---
title: "累积 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::accumulate
dev_langs: C++
helpviewer_keywords: accumulate function [STL/CLR]
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50334d4468f34afa10639ad18b649c964b126ee4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="accumulate-stlclr"></a>accumulate (STL/CLR)
通过计算连续部分总和来计算指定范围（包括一些初始值）中所有元素的和，或计算通过指定的二元运算（而不是求和运算）获得的类似的连续部分结果的结果。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`accumulate`。 有关详细信息，请参阅[累积](../standard-library/numeric-functions.md#accumulate)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/数字 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)