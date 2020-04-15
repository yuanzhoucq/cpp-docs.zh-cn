---
title: Mutex 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: 36466bd00c5b100f20ee87173e68fdef4131ec23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371238"
---
# <a name="mutex-class"></a>Mutex 类

表示完全控制共享资源的同步对象。

## <a name="syntax"></a>语法

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称       | 说明
---------- | ------------------------------------------------------
`SyncLock` | 支持同步锁的类的同义词。

### <a name="public-constructor"></a>公共构造函数

名称                   | 说明
---------------------- | ------------------------------------------------
[穆顶：：Mutex](#mutex) | 初始化 `Mutex` 类的新实例。

### <a name="public-members"></a>公共成员

名称                 | 说明
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[静音：：锁定](#lock) | 等待，直到当前对象或与指定句柄关联的`Mutex`对象释放互斥体或指定的超时间隔已过。

### <a name="public-operator"></a>公共运营商

名称                                 | 说明
------------------------------------ | ---------------------------------------------------------------------------
[互斥：：运算符*](#operator-assign) | 将指定`Mutex`对象分配给（移动）到当前`Mutex`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Mutex`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="mutexlock"></a><a name="lock"></a>静音：：锁定

等待，直到当前对象或与指定句柄关联的`Mutex`对象释放互斥体或指定的超时间隔已过。

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
`Mutex`对象的句柄。

### <a name="return-value"></a>返回值

## <a name="mutexmutex"></a><a name="mutex"></a>穆顶：：Mutex

初始化 `Mutex` 类的新实例。

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>参数

*H*<br/>
对`Mutex`对象的句柄或句柄的 rvalue 引用。

### <a name="remarks"></a>备注

第一个构造函数从指定的句柄`Mutex`初始化对象。 第二个构造函数从指定的句柄`Mutex`初始化对象，然后将互斥体的所有权移动到当前`Mutex`对象。

## <a name="mutexoperator"></a><a name="operator-assign"></a>互斥：：运算符*

将指定`Mutex`对象分配给（移动）到当前`Mutex`对象。

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>参数

*H*<br/>
对`Mutex`对象的 rvalue 引用。

### <a name="return-value"></a>返回值

对当前`Mutex`对象的引用。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Rvalue 参考声明器： &&](../../cpp/rvalue-reference-declarator-amp-amp.md)的**移动语义**部分。
