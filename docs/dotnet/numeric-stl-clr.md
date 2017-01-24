---
title: "numeric (STL/CLR) | Microsoft Docs"
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
  - "<cliext/numeric>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/numeric> 标头 [STL/CLR]"
  - "<numeric> 标头 [STL/CLR]"
  - "数字函数 [STL/CLR]"
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# numeric (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义执行数值处理算法的容器模板函数。  
  
## 语法  
  
```  
#include <cliext/numeric>  
```  
  
## 函数  
  
|功能|说明|  
|--------|--------|  
|[accumulate](../dotnet/accumulate-stl-clr.md)|通过计算连续的部分和来计算指定范围中所有元素的总和（包括初始值），或计算通过使用指定二元运算而非求和运算获得的连续部分结果的结果总和。|  
|[adjacent\_difference](../dotnet/adjacent-difference-stl-clr.md)|计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。|  
|[inner\_product](../dotnet/inner-product-stl-clr.md)|计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积运算替换为其他指定二元运算的一般化程序的结果。|  
|[partial\_sum](../dotnet/partial-sum-stl-clr.md)|计算输入范围中从第一个元素到第 `i` 个元素的一系列总和，并在目标范围的第 `i` 个元素中存储每个总和的结果，或计算将求和运算替换为其他指定二元运算的一般化程序的结果。|  
  
## 要求  
 **标头：**  \<cliext\/numeric\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)