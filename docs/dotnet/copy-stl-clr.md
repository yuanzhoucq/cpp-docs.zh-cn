---
title: "copy (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copy 函数 [STL/CLR]"
ms.assetid: f6738535-fde6-446e-a797-bf2b457c2bff
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将源区的元素到目标范围，循环访问源元素序列并将它们分配在向前的方向值的新位置。  
  
## 语法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
```  
  
## 备注  
 此函数行为与 STL `copy`函数相同。  有关详细信息，请参阅[copy](../Topic/copy.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)