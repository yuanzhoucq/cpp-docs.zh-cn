---
title: Microsoft::WRL::Wrappers 命名空间
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 4b88ad0da31321a696c1238f1c9838d3b3a1c927
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391993"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers 命名空间

定义简化对象、字符串和句柄的生存期管理的“获取资源即初始化”(RAII) 包装器类型。

## <a name="syntax"></a>语法

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>成员

### <a name="typedefs"></a>Typedef

|名称|描述|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>类

|名称|描述|
|----------|-----------------|
|[CriticalSection 类](criticalsection-class.md)|表示关键部分对象。|
|[Event 类 (WRL)](event-class-wrl.md)|表示一个事件。|
|[HandleT 类](handlet-class.md)|表示对象的句柄。|
|[HString 类](hstring-class.md)|为处理 HSTRING 句柄提供支持。|
|[HStringReference 类](hstringreference-class.md)|表示从现有字符串创建的 HSTRING。|
|[Mutex 类](mutex-class.md)|表示完全控制共享资源的同步对象。|
|[RoInitializeWrapper 类](roinitializewrapper-class.md)|初始化 Windows 运行时。|
|[Semaphore 类](semaphore-class.md)|表示控制可支持有限数量用户的共享资源的同步对象。|
|[SRWLock 类](srwlock-class.md)|表示精简读取器/编写器锁定。|

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)