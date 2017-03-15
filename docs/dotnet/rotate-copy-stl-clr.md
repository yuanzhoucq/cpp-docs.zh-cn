---
title: "rotate_copy (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::rotate_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rotate_copy 函数 [STL/CLR]"
ms.assetid: ed697552-130f-474f-9ab6-133332bb2587
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# rotate_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交换是在两个相邻范围的元素。源区中复制结果与目标范围。  
  
## 语法  
  
```  
template<class _FwdIt, class _OutIt> inline  
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,  
        _OutIt _Dest);  
```  
  
## 备注  
 此函数行为与 STL `rotate_copy`函数相同。  有关详细信息，请参阅[rotate\_copy](../Topic/rotate_copy.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)