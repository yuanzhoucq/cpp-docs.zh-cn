---
title: "find_end (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::find_end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find_end 函数 [STL/CLR]"
ms.assetid: a2008414-163a-4da2-9ac6-4e3c85a02d38
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# find_end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在范围中查找与指定序列相同的最后一个序列，或在二元谓词指定的意义上等效的最后一个序列。  
  
## 语法  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `find_end`函数相同。  有关详细信息，请参阅[find\_end](../Topic/find_end.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)