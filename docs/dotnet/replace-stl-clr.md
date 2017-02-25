---
title: "replace (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::replace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "replace 函数 [STL/CLR]"
ms.assetid: 3792abca-8d73-476a-8540-c5f739aa48c2
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# replace (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检查范围中的每个元素，并替换与指定值匹配的元素。  
  
## 语法  
  
```  
template<class _FwdIt, class _Ty> inline  
    void replace(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## 备注  
 此函数行为与 STL `replace`函数相同。  有关详细信息，请参阅[replace](../Topic/replace.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)