---
title: RuntimeClassType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 3b869be00cdc405569b82bdf3730f8d4ca4f3aab
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335778"
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

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)