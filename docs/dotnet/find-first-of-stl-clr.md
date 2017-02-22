---
title: "find_first_of (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::find_first_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find_first_of 函数 [STL/CLR]"
ms.assetid: d559bad4-fc12-4201-af49-db0e7eec48e8
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# find_first_of (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

搜索的第一次出现的任何在目标范围中的第几个值或一次出现的二进制谓词事实上是等效的指定与元素指定的组任意多个元素。  
  
## 语法  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `find_first_of`函数相同。  有关详细信息，请参阅[find\_first\_of](../Topic/find_first_of.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)