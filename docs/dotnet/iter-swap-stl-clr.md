---
title: "iter_swap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::iter_swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iter_swap 函数 [STL/CLR]"
ms.assetid: 9809c9f5-2ca6-4e9e-97c1-d7973d3134f8
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# iter_swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交换由一对指定迭代器引用的两个值。  
  
## 语法  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);  
```  
  
## 备注  
 此函数行为与 STL `iter_swap`函数相同。  有关详细信息，请参阅[iter\_swap](../Topic/iter_swap.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)