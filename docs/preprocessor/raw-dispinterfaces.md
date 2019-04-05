---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: ef8ed3992c77df0f1d551e923ddc90c2d1bb9b0b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027918"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C++ 专用**

告知编译器生成低级别的包装函数的调用调度接口方法和属性的`IDispatch::Invoke`并返回 HRESULT 错误代码。

## <a name="syntax"></a>语法

```
raw_dispinterfaces
```

## <a name="remarks"></a>备注

如果未指定该特性，则只生成高级包装器，它在失败时引发 C++ 异常。

**结束 C++ 专用**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)