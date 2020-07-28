---
title: SyncLockT 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 6a6e176020624f02e778ba5684a374abfbafa9e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184665"
---
# <a name="synclockt-class"></a>SyncLockT 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>参数

*SyncTraits*<br/>
可以取得资源所有权的类型。

## <a name="remarks"></a>备注

表示一个类型，该类型可以采用资源的独占或共享所有权。

`SyncLockT`例如，使用类来帮助实现[SRWLock](srwlock-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                      | 描述
----------------------------------------- | ----------------------------------------------------
[SyncLockT：： SyncLockT](#synclockt)        | 初始化 `SyncLockT` 类的新实例。
[SyncLockT：： ~ SyncLockT](#tilde-synclockt) | 取消初始化类的实例 `SyncLockT` 。

### <a name="protected-constructors"></a>受保护的构造函数

名称                               | 描述
---------------------------------- | ----------------------------------------------------
[SyncLockT：： SyncLockT](#synclockt) | 初始化 `SyncLockT` 类的新实例。

### <a name="public-methods"></a>公共方法

“属性”                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT：： IsLocked](#islocked) | 指示当前对象是否 `SyncLockT` 拥有资源; 即， `SyncLockT` 对象已*锁定*。
[SyncLockT：： Unlock](#unlock)     | 释放由当前对象保存的资源 `SyncLockT` （如果有）。

### <a name="protected-data-members"></a>受保护的数据成员

名称                      | 描述
------------------------- | -------------------------------------------------------------------
[SyncLockT：： sync_](#sync) | 保存由类表示的基础资源 `SyncLockT` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SyncLockT`

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装：:D etails

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLockT：： ~ SyncLockT

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~SyncLockT();
```

### <a name="remarks"></a>备注

取消初始化类的实例 `SyncLockT` 。

此析构函数也会解锁当前 `SyncLockT` 实例。

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLockT：： IsLocked

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果 `SyncLockT` 对象被锁定，则为; 否则为 **`false`** 。

### <a name="remarks"></a>备注

指示当前对象是否 `SyncLockT` 拥有资源; 即， `SyncLockT` 对象已*锁定*。

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLockT：： sync_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>备注

保存由类表示的基础资源 `SyncLockT` 。

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLockT：： SyncLockT

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>参数

*以外*<br/>
对另一对象的 rvalue 引用 `SyncLockT` 。

*同步*<br/>
对另一对象的引用 `SyncLockWithStatusT` 。

### <a name="remarks"></a>备注

初始化 `SyncLockT` 类的新实例。

第一个构造函数 `SyncLockT` 从另一个 `SyncLockT` 由参数指定的对象初始化*other*当前对象，然后使另一个 `SyncLockT` 对象失效。 第二个构造函数为 **`protected`** ，并将当前 `SyncLockT` 对象初始化为无效状态。

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLockT：： Unlock

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void Unlock();
```

### <a name="remarks"></a>备注

释放由当前对象保存的资源 `SyncLockT` （如果有）。
