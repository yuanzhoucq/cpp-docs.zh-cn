---
title: lock_guard 类
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 45a01c5fdd431bcfad1eeb5ab0531c11c89e9767
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645544"
---
# <a name="lockguard-class"></a>lock_guard 类

表示可进行实例化以创建其析构函数解锁 `mutex` 的对象的模板。

## <a name="syntax"></a>语法

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>备注

模板参数 `Mutex` 必须命名为 mutex 类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`lock_guard::mutex_type`|模板参数 `Mutex` 的同义词。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[lock_guard](#lock_guard)|构造 `lock_guard` 对象。|
|[lock_guard::~lock_guard 析构函数](#dtorlock_guard_destructor)|解锁传递给构造函数的 `mutex`。|

## <a name="requirements"></a>要求

**标头：** \<互斥体 >

**命名空间：** std

## <a name="lock_guard"></a>lock_guard::lock_guard 构造函数

构造 `lock_guard` 对象。

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>参数

*使用 Mtx*<br/>
一个 mutex 类型对象。

### <a name="remarks"></a>备注

第一个构造函数将构造类型的对象`lock_guard`和锁*使用 Mtx*。 如果*使用 Mtx*不是递归互斥体，它必须在调用此构造函数时解锁。

第二个构造函数不会锁定*使用 Mtx*。 *使用 Mtx*时调用此构造函数，必须锁定。 此构造函数不会引发异常。

## <a name="dtorlock_guard_destructor"></a>lock_guard::~lock_guard 析构函数

解锁传递给构造函数的 `mutex`。

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>备注

如果析构函数运行时 `mutex` 不存在，则该行为不确定。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
