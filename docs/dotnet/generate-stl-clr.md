---
title: "generate (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::generate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generate 函数 [STL/CLR]"
ms.assetid: 970f209f-31db-47c4-a0bb-4c3e579adb52
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# generate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将函数对象生成的值分配给范围中的每个元素。  
  
## 语法  
  
```  
template<class _FwdIt, class _Fn0> inline  
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);  
```  
  
## 备注  
 此函数行为与 STL `generate`函数相同。  有关详细信息，请参阅[生成](../Topic/generate.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)