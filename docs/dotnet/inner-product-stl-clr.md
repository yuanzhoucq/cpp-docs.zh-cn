---
title: inner_product (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::inner_product
dev_langs:
- C++
helpviewer_keywords:
- inner_product function [STL/CLR]
ms.assetid: 97d7a507-7494-4216-aedf-0546ed0edb3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b97b1a4be96e697c8e69db9c9d084780dd25d55f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="innerproduct-stlclr"></a>inner_product (STL/CLR)
计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积二元运算替换为其他指定二元运算的一般化程序的结果。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _InIt1, class _InIt2, class _Ty> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val);  
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,  
       class _Fn22> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库数值函数相同`inner_product`。 有关详细信息，请参阅[inner_product](../standard-library/numeric-functions.md#inner_product)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/数字 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)