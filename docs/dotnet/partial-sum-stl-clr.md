---
title: "partial_sum (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::partial_sum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "partial_sum 函数 [STL/CLR]"
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# partial_sum (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算输入范围中从第一个元素到第 `i` 个元素的一系列总和，并在目标范围的第 `i` 个元素中存储每个总和的结果，或计算将求和运算替换为其他指定二元运算的一般化程序的结果。  
  
## 语法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## 备注  
 此函数行为与 STL `partial_sum`函数相同。  有关详细信息，请参阅[partial\_sum](../Topic/partial_sum.md)。  
  
## 要求  
 **标头：**  \<cliext\/numeric\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [numeric](../dotnet/numeric-stl-clr.md)