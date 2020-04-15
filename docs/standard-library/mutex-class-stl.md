---
title: mutex 类（C++ 标准库）| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 84e6e3a46903a204444df9886556ae2c563304a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364847"
---
# <a name="mutex-class-c-standard-library"></a>mutex 类（C++ 标准库）

表示互斥体类型**。 此类型的对象可用于强制程序内的互斥。

## <a name="syntax"></a>语法

```cpp
class mutex;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[互斥](#mutex)|构造 `mutex` 对象。|
|[mutex::~mutex 析构函数](#dtormutex_destructor)|释放由 `mutex` 对象使用的任何资源。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[锁](#lock)|阻止调用线程，直到线程获取 `mutex` 的所有权。|
|[native_handle](#native_handle)|返回表示 mutex 句柄的特定于实现的类型。|
|[try_lock](#try_lock)|在不阻止的情况下尝试获取 `mutex` 的所有权。|
|[解 锁](#unlock)|释放 `mutex` 的所有权。|

## <a name="requirements"></a>要求

**标题：**\<互斥>

**命名空间:** std

## <a name="mutexlock"></a><a name="lock"></a>互斥：：锁定

阻止调用线程，直到线程获取 `mutex` 的所有权。

```cpp
void lock();
```

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该行为不确定。

## <a name="mutexmutex-constructor"></a><a name="mutex"></a>互斥：：互斥构造函数

构造未锁定的 `mutex` 对象。

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a>互斥：：=多斥析构函数

释放由 `mutex` 对象使用的任何资源。

```cpp
~mutex();
```

### <a name="remarks"></a>备注

如果当析构函数运行时对象被锁定，则该行为不确定。

## <a name="mutexnative_handle"></a><a name="native_handle"></a>互斥：：native_handle

返回表示 mutex 句柄的特定于实现的类型。 可以特定于实现的方式使用互斥体句柄。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>返回值

`native_handle_type` 定义为 `Concurrency::critical_section *`，其强制转换为 `void *`。

## <a name="mutextry_lock"></a><a name="try_lock"></a>互斥：：try_lock

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
bool try_lock();
```

### <a name="return-value"></a>返回值

**如果**该方法成功获得 的所有权， `mutex`否则，**假**。

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该行为不确定。

## <a name="mutexunlock"></a><a name="unlock"></a>互斥：：解锁

释放 `mutex` 的所有权。

```cpp
void unlock();
```

### <a name="remarks"></a>备注

如果调用的线程不拥有 `mutex`，则该行为不确定。

## <a name="see-also"></a>另请参阅

[标题文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<互斥>](../standard-library/mutex.md)
