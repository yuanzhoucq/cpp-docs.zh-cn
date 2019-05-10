---
title: FactoryCacheFlags 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 8cf4af2ac0b4557fc6b175b84c47f83dd8a6e4ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398454"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 枚举

确定是否缓存工厂对象。

## <a name="syntax"></a>语法

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>备注

默认情况下，工厂缓存策略指定为[ModuleType](moduletype-enumeration.md)时创建的模板参数[模块](module-class.md)对象。 若要重写此策略，指定**FactoryCacheFlags**时创建一个工厂对象的值。

|||
|-|-|
|`FactoryCacheDefault`|将使用 `Module` 对象的缓存策略。|
|`FactoryCacheEnabled`|启用工厂缓存，无论用于创建 `ModuleType` 对象的 `Module` 模板参数如何都是如此。|
|`FactoryCacheDisabled`|禁用工厂缓存，无论用于创建 `ModuleType` 对象的 `Module` 模板参数如何都是如此。|

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)