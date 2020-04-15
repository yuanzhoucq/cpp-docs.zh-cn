---
title: SyncLockWithStatusT 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 77bcb8336e4650de7ed01a067fa1bdd7ec0ba3e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374268"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>参数

*同步特征*<br/>
可以获取资源的独占或共享所有权的类型。

## <a name="remarks"></a>备注

表示可以获取资源的独占或共享所有权的类型。

该`SyncLockWithStatusT`类用于实现[Mutex](mutex-class.md)和[信号量](semaphore-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                             | 说明
---------------------------------------------------------------- | --------------------------------------------------------------
[与状态同步锁定：：与状态同步锁定](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="protected-constructors"></a>受保护的构造函数

名称                                                             | 说明
---------------------------------------------------------------- | --------------------------------------------------------------
[与状态同步锁定：：与状态同步锁定](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                         | 说明
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[与状态同步锁定：：获取状态](#getstatus) | 检索当前`SyncLockWithStatusT`对象的等待状态。
[与状态同步锁定：：已锁定](#islocked)   | 指示当前对象是否`SyncLockWithStatusT`拥有资源;如果当前对象是否拥有资源，则表明当前对象是否拥有资源。也就是说，`SyncLockWithStatusT`对象已*锁定*。

### <a name="protected-data-members"></a>受保护的数据成员

名称                                    | 说明
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[与状态同步锁定：：status_](#status) | 保存基于当前`SyncLockWithStatusT`对象的锁定操作后基础等待操作的结果。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：:D

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>与状态同步锁定：：获取状态

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>返回值

基于`SyncLockWithStatusT`类的对象（如[Mutex](mutex-class.md)或[Semaphore）](semaphore-class.md)的等待操作的结果。 零 （0） 表示等待操作返回了信号状态;否则，则发生另一种状态，例如已经过的超时值。

### <a name="remarks"></a>备注

检索当前`SyncLockWithStatusT`对象的等待状态。

GetStatus（） 函数检索基础[status_](#status)数据成员的值。 当基于`SyncLockWithStatusT`类的对象执行锁定操作时，该对象首先等待该对象变为可用。 等待操作的结果存储在数据成员中`status_`。 `status_`数据成员的可能值是等待操作的返回值。 有关详细信息，请参阅 MSDN 库中`WaitForSingleObjectEx()`函数的返回值。

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>与状态同步锁定：：已锁定

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>备注

指示当前对象是否`SyncLockWithStatusT`拥有资源;如果当前对象是否拥有资源，则表明当前对象是否拥有资源。也就是说，`SyncLockWithStatusT`对象已*锁定*。

### <a name="return-value"></a>返回值

如果对象已`SyncLockWithStatusT`锁定，**则为 true;** 否则，**假**。

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>与状态同步锁定：：status_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD status_;
```

### <a name="remarks"></a>备注

保存基于当前`SyncLockWithStatusT`对象的锁定操作后基础等待操作的结果。

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>与状态同步锁定：：与状态同步锁定

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>参数

*其他*<br/>
对另一个`SyncLockWithStatusT`对象的 rvalue 引用。

*sync*<br/>
对另一个`SyncLockWithStatusT`对象的引用。

*状态*<br/>
*另*一个参数或*同步*参数的数据成员[status_](#status)的值。

### <a name="remarks"></a>备注

初始化 `SyncLockWithStatusT` 类的新实例。

第一个构造函数从参数*其他*指定的`SyncLockWithStatusT`另一个`SyncLockWithStatusT`初始化当前对象，然后使另一个`SyncLockWithStatusT`对象无效。 第二个构造函数`protected`是 ，并将当前`SyncLockWithStatusT`对象初始化为无效状态。
