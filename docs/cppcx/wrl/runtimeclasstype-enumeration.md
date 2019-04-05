---
title: RuntimeClassType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 80e8a120f7e3666721ff839a2a696388a64d734e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035953"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType 枚举

指定的类型[RuntimeClass](runtimeclass-class.md)支持实例。

## <a name="syntax"></a>语法

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|描述|
|----------|-----------------|
|`ClassicCom`|经典的 COM 运行时类。|
|`Delegate`|等效于 `ClassicCom`。|
|`InhibitFtmBase`|禁用`FtmBase`支持的同时，`__WRL_CONFIGURATION_LEGACY__`未定义。|
|`InhibitWeakReference`|禁用弱引用支持。|
|`WinRt`|Windows 运行时类。|
|`WinRtClassicComMix`|`WinRt` 和 `ClassicCom` 的组合。|

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL 命名空间](microsoft-wrl-namespace.md)