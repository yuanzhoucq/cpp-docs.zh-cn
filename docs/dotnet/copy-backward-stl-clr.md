---
title: "copy_backward (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::copy_backward"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copy_backward 函数 [STL/CLR]"
ms.assetid: 649db3fd-5a79-44b6-bea9-ecbcbeba1f32
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# copy_backward (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

分配元素的值从一种源区到目标排列，循环元素源序列并将它们分配在一个反向的新位置。  
  
## 语法  
  
```  
template<class _BidIt1, class _BidIt2> inline  
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,  
        _BidIt2 _Dest);  
```  
  
## 备注  
 此函数行为与 STL `copy_backward`函数相同。  有关详细信息，请参阅[copy\_backward](../Topic/copy_backward.md)。  
  
## 要求  
 **标头:** \<cliext\/algorithm\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [algorithm](../dotnet/algorithm-stl-clr.md)