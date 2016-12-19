---
title: "sort_heap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::sort_heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sort_heap 函数 [STL/CLR]"
ms.assetid: a8fa6b76-90cd-413b-9c5b-f65b93d4bbed
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sort_heap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将堆转换为排序的范围。  
  
## 语法  
  
```  
template<class _RanIt> inline  
    void sort_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `sort_heap`函数相同。  有关详细信息，请参阅[sort\_heap](../Topic/sort_heap.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)