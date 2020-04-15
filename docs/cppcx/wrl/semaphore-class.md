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
ms.openlocfilehash: e017b1b6316c4b6d49563d9a543950ab28961d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359360"
---
# <a name="semaphore-class"></a>Semaphore 类

表示控制可支持有限数量用户的共享资源的同步对象。

## <a name="syntax"></a>语法

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称       | 说明
---------- | ------------------------------------------------------
`SyncLock` | 支持同步锁的类的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                               | 说明
---------------------------------- | ----------------------------------------------------
[信号量：信号量：信号量](#semaphore) | 初始化 `Semaphore` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                     | 说明
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[信号量：锁](#lock) | 等待，直到当前对象或与指定句柄关联的对象处于信号状态或指定的超时间隔已过。

### <a name="public-operators"></a>公共运算符

名称                                     | 说明
---------------------------------------- | ---------------------------------------------------------------------------------------
[信号量：：运算符*](#operator-assign) | 将指定的句柄从`Semaphore`对象移动到当前`Semaphore`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Semaphore`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="semaphorelock"></a><a name="lock"></a>信号量：锁

等待，直到当前对象或与指定句柄关联的`Semaphore`对象处于信号状态或指定的超时间隔已过。

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

*毫秒*<br/>
超时间隔（以毫秒为单位）。 默认值为 INFINITE，其表示将无限期地等待。

*H*<br/>
`Semaphore`对象的句柄。

### <a name="return-value"></a>返回值

一个 `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>` 类型的值

## <a name="semaphoreoperator"></a><a name="operator-assign"></a>信号量：：运算符*

将指定的句柄从`Semaphore`对象移动到当前`Semaphore`对象。

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>参数

*H*<br/>
对`Semaphore`对象的 Rvalue 引用。

### <a name="return-value"></a>返回值

对当前`Semaphore`对象的引用。

## <a name="semaphoresemaphore"></a><a name="semaphore"></a>信号量：信号量：信号量

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

*H*<br/>
`Semaphore`对象的句柄或 rvalue 引用。
