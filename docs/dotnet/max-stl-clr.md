---
title: "max (STL/CLR) | Microsoft Docs"
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
  - "cliext::max"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max 函数 [STL/CLR]"
ms.assetid: bf51aedc-b7a0-4b6c-a76e-fdbc4af042fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# max (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

比较两个对象并返回两个中大的，其中是排序的标准可以由二进制谓词指定。  
  
## 语法  
  
```  
template<class _Ty> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
## 备注  
 此函数行为与 STL `max`函数相同。  有关详细信息，请参阅[max](../Topic/max.md)。  
  
## 要求  
 **页眉：** \<\/cliext 算法\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)