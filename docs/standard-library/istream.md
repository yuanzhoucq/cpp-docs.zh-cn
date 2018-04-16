---
title: '&lt;istream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
dev_langs:
- C++
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83ad1cd6a07e4b8b6ce71e6803170ce3cc1c0342
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltistreamgt"></a>&lt;istream&gt;
定义调解 iostreams 提取的模板类 basic_istream，以及调解插入和提取的模板类 basic_iostream。 标头还定义了一个相关的操控程序。 通常会由另一个 iostreams 标头为你包括此头文件；几乎不需要直接包括它。  
  
## <a name="syntax"></a>语法  
  
```  
#include <istream>  
  
```  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[iostream](../standard-library/istream-typedefs.md#iostream)|专用于 `char` 的类型 `basic_iostream`。|  
|[istream](../standard-library/istream-typedefs.md#istream)|专用于 `char` 的类型 `basic_istream`。|  
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|专用于 **wchar** 的类型 `basic_iostream`。|  
|[wistream](../standard-library/istream-typedefs.md#wistream)|专用于 **wchar** 的类型 `basic_istream`。|  
  
### <a name="manipulators"></a>操控器  
  
|||  
|-|-|  
|[ws](../standard-library/istream-functions.md#ws)|跳过流中的空白。|  
|[swap](../standard-library/istream-functions.md#istream_swap)|交换两个流对象。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|从流中提取字符和字符串。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[basic_iostream](../standard-library/basic-iostream-class.md)|可以完成输入和输出的流类。|  
|[basic_istream](../standard-library/basic-istream-class.md)|该模板类描述一个控制从流缓冲区提取元素和编码对象的对象（其字符特征由类 **Tr** 确定，也称为 [traits_type](../standard-library/basic-ios-class.md#traits_type)），该流缓冲区具有 **Elem** 类型的元素（也称为 [char_type](../standard-library/basic-ios-class.md#char_type)）。|  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



