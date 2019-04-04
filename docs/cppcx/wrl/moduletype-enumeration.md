---
title: ModuleType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 937649eada481f7c45359fa0816266f62dc03875
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784150"
---
# <a name="moduletype-enumeration"></a>ModuleType 枚举

指定模块是否应支持进程内服务器或进程外服务器。

## <a name="syntax"></a>语法

```cpp
enum ModuleType;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|描述|
|----------|-----------------|
|`InProc`|进程内服务器。|
|`OutOfProc`|进程外服务器。|
|`DisableCaching`|禁用模块上的缓存机制。|
|`InProcDisableCaching`|组合`InProc`和`DisableCaching`。|
|`OutOfProcDisableCaching`|组合`OutOfProc`和`DisableCaching`。|

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)