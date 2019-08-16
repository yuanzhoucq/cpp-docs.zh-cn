---
title: InspectableClass 宏
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: ee2a76edb967923a03ce6720b4163baf1cc48c32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500479"
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
[TrustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel)枚举值之一。

## <a name="remarks"></a>备注

**InspectableClass**宏只能与 Windows 运行时类型一起使用。

## <a name="requirements"></a>要求

**标头:** 实现。h

**命名空间：** Microsoft:: WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](runtimeclass-class.md)