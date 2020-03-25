---
title: RuntimeClassType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213572"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType 枚举

指定受支持的[RuntimeClass](runtimeclass-class.md)实例的类型。

## <a name="syntax"></a>语法

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`ClassicCom`|典型的 COM 运行时类。|
|`Delegate`|等效于 `ClassicCom`。|
|`InhibitFtmBase`|当 `__WRL_CONFIGURATION_LEGACY__` 未定义时禁用 `FtmBase` 支持。|
|`InhibitWeakReference`|禁用弱引用支持。|
|`WinRt`|Windows 运行时类。|
|`WinRtClassicComMix`|`WinRt` 和 `ClassicCom` 的组合。|

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)
