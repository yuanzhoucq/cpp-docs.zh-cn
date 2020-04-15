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
ms.openlocfilehash: 5deb89e795d1886ca316886ae1ea260ce1f36fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372590"
---
# <a name="criticalsection-class"></a>CriticalSection 类

表示关键部分对象。

## <a name="syntax"></a>语法

```cpp
class CriticalSection;
```

## <a name="members"></a>成员

### <a name="constructor"></a>构造函数

名称                                                        | 说明
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[关键部分：：关键部分](#criticalsection)        | 初始化类似 mutex 对象、但只能由单一进程的线程使用的同步对象。
[关键部分：：*关键部分](#tilde-criticalsection) | 取消初始化和销毁当前`CriticalSection`对象。

### <a name="public-methods"></a>公共方法

名称                                 | 说明
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[关键部分：：有效](#isvalid) | 指示当前的临界部分是否有效。
[关键部分：锁定](#lock)       | 等待指定关键部分对象的所有权。 此函数将在授予调用线程所有权时返回。
[关键部分：：尝试锁定](#trylock) | 尝试在不阻塞的情况下进入关键部分。 如果调用成功，则调用线程将接管关键部分的所有权。

### <a name="protected-data-members"></a>受保护的数据成员

名称                        | 说明
--------------------------- | ----------------------------------------
[关键部分：：cs_](#cs) | 声明关键部分数据成员。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CriticalSection`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>关键部分：：*关键部分

取消初始化和销毁当前`CriticalSection`对象。

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>关键部分：：关键部分

初始化类似 mutex 对象、但只能由单一进程的线程使用的同步对象。

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>参数

*旋转计数*<br/>
关键部分对象的旋转计数。 默认值为 0。

### <a name="remarks"></a>备注

有关关键部分和自旋计数的详细信息，请参阅 Windows `InitializeCriticalSectionAndSpinCount` API`Synchronization`操作版部分中的函数。

## <a name="criticalsectioncs_"></a><a name="cs"></a>关键部分：：cs_

声明关键部分数据成员。

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>备注

此数据成员受保护。

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>关键部分：：有效

指示当前的临界部分是否有效。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>返回值

默认情况下，始终返回**true**。

## <a name="criticalsectionlock"></a><a name="lock"></a>关键部分：锁定

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

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>关键部分：：尝试锁定

尝试在不阻塞的情况下进入关键部分。 如果调用成功，则调用线程将接管关键部分的所有权。

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

如果成功输入关键节或当前线程已拥有关键节，则为非零值。 如果另一个线程已拥有关键部分，则为零。

### <a name="remarks"></a>备注

第一个 `TryLock` 函数影响当前关键部分对象。 第二个 `TryLock` 函数影响用户指定的关键部分。
