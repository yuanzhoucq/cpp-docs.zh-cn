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
ms.openlocfilehash: 52c4404fa28f680a9a7a4592d03f535e8406d1a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374285"
---
# <a name="synclockt-class"></a>SyncLockT 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>参数

*同步特征*<br/>
可以取得资源所有权的类型。

## <a name="remarks"></a>备注

表示可以获取资源的独占或共享所有权的类型。

例如`SyncLockT`，该类用于帮助实现[SRWLock](srwlock-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                      | 说明
----------------------------------------- | ----------------------------------------------------
[同步锁定T：同步锁定](#synclockt)        | 初始化 `SyncLockT` 类的新实例。
[同步锁定T：*同步锁定](#tilde-synclockt) | 取消初始化类的`SyncLockT`实例。

### <a name="protected-constructors"></a>受保护的构造函数

名称                               | 说明
---------------------------------- | ----------------------------------------------------
[同步锁定T：同步锁定](#synclockt) | 初始化 `SyncLockT` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                             | 说明
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[同步锁定T：锁定](#islocked) | 指示当前对象是否`SyncLockT`拥有资源;如果当前对象是否拥有资源，则表明当前对象是否拥有资源。也就是说，`SyncLockT`对象已*锁定*。
[同步锁定T：解锁](#unlock)     | 释放对当前`SyncLockT`对象（如果有）持有的资源的控制。

### <a name="protected-data-members"></a>受保护的数据成员

名称                      | 说明
------------------------- | -------------------------------------------------------------------
[同步锁定T：sync_](#sync) | 保存类`SyncLockT`表示的基础资源。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SyncLockT`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：:D

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>同步锁定T：*同步锁定

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~SyncLockT();
```

### <a name="remarks"></a>备注

取消初始化类的`SyncLockT`实例。

此析构函数还会解锁当前`SyncLockT`实例。

## <a name="synclocktislocked"></a><a name="islocked"></a>同步锁定T：锁定

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>返回值

如果对象已`SyncLockT`锁定，**则为 true;** 否则，**假**。

### <a name="remarks"></a>备注

指示当前对象是否`SyncLockT`拥有资源;如果当前对象是否拥有资源，则表明当前对象是否拥有资源。也就是说，`SyncLockT`对象已*锁定*。

## <a name="synclocktsync_"></a><a name="sync"></a>同步锁定T：sync_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>备注

保存类`SyncLockT`表示的基础资源。

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>同步锁定T：同步锁定

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

*其他*<br/>
对另一个`SyncLockT`对象的 rvalue 引用。

*sync*<br/>
对另一个`SyncLockWithStatusT`对象的引用。

### <a name="remarks"></a>备注

初始化 `SyncLockT` 类的新实例。

第一个构造函数从参数*其他*指定的`SyncLockT`另一`SyncLockT`个对象初始化当前对象，然后使另一个`SyncLockT`对象无效。 第二个构造函数`protected`是 ，并将当前`SyncLockT`对象初始化为无效状态。

## <a name="synclocktunlock"></a><a name="unlock"></a>同步锁定T：解锁

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void Unlock();
```

### <a name="remarks"></a>备注

释放对当前`SyncLockT`对象（如果有）持有的资源的控制。
