---
title: SRWLock 类
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: e305ad54e30455ce7c25f356c454791da0783591
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377266"
---
# <a name="srwlock-class"></a>SRWLock 类

表示精简读取器/编写器锁定。

## <a name="syntax"></a>语法

```cpp
class SRWLock;
```

## <a name="remarks"></a>备注

超薄读取器/写入器锁用于将线程之间的访问同步到对象或资源。 有关详细信息，请参阅[同步函数](/windows/win32/Sync/synchronization-functions)。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称                | 说明
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | 在独占模式下获取`SRWLock`的对象的同义词。
`SyncLockShared`    | 在共享模式下获取`SRWLock`的对象的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                                     | 说明
---------------------------------------- | --------------------------------------------------
[SRWLock：SRWLock](#srwlock-constructor) | 初始化 `SRWLock` 类的新实例。
[SRWLock：*SRWLock](#tilde-srwlock)      | 取消初始化类的`SRWLock`实例。

### <a name="public-methods"></a>公共方法

名称                                           | 说明
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock：锁独家](#lockexclusive)       | 在独占`SRWLock`模式下获取对象。
[SRWLock：锁定共享](#lockshared)             | 在共享模式下`SRWLock`获取对象。
[SRWLock：尝试锁定独家](#trylockexclusive) | 尝试以独占`SRWLock`模式获取当前或指定`SRWLock`对象的对象。
[SRWLock：尝试锁定共享](#trylockshared)       | 尝试在共享模式下`SRWLock`获取当前或指定`SRWLock`对象的对象。

### <a name="protected-data-member"></a>受保护的数据成员

名称                                      | 说明
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock：SRWLock_](#srwlock-data-member) | 包含当前`SRWLock`对象的基础锁定变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLock`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a>SRWLock：*SRWLock

取消初始化类的`SRWLock`实例。

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a>SRWLock：锁独家

在独占`SRWLock`模式下获取对象。

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*锁*<br/>
指向对象的指针`SRWLock`。

### <a name="return-value"></a>返回值

独`SRWLock`占模式下的对象。

## <a name="srwlocklockshared"></a><a name="lockshared"></a>SRWLock：锁定共享

在共享模式下`SRWLock`获取对象。

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*锁*<br/>
指向对象的指针`SRWLock`。

### <a name="return-value"></a>返回值

共享`SRWLock`模式下的对象。

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a>SRWLock：SRWLock

初始化 `SRWLock` 类的新实例。

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a>SRWLock：SRWLock_

包含当前`SRWLock`对象的基础锁定变量。

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a>SRWLock：尝试锁定独家

尝试以独占`SRWLock`模式获取当前或指定`SRWLock`对象的对象。 如果调用成功，则调用线程将接管锁的所有权。

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*锁*<br/>
指向对象的指针`SRWLock`。

### <a name="return-value"></a>返回值

如果成功，则`SRWLock`独占模式下的对象和调用线程将获取锁的所有权。 否则，`SRWLock`其状态无效的对象。

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a>SRWLock：尝试锁定共享

尝试在共享模式下`SRWLock`获取当前或指定`SRWLock`对象的对象。

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*锁*<br/>
指向对象的指针`SRWLock`。

### <a name="return-value"></a>返回值

如果成功，共享`SRWLock`模式下的对象和调用线程将获取锁的所有权。 否则，`SRWLock`其状态无效的对象。
