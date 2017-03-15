---
title: "fill_n (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::fill_n"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fill_n 函数"
ms.assetid: bb9f2f71-ba1d-44ec-8b47-6ece149dd6b8
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# fill_n (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将新值分配给以特定元素开始的范围中的指定数量的元素。  
  
## 语法  
  
```  
template<class _OutIt, class _Diff, class _Ty> inline  
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);  
```  
  
## 备注  
 此函数行为与 STL `fill_n`函数相同。  有关详细信息，请参阅[fill\_n](../Topic/fill_n.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)