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
ms.openlocfilehash: 93de43ac7e5314501d0391e2cde862ba32be0b4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379137"
---
# <a name="mutex-class"></a>Mutex 类

表示完全控制共享资源的同步对象。

## <a name="syntax"></a>语法

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称       | 描述
---------- | ------------------------------------------------------
`SyncLock` | 类支持同步锁的同义词。

### <a name="public-constructor"></a>公共构造函数

名称                   | 描述
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | 初始化 `Mutex` 类的新实例。

### <a name="public-members"></a>公共成员

名称                 | 描述
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Lock](#lock) | 等到当前对象，或`Mutex`与指定句柄，互斥体或指定的超时间隔已过的版本关联的对象。

### <a name="public-operator"></a>公共运算符

名称                                 | 描述
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operator=](#operator-assign) | 分配 （移动） 指定`Mutex`对象与当前`Mutex`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Mutex`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="lock"></a>Mutex::Lock

等到当前对象，或`Mutex`与指定句柄，互斥体或指定的超时间隔已过的版本关联的对象。

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
句柄`Mutex`对象。

### <a name="return-value"></a>返回值

## <a name="mutex"></a>Mutex::Mutex

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

*h*<br/>
句柄或对句柄的右值引用到`Mutex`对象。

### <a name="remarks"></a>备注

第一个构造函数初始化`Mutex`从指定句柄的对象。 第二个构造函数初始化`Mutex`从指定句柄，然后将 mutex 的所有权的对象与当前`Mutex`对象。

## <a name="operator-assign"></a>Mutex:: operator =

分配 （移动） 指定`Mutex`对象与当前`Mutex`对象。

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
对的右值引用`Mutex`对象。

### <a name="return-value"></a>返回值

对当前的引用`Mutex`对象。

### <a name="remarks"></a>备注

有关详细信息，请参阅**移动语义**一部分[右值引用声明符： & &](../../cpp/rvalue-reference-declarator-amp-amp.md)。
