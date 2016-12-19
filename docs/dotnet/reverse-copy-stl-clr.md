---
title: "reverse_copy (STL/CLR) | Microsoft Docs"
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
  - "cliext::reverse_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_copy 函数 [STL/CLR]"
ms.assetid: 694e577a-0fa8-44f7-adde-6dd9f45adefd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# reverse_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反转源范围中元素的顺序，同时将这些元素复制到目标范围  
  
## 语法  
  
```  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
## 备注  
 此函数行为与 STL `reverse_copy`函数相同。  有关详细信息，请参阅[reverse\_copy](../Topic/reverse_copy.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)