---
title: InspectableClass 宏
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 9d194f5a87ac4a142301bc896cb3ed172f119473
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398182"
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
之一[TrustLevel](/windows/desktop/api/inspectable/ne-inspectable-trustlevel)枚举值。

## <a name="remarks"></a>备注

**InspectableClass**宏可以仅可用于 Windows 运行时类型。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[RuntimeClass 类](runtimeclass-class.md)