---
title: recursive_mutex 类
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 448b4d03e4d38dc45621cddab7d8f5d03b805968
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451674"
---
# <a name="recursivemutex-class"></a>recursive_mutex 类

表示互斥体类型。 与 [mutex](../standard-library/mutex-class-stl.md) 类相反，为已锁定的对象调用锁定方法的行为是有明确定义的。

## <a name="syntax"></a>语法

```cpp
class recursive_mutex;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|构造 `recursive_mutex` 对象。|
|[~recursive_mutex 析构函数](#dtorrecursive_mutex_destructor)|释放由 `recursive_mutex` 对象使用的任何资源。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[lock](#lock)|阻止调用线程，直到线程获取 mutex 的所有权。|
|[try_lock](#try_lock)|在不阻止的情况下尝试获取 mutex 的所有权。|
|[unlock](#unlock)|释放 mutex 的所有权。|

## <a name="requirements"></a>要求

**标头:** \<mutex >

**命名空间：** std

## <a name="lock"></a>lock

阻止调用线程，直到线程获取 `mutex` 的所有权。

```cpp
void lock();
```

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该方法将立即返回，同时上一锁定保持有效。

## <a name="recursive_mutex"></a>recursive_mutex

构造未锁定的 `recursive_mutex` 对象。

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>~recursive_mutex

释放由该对象使用的所有资源。

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>备注

如果当析构函数运行时对象被锁定，则该行为不确定。

## <a name="try_lock"></a>try_lock

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>返回值

如果方法成功获取的所有权, `mutex`则为 true; 如果调用线程已拥有, `mutex**; otherwise, **false`则**为 true** 。

### <a name="remarks"></a>备注

如果调用线程已拥有`mutex`, 则函数立即返回**true**, 而上一个锁仍有效。

## <a name="unlock"></a>unlock

释放 mutex 的所有权。

```cpp
void unlock();
```

### <a name="remarks"></a>备注

仅当 `mutex` 的调用次数与在 `recursive_mutex` 对象上成功调用 [lock](#lock) 和 [try_lock](#try_lock) 的次数一样多时，此方法才释放其所有权。

如果调用的线程不拥有 `mutex`，则该行为不确定。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
