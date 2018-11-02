---
title: CriticalSection 类
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: dd34206741ba8fee8b283e22b6e8eefb3b3efb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651147"
---
# <a name="criticalsection-class"></a>CriticalSection 类

表示关键部分对象。

## <a name="syntax"></a>语法

```cpp
class CriticalSection;
```

## <a name="members"></a>成员

### <a name="constructor"></a>构造函数

name                                                        | 描述
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Criticalsection:: Criticalsection](#criticalsection)        | 初始化类似 mutex 对象、但只能由单一进程的线程使用的同步对象。
[CriticalSection:: ~ CriticalSection](#tilde-criticalsection) | 取消初始化和销毁当前`CriticalSection`对象。

### <a name="public-methods"></a>公共方法

名称                                 | 描述
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[Criticalsection:: Isvalid](#isvalid) | 指示当前的临界部分是否有效。
[Criticalsection:: Lock](#lock)       | 等待指定关键部分对象的所有权。 此函数将在授予调用线程所有权时返回。
[Criticalsection:: Trylock](#trylock) | 尝试进入关键节而不会阻塞。 如果调用成功，调用线程将取得所有权的关键部分。

### <a name="protected-data-members"></a>受保护的数据成员

name                        | 描述
--------------------------- | ----------------------------------------
[Criticalsection:: Cs_](#cs) | 声明关键部分数据成员。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CriticalSection`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="tilde-criticalsection"></a>CriticalSection:: ~ CriticalSection

取消初始化和销毁当前`CriticalSection`对象。

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsection"></a>Criticalsection:: Criticalsection

初始化类似 mutex 对象、但只能由单一进程的线程使用的同步对象。

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>参数

*spincount*<br/>
关键部分对象的旋转计数。 默认值为 0。

### <a name="remarks"></a>备注

有关关键部分和旋转计数的详细信息，请参阅`InitializeCriticalSectionAndSpinCount`函数，在`Synchronization`部分 Windows API 文档。

## <a name="cs"></a>Criticalsection:: Cs_

声明关键部分数据成员。

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>备注

此数据成员受保护。

## <a name="isvalid"></a>Criticalsection:: Isvalid

指示当前的临界部分是否有效。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>返回值

默认情况下始终返回 **，则返回 true**。

## <a name="lock"></a>Criticalsection:: Lock

等待指定关键部分对象的所有权。 此函数将在授予调用线程所有权时返回。

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>参数

*cs*<br/>
用户指定的关键部分对象。

### <a name="return-value"></a>返回值

可用于取消锁定当前关键部分的锁定对象。

### <a name="remarks"></a>备注

第一个 `Lock` 函数影响当前关键部分对象。 第二个 `Lock` 函数影响用户指定的关键部分。

## <a name="trylock"></a>Criticalsection:: Trylock

尝试进入关键节而不会阻塞。 如果调用成功，调用线程将取得所有权的关键部分。

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>参数

*cs*<br/>
用户指定的关键部分对象。

### <a name="return-value"></a>返回值

如果成功进入关键节一个非零值或当前线程已拥有关键部分。 如果另一个线程已拥有关键部分，则为零。

### <a name="remarks"></a>备注

第一个 `TryLock` 函数影响当前关键部分对象。 第二个 `TryLock` 函数影响用户指定的关键部分。
