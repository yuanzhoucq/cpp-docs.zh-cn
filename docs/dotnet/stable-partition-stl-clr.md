---
title: "stable_partition (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stable_partition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stable_partition 函数 [STL/CLR]"
ms.assetid: b82c194c-ae38-4afb-b255-a95a4c2b3101
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# stable_partition (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在分类范围的元素分为两相交集，并且这些元素满足前面无法满足该类型的一元谓词，保持等效元素相关命令。  
  
## 语法  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `stable_partition`函数相同。  有关详细信息，请参阅[stable\_partition](../Topic/stable_partition.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)