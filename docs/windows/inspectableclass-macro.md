---
title: InspectableClass 宏
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 55d5aed96ff7c8b01142f8d4de81a431fdfcc2d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631585"
---
# <a name="inspectableclass-macro"></a>InspectableClass 宏

设置运行时类名称和信任级别。

## <a name="syntax"></a>语法

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>参数

*runtimeClassName*<br/>
运行时类的完整文本名称。

*trustLevel*<br/>
之一[TrustLevel](https://msdn.microsoft.com/library/br224625.aspx)枚举值。

## <a name="remarks"></a>备注

**InspectableClass**宏可以仅可用于 Windows 运行时类型。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](../windows/runtimeclass-class.md)