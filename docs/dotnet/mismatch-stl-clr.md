---
title: "mismatch (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::mismatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "不匹配函数 [STL/CLR]"
ms.assetid: 77876875-44bb-4476-afd9-390da4eaac16
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# mismatch (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效，并找到出现不同的第一个位置。  
  
## 语法  
  
```  
template<class _InIt1, class _InIt2> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
            _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `mismatch`函数相同。  有关详细信息，请参阅[mismatch](../Topic/mismatch.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)