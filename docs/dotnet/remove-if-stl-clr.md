---
title: "remove_if (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::remove_if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_if 函数 [STL/CLR]"
ms.assetid: de501d3f-965b-4a99-b833-f6fa303fbcdc
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# remove_if (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

消除满足给定范围中的谓词，而不干扰剩余的元素的顺序和返回新范围的末尾释放指定的元素。  
  
## 语法  
  
```  
template<class _FwdIt, class _Pr> inline  
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `remove_if`函数相同。  有关详细信息，请参阅[remove\_if](../Topic/remove_if.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)