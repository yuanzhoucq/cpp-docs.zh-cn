---
title: "lower_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound 函数 [STL/CLR]"
ms.assetid: 841b70b5-1f54-4ecf-8faa-7dda32a24c54
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在排序的范围中查找其值小于或等效于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。  
  
## 语法  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `lower_bound`函数相同。  有关详细信息，请参阅[lower\_bound](../Topic/lower_bound.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)