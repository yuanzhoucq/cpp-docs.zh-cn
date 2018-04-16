---
title: "数字 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <cliext/numeric>
dev_langs:
- C++
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cdf9ccb65299af688fde2fbff7b3d6cedad6de96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)
定义容器模板函数执行为数值处理提供的算法。  
  
## <a name="syntax"></a>语法  
  
```  
#include <cliext/numeric>  
```  
  
## <a name="functions"></a>函数  
  
|函数|描述|  
|--------------|-----------------|  
|[accumulate (STL/CLR)](../dotnet/accumulate-stl-clr.md)|通过计算连续部分总和来计算指定范围（包括一些初始值）中所有元素的和，或计算通过指定的二元运算（而不是求和运算）获得的类似的连续部分结果的结果。|  
|[adjacent_difference (STL/CLR)](../dotnet/adjacent-difference-stl-clr.md)|计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。|  
|[inner_product (STL/CLR)](../dotnet/inner-product-stl-clr.md)|计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积二元运算替换为其他指定二元运算的一般化程序的结果。|  
|[partial_sum (STL/CLR)](../dotnet/partial-sum-stl-clr.md)|计算一系列从第一个元素到输入范围中的总和`i`th 元素，并将存储在每个此类总和的结果`i`个元素的目标范围，或计算结果的一般化程序的其中求和运算是替换为其他指定二元运算。|  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/数字 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)