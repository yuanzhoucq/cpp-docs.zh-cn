---
title: "upper_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound 函数 [STL/CLR]"
ms.assetid: a377a77b-8005-496e-85ae-b431a9b2f0b9
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在有序的范围内（具有大于指定值的值）查找第一个元素的位置，该排序标准可由二进制谓词指定。  
  
## 语法  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `upper_bound`函数相同。  有关详细信息，请参阅[upper\_bound](../Topic/upper_bound.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)