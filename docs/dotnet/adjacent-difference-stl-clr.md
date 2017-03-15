---
title: "adjacent_difference (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "adjacent_difference 函数"
ms.assetid: 2b462e2e-b8f2-4b2e-9b87-5f688d8da9f4
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# adjacent_difference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。  
  
## 语法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## 备注  
 此函数行为与 STL `adjacent_difference`函数相同。  有关详细信息，请参阅[adjacent\_difference](../Topic/adjacent_difference.md)。  
  
## 要求  
 **标头：**  \<cliext\/numeric\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [numeric](../dotnet/numeric-stl-clr.md)