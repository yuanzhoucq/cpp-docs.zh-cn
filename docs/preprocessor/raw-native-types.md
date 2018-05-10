---
title: raw_native_types |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5baa3204b14da53f6a6a3232874e0ac7de0fd91b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="rawnativetypes"></a>raw_native_types
**C + + 专用**  
  
 禁止在高级包装器函数中使用 COM 支持类，并强制改用低级数据类型。      
  
## <a name="syntax"></a>语法  
  
```  
raw_native_types  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，高级错误处理方法使用 COM 支持类[_bstr_t](../cpp/bstr-t-class.md)和[_variant_t](../cpp/variant-t-class.md)代替了`BSTR`和**VARIANT**数据类型和原始 COM 接口指针。 这些类封装了为这些数据类型分配和解除分配内存存储的详细信息，并大大简化了类型强制转换和转换操作。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)