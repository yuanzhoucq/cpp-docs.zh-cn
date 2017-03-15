---
title: "inner_product (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::inner_product"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inner_product 函数 [STL/CLR]"
ms.assetid: 97d7a507-7494-4216-aedf-0546ed0edb3f
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# inner_product (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积运算替换为其他指定二元运算的一般化程序的结果。  
  
## 语法  
  
```  
template<class _InIt1, class _InIt2, class _Ty> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val);  
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,  
       class _Fn22> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);  
```  
  
## 备注  
 此函数行为与 STL `inner_product`函数相同。  有关详细信息，请参阅[inner\_product](../Topic/inner_product.md)。  
  
## 要求  
 **标头：**  \<cliext\/numeric\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [numeric](../dotnet/numeric-stl-clr.md)