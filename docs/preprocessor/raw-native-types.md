---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: e48aa2ca1469d38b67dcb06a3377713141a158e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620436"
---
# <a name="rawnativetypes"></a>raw_native_types
**C + + 专用**

禁止在高级包装器函数中使用 COM 支持类，并强制改用低级数据类型。    

## <a name="syntax"></a>语法

```
raw_native_types
```

## <a name="remarks"></a>备注

默认情况下，高级错误处理方法使用 COM 支持类[_bstr_t](../cpp/bstr-t-class.md)并[_variant_t](../cpp/variant-t-class.md)来代替`BSTR`和`VARIANT`数据类型和原始 COM 接口指针。 这些类封装了为这些数据类型分配和解除分配内存存储的详细信息，并大大简化了类型强制转换和转换操作。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)