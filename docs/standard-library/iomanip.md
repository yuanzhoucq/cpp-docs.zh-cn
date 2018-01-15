---
title: '&lt;iomanip&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
dev_langs: C++
helpviewer_keywords: iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c2f229f5706902eac1c0326cfb446b4dc650c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;
包含 `iostreams` 标准标头 `<iomanip>` 以定义几个各自采用单个参数的操控器。  
  
## <a name="syntax"></a>语法  
  
```  
#include <iomanip>  
  
```  
  
## <a name="remarks"></a>备注  
 其中每个操控器都会返回重载 `basic_istream`\<**Elem**, **Tr**>`::`[operator>>](../standard-library/istream-operators.md#op_gt_gt) 和 `basic_ostream`\<**Elem**, **Tr**>`::`[operator<<](../standard-library/ostream-operators.md#op_lt_lt) 的未指定类型（名称为 **T1** 到 **T10**）。  
  
### <a name="manipulators"></a>操控器  
  
|||  
|-|-|  
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|获取货币金额（可选择采用国际格式）。|  
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|使用指定格式以某种时间结构获取时间。|  
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|提供货币金额（可选择采用国际格式）。|  
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|采用要使用的时间结构和格式字符串提供时间。|  
|[quoted](../standard-library/iomanip-functions.md#quoted)|使用插入和提取运算符实现字符串的方便往返。|  
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|清除指定标志。|  
|[setbase](../standard-library/iomanip-functions.md#setbase)|为整数设置基数。|  
|[setfill](../standard-library/iomanip-functions.md#setfill)|设置用于在右对齐显示中填充空格的字符。|  
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|设置指定标志。|  
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|为浮点值设置精度。|  
|[setw](../standard-library/iomanip-functions.md#setw)|指定显示字段的宽度。|  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



