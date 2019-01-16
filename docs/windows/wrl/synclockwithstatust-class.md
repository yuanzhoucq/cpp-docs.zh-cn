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
ms.openlocfilehash: 1c9c0805834a59d10a559bfc2b6da0f10e2fe160
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335567"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>参数

*SyncTraits*<br/>
可能需要排他的类型或共享资源的所有权。

## <a name="remarks"></a>备注

表示可能需要排他的类型或共享资源的所有权。

`SyncLockWithStatusT`类用于实现[Mutex](mutex-class.md)并[信号量](semaphore-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="protected-constructors"></a>受保护的构造函数

名称                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | 检索当前的等待状态`SyncLockWithStatusT`对象。
[SyncLockWithStatusT::IsLocked](#islocked)   | 指示是否当前`SyncLockWithStatusT`对象拥有一个资源; 也就是，则`SyncLockWithStatusT`对象是*锁定*。

### <a name="protected-data-members"></a>受保护的数据成员

name                                    | 描述
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | 保存后对象的锁操作取决于当前的基础的等待操作结果`SyncLockWithStatusT`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>SyncLockWithStatusT::GetStatus

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>返回值

基于对象的等待操作结果`SyncLockWithStatusT`类，如[Mutex](mutex-class.md)或[信号量](semaphore-class.md)。 零 (0) 指示等待操作返回已发出信号的状态;否则，另一种状态发生，如已用超时值。

### <a name="remarks"></a>备注

检索当前的等待状态`SyncLockWithStatusT`对象。

GetStatus() 函数用于检索基础[status_](#status)数据成员。 当对象基于`SyncLockWithStatusT`类执行锁定操作，该对象将会先等待对象变得可用。 这一等待操作的结果存储在`status_`数据成员。 可能值`status_`数据成员是等待操作的返回值。 有关详细信息，请参阅的返回值`WaitForSingleObjectEx()`MSDN 库中的函数。

## <a name="islocked"></a>SyncLockWithStatusT::IsLocked

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>备注

指示是否当前`SyncLockWithStatusT`对象拥有一个资源; 也就是，则`SyncLockWithStatusT`对象是*锁定*。

### <a name="return-value"></a>返回值

**true**如果`SyncLockWithStatusT`对象是锁定; 否则为**false**。

## <a name="status"></a>SyncLockWithStatusT::status_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD status_;
```

### <a name="remarks"></a>备注

保存后对象的锁操作取决于当前的基础的等待操作结果`SyncLockWithStatusT`对象。

## <a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

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

*other*<br/>
对另一个右值引用`SyncLockWithStatusT`对象。

*sync*<br/>
对另一个引用`SyncLockWithStatusT`对象。

*status*<br/>
值[status_](#status)的数据成员*其他*参数或*同步*参数。

### <a name="remarks"></a>备注

初始化 `SyncLockWithStatusT` 类的新实例。

第一个构造函数初始化当前`SyncLockWithStatusT`从另一个对象`SyncLockWithStatusT`由参数指定*其他*，然后使其他和`SyncLockWithStatusT`对象。 第二个构造函数是`protected`，并初始化当前`SyncLockWithStatusT`为无效状态的对象。
