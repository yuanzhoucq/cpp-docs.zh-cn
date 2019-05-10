---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: ef8ed3992c77df0f1d551e923ddc90c2d1bb9b0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179836"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C++特定**

告知编译器生成低级别的包装函数的调用调度接口方法和属性的`IDispatch::Invoke`并返回 HRESULT 错误代码。

## <a name="syntax"></a>语法

```
raw_dispinterfaces
```

## <a name="remarks"></a>备注

如果未指定该特性，则只生成高级包装器，它在失败时引发 C++ 异常。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)