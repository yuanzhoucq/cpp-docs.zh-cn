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
ms.openlocfilehash: 4b7dbe8ae1648e4185a9eb1e1142df4a3869aa2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216539"
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
一种类型，该类型可以采用资源的独占或共享所有权。

## <a name="remarks"></a>备注

表示一个类型，该类型可以采用资源的独占或共享所有权。

`SyncLockWithStatusT`类用于实现[互斥体](mutex-class.md)和[信号灯](semaphore-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT：： SyncLockWithStatusT](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="protected-constructors"></a>受保护的构造函数

名称                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT：： SyncLockWithStatusT](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 类的新实例。

### <a name="public-methods"></a>公共方法

“属性”                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT：： GetStatus](#getstatus) | 检索当前对象的等待状态 `SyncLockWithStatusT` 。
[SyncLockWithStatusT：： IsLocked](#islocked)   | 指示当前对象是否 `SyncLockWithStatusT` 拥有资源; 即， `SyncLockWithStatusT` 对象已*锁定*。

### <a name="protected-data-members"></a>受保护的数据成员

名称                                    | 描述
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT：： status_](#status) | 保存基于当前对象的对象上的锁定操作后的基础等待操作的结果 `SyncLockWithStatusT` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装：:D etails

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT：： GetStatus

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>返回值

基于类的对象（ `SyncLockWithStatusT` 如[互斥体](mutex-class.md)或[信号量](semaphore-class.md)）上等待操作的结果。 零（0）指示等待操作返回了终止状态;否则，会发生另一种状态，如已用超时值。

### <a name="remarks"></a>备注

检索当前对象的等待状态 `SyncLockWithStatusT` 。

GetStatus （）函数检索基础[status_](#status)数据成员的值。 当基于类的对象 `SyncLockWithStatusT` 执行锁定操作时，对象首先会等待对象变为可用。 该等待操作的结果存储在 `status_` 数据成员中。 数据成员的可能值 `status_` 为 wait 操作的返回值。 有关详细信息，请参阅函数的返回值 [`WaitForSingleObjectEx`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobjectex) 。

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT：： IsLocked

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>备注

指示当前对象是否 `SyncLockWithStatusT` 拥有资源; 即， `SyncLockWithStatusT` 对象已*锁定*。

### <a name="return-value"></a>返回值

**`true`** 如果 `SyncLockWithStatusT` 对象被锁定，则为; 否则为 **`false`** 。

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT：： status_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
DWORD status_;
```

### <a name="remarks"></a>备注

保存基于当前对象的对象上的锁定操作后的基础等待操作的结果 `SyncLockWithStatusT` 。

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>SyncLockWithStatusT：： SyncLockWithStatusT

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

*以外*<br/>
对另一对象的 rvalue 引用 `SyncLockWithStatusT` 。

*同步*<br/>
对另一对象的引用 `SyncLockWithStatusT` 。

*status*<br/>
*其他*参数或*sync*参数的[status_](#status)数据成员的值。

### <a name="remarks"></a>备注

初始化 `SyncLockWithStatusT` 类的新实例。

第一个构造函数 `SyncLockWithStatusT` 从另一个由参数指定的中初始化当前对象 `SyncLockWithStatusT` ，然后使另一个对象失效*other* `SyncLockWithStatusT` 。 第二个构造函数为 **`protected`** ，并将当前 `SyncLockWithStatusT` 对象初始化为无效状态。
