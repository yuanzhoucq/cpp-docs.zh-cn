---
title: "next_permutation (STL/CLR) | Microsoft Docs"
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
  - "cliext::next_permutation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "next_permutation 函数 [STL/CLR]"
ms.assetid: e36e821f-4b8d-461b-8074-69cd0175ccec
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# next_permutation (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重新排序的范围中的原始元素，以便按照字典。下更大的范围替换，如果该文件存在，其中明年五月有意义指定具有二进制谓词。  
  
## 语法  
  
```  
template<class _BidIt> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `next_permutation`函数相同。  有关详细信息，请参阅[next\_permutation](../Topic/next_permutation.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)