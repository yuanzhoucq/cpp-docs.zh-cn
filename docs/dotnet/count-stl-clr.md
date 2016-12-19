---
title: "count (STL/CLR) | Microsoft Docs"
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
  - "cliext::count"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "count 函数 [STL/CLR]"
ms.assetid: 6d10abb4-3c48-469c-804c-281015b12865
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# count (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回范围中其值与指定值匹配的元素的数量。  
  
## 语法  
  
```  
template<class _InIt, class _Ty> inline  
    typename iterator_traits<_InIt>::difference_type  
        count(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
## 备注  
 此函数行为与 STL `count`函数相同。  有关详细信息，请参阅[count](../Topic/count.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)