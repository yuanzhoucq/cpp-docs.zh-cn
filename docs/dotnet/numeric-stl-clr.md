---
title: 数字 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
dev_langs:
- C++
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4313b80a4fa83e5340f678834b64dd5269278a0d
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305509"
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)
定义容器模板函数执行为数值处理提供的算法。  
  
## <a name="syntax"></a>语法  
  
```  
#include <cliext/numeric>  
```  

## <a name="requirements"></a>要求  
 **标头：** \<cliext/数字 >  
  
 **Namespace:** cliext  
  
## <a name="declarations"></a>声明  
  
|函数|Description|  
|--------------|-----------------|  
|[accumulate (STL/CLR)](#accumulate)|通过计算连续部分总和来计算指定范围（包括一些初始值）中所有元素的和，或计算通过指定的二元运算（而不是求和运算）获得的类似的连续部分结果的结果。|  
|[adjacent_difference (STL/CLR)](#adjacent_difference)|计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。|  
|[inner_product (STL/CLR)](#inner_product)|计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积二元运算替换为其他指定二元运算的一般化程序的结果。|  
|[partial_sum (STL/CLR)](#partial_sum)|计算一系列从第一个元素到输入范围中的总和`i`th 元素，并将存储在每个此类总和的结果`i`个元素的目标范围，或计算结果的一般化程序的其中求和运算是替换为其他指定二元运算。|  
 
## <a name="functions"></a>函数

## <a name="accumulate"></a> 累积 (STL/CLR)
通过计算连续部分总和来计算指定范围（包括一些初始值）中所有元素的和，或计算通过指定的二元运算（而不是求和运算）获得的类似的连续部分结果的结果。  
  
### <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
### <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`accumulate`。 有关详细信息，请参阅[累积](../standard-library/numeric-functions.md#accumulate)。  

## <a name="adjacent_difference"></a> adjacent_difference (STL/CLR)
计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。  
  
### <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
### <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`adjacent_difference`。 有关详细信息，请参阅[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)。  

## <a name="inner_product"></a> inner_product (STL/CLR)
计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积二元运算替换为其他指定二元运算的一般化程序的结果。  
  
###<a name="syntax"></a>语法  
  
```  
template<class _InIt1, class _InIt2, class _Ty> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val);  
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,  
       class _Fn22> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);  
```  
  
### <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`inner_product`。 有关详细信息，请参阅[inner_product](../standard-library/numeric-functions.md#inner_product)。

## <a name="partial_sum"></a> partial_sum (STL/CLR)
计算一系列从第一个元素到输入范围中的总和`i`th 元素，并将存储在每个此类总和的结果`i`个元素的目标范围，或计算结果的一般化程序的其中求和运算是替换为其他指定二元运算。  
  
### <a name="syntax"></a>语法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
### <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`partial_sum`。 有关详细信息，请参阅[partial_sum](../standard-library/numeric-functions.md#partial_sum)。  
    