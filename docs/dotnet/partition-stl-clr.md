---
title: "partition (STL/CLR) | Microsoft Docs"
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
  - "cliext::partition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "partition 函数 [STL/CLR]"
ms.assetid: 3f551eb3-31ec-4b1d-b585-07718d6a1bd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# partition (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前。  
  
## 语法  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `partition`函数相同。  有关详细信息，请参阅[partition](../Topic/partition.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)