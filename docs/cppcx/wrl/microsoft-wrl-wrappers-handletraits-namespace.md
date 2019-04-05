---
title: Microsoft::WRL::Wrappers::HandleTraits 命名空间
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: 6ed8156b6a0e71d40d1579fc9a33912f698e1773
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030380"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits 命名空间

介绍了常见的基于句柄的资源类型的特征。

## <a name="syntax"></a>语法

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>成员

### <a name="structures"></a>结构

|名称|描述|
|----------|-----------------|
|[CriticalSectionTraits 结构](criticalsectiontraits-structure.md)|专门负责`CriticalSection`对象以支持无效的关键部分或函数，以释放关键节。|
|[EventTraits 结构](eventtraits-structure.md)|定义特征`Event`类句柄。|
|[FileHandleTraits 结构](filehandletraits-structure.md)|定义的文件句柄的特征。|
|[HANDLENullTraits 结构](handlenulltraits-structure.md)|定义未初始化句柄的共同特征。|
|[HANDLETraits 结构](handletraits-structure.md)|定义句柄的共同特征。|
|[MutexTraits 结构](mutextraits-structure.md)|定义常见特征[互斥体](mutex-class.md)类。|
|[SemaphoreTraits 结构](semaphoretraits-structure.md)|定义信号量对象的共同特征。|
|[SRWLockExclusiveTraits 结构](srwlockexclusivetraits-structure.md)|描述的常见特征`SRWLock`中排他锁模式的类。|
|[SRWLockSharedTraits 结构](srwlocksharedtraits-structure.md)|描述的常见特征`SRWLock`中共享锁模式的类。|

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](microsoft-wrl-wrappers-namespace.md)