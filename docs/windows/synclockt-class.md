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
ms.openlocfilehash: ae6ac25605d23a6c408afae355e6f4349cf0a4a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432358"
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
可以获得资源的所有权类型。

## <a name="remarks"></a>备注

表示可能需要排他的类型或共享资源的所有权。

`SyncLockT`类用于，例如，可以帮助实施[SRWLock](../windows/srwlock-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                      | 描述
----------------------------------------- | ----------------------------------------------------
[Synclockt:: Synclockt](#synclockt)        | 初始化 `SyncLockT` 类的新实例。
[SyncLockT:: ~ SyncLockT](#tilde-synclockt) | 取消初始化的实例`SyncLockT`类。

### <a name="protected-constructors"></a>受保护的构造函数

名称                               | 描述
---------------------------------- | ----------------------------------------------------
[Synclockt:: Synclockt](#synclockt) | 初始化 `SyncLockT` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[Synclockt:: Islocked](#islocked) | 指示是否当前`SyncLockT`对象拥有一个资源; 也就是，则`SyncLockT`对象是*锁定*。
[Synclockt:: Unlock](#unlock)     | 释放当前占用的资源的控制`SyncLockT`对象，如果有的话。

### <a name="protected-data-members"></a>受保护的数据成员

name                      | 描述
------------------------- | -------------------------------------------------------------------
[Synclockt:: Sync_](#sync) | 保存由表示的基础资源`SyncLockT`类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SyncLockT`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="tilde-synclockt"></a>SyncLockT:: ~ SyncLockT

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~SyncLockT();
```

### <a name="remarks"></a>备注

取消初始化的实例`SyncLockT`类。

此析构函数还能释放种种当前`SyncLockT`实例。

## <a name="islocked"></a>Synclockt:: Islocked

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>返回值

**true**如果`SyncLockT`对象是锁定; 否则为**false**。

### <a name="remarks"></a>备注

指示是否当前`SyncLockT`对象拥有一个资源; 也就是，则`SyncLockT`对象是*锁定*。

## <a name="sync"></a>Synclockt:: Sync_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>备注

保存由表示的基础资源`SyncLockT`类。

## <a name="synclockt"></a>Synclockt:: Synclockt

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

*other*<br/>
对另一个右值引用`SyncLockT`对象。

*sync*<br/>
对另一个引用`SyncLockWithStatusT`对象。

### <a name="remarks"></a>备注

初始化 `SyncLockT` 类的新实例。

第一个构造函数初始化当前`SyncLockT`从另一个对象`SyncLockT`参数指定的对象*其他*，然后使其他和`SyncLockT`对象。 第二个构造函数是`protected`，并初始化当前`SyncLockT`为无效状态的对象。

## <a name="unlock"></a>Synclockt:: Unlock

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void Unlock();
```

### <a name="remarks"></a>备注

释放当前占用的资源的控制`SyncLockT`对象，如果有的话。
