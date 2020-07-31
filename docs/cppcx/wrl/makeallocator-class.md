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
ms.openlocfilehash: 19d3ab294df8adc059424c97e5733ae9ebb75c9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218372"
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
**`true`** 为支持弱引用的对象分配内存;**`false`** 为不支持弱引用的对象分配内存。

## <a name="remarks"></a>备注

为可激活的类分配内存，但不支持弱引用。

重写 `MakeAllocator` 类以实现用户定义的内存分配模型。

`MakeAllocator`通常用于在构造过程中引发对象时防止内存泄漏。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator：： MakeAllocator](#makeallocator)        | 初始化 `MakeAllocator` 类的新实例。
[MakeAllocator：： ~ MakeAllocator](#tilde-makeallocator) | 取消初始化类的当前实例 `MakeAllocator` 。

### <a name="public-methods"></a>公共方法

“属性”                                 | 描述
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator：： Allocate](#allocate) | 分配内存并将其与当前的 `MakeAllocator` 对象相关联。
[MakeAllocator：:D etach](#detach)     | 解除[分配](#allocate)方法从当前对象分配的内存 `MakeAllocator` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`MakeAllocator`

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator：： Allocate

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>返回值

如果成功，则为指向分配的内存的指针;否则为 **`nullptr`** 。

### <a name="remarks"></a>备注

分配内存并将其与当前的 `MakeAllocator` 对象相关联。

分配的内存的大小为当前模板参数所指定的类型的大小 `MakeAllocator` 。

开发人员只需重写 `Allocate()` 方法即可实现不同的内存分配模型。

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator：:D etach

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>备注

解除[分配](#allocate)方法从当前对象分配的内存 `MakeAllocator` 。

如果调用 `Detach()` ，则负责删除方法提供的内存 `Allocate` 。

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator：： MakeAllocator

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
MakeAllocator();
```

### <a name="remarks"></a>备注

初始化 `MakeAllocator` 类的新实例。

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator：： ~ MakeAllocator

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>备注

取消初始化类的当前实例 `MakeAllocator` 。

如果需要，此析构函数还会删除基础已分配的内存。
