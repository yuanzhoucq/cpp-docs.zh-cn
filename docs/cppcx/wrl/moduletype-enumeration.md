---
title: ModuleType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 3c7486cbc761975dd133f229f23dcf0b70e7e3ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403225"
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