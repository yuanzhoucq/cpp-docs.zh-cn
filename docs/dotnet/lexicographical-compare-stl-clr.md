---
title: "lexicographical_compare (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::lexicographical_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lexicographical_compare 函数 [STL/CLR]"
ms.assetid: 9ec217f3-5523-4f90-a0cc-8fb7dbe4946b
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# lexicographical_compare (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

逐个元素比较两个序列以确定其中的较小序列。  
  
## 语法  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `lexicographical_compare`函数相同。  有关详细信息，请参阅[lexicographical\_compare](../Topic/lexicographical_compare.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)