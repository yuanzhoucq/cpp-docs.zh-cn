---
title: "replace_copy_if (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::replace_copy_if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "replace_copy_if 函数 [STL/CLR]"
ms.assetid: 60edf9b8-34e6-4d94-a611-363ef7b7fb80
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# replace_copy_if (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。  
  
## 语法  
  
```  
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline  
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred, const _Ty% _Val);  
```  
  
## 备注  
 此函数行为与 STL `replace_copy_if`函数相同。  有关详细信息，请参阅[replace\_copy\_if](../Topic/replace_copy_if.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)