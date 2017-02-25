---
title: "inplace_merge (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::inplace_merge"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inplace_merge 函数 [STL/CLR]"
ms.assetid: e6948c03-8c5b-4a7c-915c-0a531946a321
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# inplace_merge (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将两个连续的范围的元素分为单个订单的范围，排序的标准可能是按二进制谓词指定。  
  
## 语法  
  
```  
template<class _BidIt> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,  
        _Pr _Pred);  
```  
  
## 备注  
 此函数相同行为与 STL `inplace_merge` 函数对于更多信息，请参见 [inplace\_merge](../Topic/inplace_merge.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)