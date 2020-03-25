---
title: ModuleType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 8425a15d594f7b8b30027d3576ee86015b656130
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213715"
---
# <a name="moduletype-enumeration"></a>ModuleType 枚举

指定模块是否应支持进程内服务器或进程外服务器。

## <a name="syntax"></a>语法

```cpp
enum ModuleType;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`InProc`|进程内服务器。|
|`OutOfProc`|进程外服务器。|
|`DisableCaching`|禁用模块上的缓存机制。|
|`InProcDisableCaching`|`InProc` 和 `DisableCaching`的组合。|
|`OutOfProcDisableCaching`|`OutOfProc` 和 `DisableCaching`的组合。|

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)
