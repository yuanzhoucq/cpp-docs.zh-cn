---
title: "accumulate (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::accumulate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accumulate 函数 [STL/CLR]"
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# accumulate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

被计算顺序部分计算和所有元素的总和在指定的范围中包括某些初始值或计算从使用的指定二进制操作类似获取的顺序部分结果除和之外。  
  
## 语法  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## 备注  
 此函数行为与 STL 数字 `accumulate`函数相同。  有关详细信息，请参阅[accumulate](../Topic/accumulate.md)。  
  
## 要求  
 **页眉：** \<\/cliext 数字\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [numeric](../dotnet/numeric-stl-clr.md)