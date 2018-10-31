---
title: SyncLockWithStatusT 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36cee8d6f2cb41a22574f60c5cf86747228205bb
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163063"
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

`SyncLockWithStatusT`类用于实现[Mutex](../windows/mutex-class1.md)并[信号量](../windows/semaphore-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust:: Synclockwithstatust](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="protected-constructors"></a>受保护的构造函数

名称                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust:: Synclockwithstatust](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust:: Getstatus](#getstatus) | 检索当前的等待状态`SyncLockWithStatusT`对象。
[Synclockwithstatust:: Islocked](#islocked)   | 指示是否当前`SyncLockWithStatusT`对象拥有一个资源; 也就是，则`SyncLockWithStatusT`对象是*锁定*。

### <a name="protected-data-members"></a>受保护的数据成员

name                                    | 描述
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust:: Status_](#status) | 保存后对象的锁操作取决于当前的基础的等待操作结果`SyncLockWithStatusT`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>Synclockwithstatust:: Getstatus

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>返回值

基于对象的等待操作结果`SyncLockWithStatusT`类，如[Mutex](../windows/mutex-class1.md)或[信号量](../windows/semaphore-class.md)。 零 (0) 指示等待操作返回已发出信号的状态;否则，另一种状态发生，如已用超时值。

### <a name="remarks"></a>备注

检索当前的等待状态`SyncLockWithStatusT`对象。

GetStatus() 函数用于检索基础[status_](#status)数据成员。 当对象基于`SyncLockWithStatusT`类执行锁定操作，该对象将会先等待对象变得可用。 这一等待操作的结果存储在`status_`数据成员。 可能值`status_`数据成员是等待操作的返回值。 有关详细信息，请参阅的返回值`WaitForSingleObjectEx()`MSDN 库中的函数。

## <a name="islocked"></a>Synclockwithstatust:: Islocked

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>备注

指示是否当前`SyncLockWithStatusT`对象拥有一个资源; 也就是，则`SyncLockWithStatusT`对象是*锁定*。

### <a name="return-value"></a>返回值

**true**如果`SyncLockWithStatusT`对象是锁定; 否则为**false**。

## <a name="status"></a>Synclockwithstatust:: Status_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD status_;
```

### <a name="remarks"></a>备注

保存后对象的锁操作取决于当前的基础的等待操作结果`SyncLockWithStatusT`对象。

## <a name="synclockwithstatust"></a>Synclockwithstatust:: Synclockwithstatust

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
