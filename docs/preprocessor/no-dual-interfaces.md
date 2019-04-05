---
title: no_dual_interfaces
ms.date: 11/04/2016
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: ae75bc2e974f374768f1a9e5a0e1ced61e9904b0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023797"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**C++ 专用**

更改编译器为双重接口方法生成包装器函数的方式。

## <a name="syntax"></a>语法

```
no_dual_interfaces
```

## <a name="remarks"></a>备注

通常，该包装器将通过接口的虚函数表调用方法。 与**no_dual_interfaces**，而是调用包装器`IDispatch::Invoke`来调用该方法。

**结束 C++ 专用**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)