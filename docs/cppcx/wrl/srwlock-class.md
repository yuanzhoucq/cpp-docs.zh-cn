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
ms.openlocfilehash: 079f1abe652d8c1610a084f5e1158cc5798d61c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498297"
---
# <a name="srwlock-class"></a>SRWLock 类

表示精简读取器/编写器锁定。

## <a name="syntax"></a>语法

```cpp
class SRWLock;
```

## <a name="remarks"></a>备注

超薄读取器/写入器锁用于同步跨线程对对象或资源的访问。 有关详细信息, 请参阅[同步函数](/windows/win32/Sync/synchronization-functions)。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

name                | 描述
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | 以独占模式获取的对象的同义词。`SRWLock`
`SyncLockShared`    | 在共享模式下获取的对象的同义词。`SRWLock`

### <a name="public-constructors"></a>公共构造函数

名称                                     | 描述
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | 初始化 `SRWLock` 类的新实例。
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | 取消初始化`SRWLock`类的实例。

### <a name="public-methods"></a>公共方法

名称                                           | 描述
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | 获取独占`SRWLock`模式下的对象。
[SRWLock::LockShared](#lockshared)             | 获取共享`SRWLock`模式下的对象。
[SRWLock::TryLockExclusive](#trylockexclusive) | 尝试以独占模式`SRWLock`获取当前或指定`SRWLock`对象的对象。
[SRWLock::TryLockShared](#trylockshared)       | 尝试为当前或`SRWLock`指定`SRWLock`的对象获取共享模式下的对象。

### <a name="protected-data-member"></a>受保护的数据成员

name                                      | 描述
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | 包含当前`SRWLock`对象的基础锁变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLock`

## <a name="requirements"></a>要求

**标头:** corewrappers。h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

取消初始化`SRWLock`类的实例。

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

获取独占`SRWLock`模式下的对象。

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
指向`SRWLock`对象的指针。

### <a name="return-value"></a>返回值

独占`SRWLock`模式下的对象。

## <a name="lockshared"></a>SRWLock::LockShared

获取共享`SRWLock`模式下的对象。

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
指向`SRWLock`对象的指针。

### <a name="return-value"></a>返回值

处于`SRWLock`共享模式的对象。

## <a name="srwlock-constructor"></a>SRWLock:: SRWLock

初始化 `SRWLock` 类的新实例。

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

包含当前`SRWLock`对象的基础锁变量。

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

尝试以独占模式`SRWLock`获取当前或指定`SRWLock`对象的对象。 如果调用成功, 则调用线程获取锁的所有权。

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
指向`SRWLock`对象的指针。

### <a name="return-value"></a>返回值

如果成功, `SRWLock`则处于独占模式的对象和调用线程取得锁的所有权。 否则为其`SRWLock`状态无效的对象。

## <a name="trylockshared"></a>SRWLock::TryLockShared

尝试为当前或`SRWLock`指定`SRWLock`的对象获取共享模式下的对象。

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
指向`SRWLock`对象的指针。

### <a name="return-value"></a>返回值

如果成功, `SRWLock`则处于共享模式的对象和调用线程取得锁的所有权。 否则为其`SRWLock`状态无效的对象。
