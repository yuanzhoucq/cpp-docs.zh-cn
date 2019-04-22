---
title: MakeAllocator 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: 805f0c09b0490d8cec1a0be96dcb1fc99a051371
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58783850"
---
# <a name="makeallocator-class"></a>MakeAllocator 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>参数

*T*<br/>
类型名称。

*hasWeakReferenceSupport*<br/>
**true**为支持弱引用; 的对象分配内存**false**为不支持弱引用的对象分配内存。

## <a name="remarks"></a>备注

可激活的类，带或不带弱引用支持，为分配内存。

重写`MakeAllocator`类，以实现用户定义的内存分配模型。

`MakeAllocator` 通常用于防止内存泄漏，如果在构造期间引发的对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | 初始化 `MakeAllocator` 类的新实例。
[MakeAllocator::~MakeAllocator](#tilde-makeallocator) | 取消初始化的当前实例`MakeAllocator`类。

### <a name="public-methods"></a>公共方法

名称                                 | 描述
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Allocate](#allocate) | 分配内存，并将其与当前关联`MakeAllocator`对象。
[MakeAllocator::Detach](#detach)     | 解除分配的内存之间的关联[分配](#allocate)方法从当前`MakeAllocator`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`MakeAllocator`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL::Details

## <a name="allocate"></a>MakeAllocator::Allocate

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>返回值

如果成功，指向已分配的内存中;否则为`nullptr`。

### <a name="remarks"></a>备注

分配内存，并将其与当前关联`MakeAllocator`对象。

已分配内存的大小是由当前指定的类型的大小`MakeAllocator`模板参数。

开发人员需要仅重写`Allocate()`方法来实现不同的内存分配模型。

## <a name="detach"></a>MakeAllocator::Detach

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>备注

解除分配的内存之间的关联[分配](#allocate)方法从当前`MakeAllocator`对象。

如果您调用`Detach()`，你需要负责删除提供的内存`Allocate`方法。

## <a name="makeallocator"></a>MakeAllocator::MakeAllocator

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
MakeAllocator();
```

### <a name="remarks"></a>备注

初始化 `MakeAllocator` 类的新实例。

## <a name="tilde-makeallocator"></a>MakeAllocator:: ~ MakeAllocator

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>备注

取消初始化的当前实例`MakeAllocator`类。

如有必要，此析构函数也会删除基础已分配的内存。
