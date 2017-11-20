---
title: "生成 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::generate
dev_langs: C++
helpviewer_keywords: generate function [STL/CLR]
ms.assetid: 970f209f-31db-47c4-a0bb-4c3e579adb52
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a2941894e6aa63708f9878abbf33f1335f812ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="generate-stlclr"></a>generate (STL/CLR)
将函数对象生成的值分配给范围中的每个元素。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _FwdIt, class _Fn0> inline  
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`generate`。 有关详细信息，请参阅[生成](../standard-library/algorithm-functions.md#generate)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)