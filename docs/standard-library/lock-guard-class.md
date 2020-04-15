---
title: lock_guard 类
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 989c1e368e95fc0009f0c3f1c71af0bdba20609d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351720"
---
# <a name="lock_guard-class"></a>lock_guard 类

表示可进行实例化以创建其析构函数解锁 `mutex` 的对象的模板。

## <a name="syntax"></a>语法

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>备注

模板参数 `Mutex` 必须命名为 mutex 类型**。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`lock_guard::mutex_type`|模板参数 `Mutex` 的同义词。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[lock_guard](#lock_guard)|构造 `lock_guard` 对象。|
|[lock_guard：lock_guard析构器](#dtorlock_guard_destructor)|解锁传递给构造函数的 `mutex`。|

## <a name="requirements"></a>要求

**标题：**\<互斥>

**命名空间:** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a>lock_guard：lock_guard构造函数

构造 `lock_guard` 对象。

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>参数

*Mtx*\
*互斥类型*对象。

### <a name="remarks"></a>备注

第一个构造函数构造类型`lock_guard`的对象并锁定*Mtx*。 如果*Mtx*不是递归互斥，则必须在调用此构造函数时将其解锁。

第二个构造函数不锁定*Mtx*。 调用此构造函数时必须锁定*Mtx。* 此构造函数不会引发异常。

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a>lock_guard：lock_guard析构器

解锁传递给构造函数的 `mutex`。

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>备注

如果析构函数运行时 `mutex` 不存在，则该行为不确定。

## <a name="see-also"></a>另请参阅

[标题文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<互斥>](../standard-library/mutex.md)
