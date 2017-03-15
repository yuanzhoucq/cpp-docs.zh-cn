---
title: "find (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find 函数 [STL/CLR]"
ms.assetid: 88391e24-1239-4087-b1c2-96efba0337c1
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# find (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在范围中找到具有指定值的元素的第一个匹配项位置。  
  
## 语法  
  
```  
template<class _InIt, class _Ty> inline  
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
## 备注  
 此函数行为与 STL `find`函数相同。  有关详细信息，请参阅[find](../Topic/find%20\(STL\).md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)