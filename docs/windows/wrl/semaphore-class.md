---
title: Semaphore 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: 10357bb1cd46a33a8d4090c1ccc30050584d1816
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335783"
---
# <a name="semaphore-class"></a>Semaphore 类

表示控制可支持有限数量用户的共享资源的同步对象。

## <a name="syntax"></a>语法

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称       | 描述
---------- | ------------------------------------------------------
`SyncLock` | 类支持同步锁的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                               | 描述
---------------------------------- | ----------------------------------------------------
[Semaphore::Semaphore](#semaphore) | 初始化 `Semaphore` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                     | 描述
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore::Lock](#lock) | 将等待，直到当前的对象或与指定句柄关联的对象处于已发出信号状态或指定的超时间隔已过。

### <a name="public-operators"></a>公共运算符

名称                                     | 描述
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore::operator=](#operator-assign) | 将从指定句柄`Semaphore`对象与当前`Semaphore`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Semaphore`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="lock"></a>Semaphore:: lock

等到当前对象，或`Semaphore`对象与指定句柄处于已发出信号状态或指定的超时间隔已过。

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>参数

*milliseconds*<br/>
超时间隔（以毫秒为单位）。 默认值为 INFINITE，其表示将无限期地等待。

*h*<br/>
句柄`Semaphore`对象。

### <a name="return-value"></a>返回值

一个 `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="operator-assign"></a>Semaphore:: operator =

将从指定句柄`Semaphore`对象与当前`Semaphore`对象。

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
对右值引用`Semaphore`对象。

### <a name="return-value"></a>返回值

对当前的引用`Semaphore`对象。

## <a name="semaphore"></a>Semaphore:: semaphore

初始化 `Semaphore` 类的新实例。

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
句柄或对右值引用`Semaphore`对象。
