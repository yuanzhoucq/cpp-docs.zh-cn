---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 8a6c335c7afe2cc56613f06abf5c181f05f6bfec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585388"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C + + 专用**

告知编译器生成低级别的包装函数的调用调度接口方法和属性的`IDispatch::Invoke`并返回 HRESULT 错误代码。

## <a name="syntax"></a>语法

```
raw_dispinterfaces
```

## <a name="remarks"></a>备注

如果未指定该特性，则只生成高级包装器，它在失败时引发 C++ 异常。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)