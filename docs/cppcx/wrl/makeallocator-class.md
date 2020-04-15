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
ms.openlocfilehash: dc0d83f2550646572a4eff2bec7850037c6dbf6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371324"
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

*有弱参考支持*<br/>
**为**支持弱引用的对象分配内存;为不支持弱引用的对象分配内存**为 false。**

## <a name="remarks"></a>备注

为可激活类分配内存，无论是否具有弱引用支持。

重写类`MakeAllocator`以实现用户定义的内存分配模型。

`MakeAllocator`通常用于防止在构造期间对象引发时内存泄漏。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                  | 说明
----------------------------------------------------- | ----------------------------------------------------------------
[制造定位器：：制造定位器](#makeallocator)        | 初始化 `MakeAllocator` 类的新实例。
[制造定位器：：\制造定位器](#tilde-makeallocator) | 取消初始化类的`MakeAllocator`当前实例。

### <a name="public-methods"></a>公共方法

名称                                 | 说明
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[制造定位器：：分配](#allocate) | 分配内存并将其与当前`MakeAllocator`对象关联。
[制造者：:D埃塔奇](#detach)     | 将[分配](#allocate)方法分配的内存与当前`MakeAllocator`对象分离。

## <a name="inheritance-hierarchy"></a>继承层次结构

`MakeAllocator`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="makeallocatorallocate"></a><a name="allocate"></a>制造定位器：：分配

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>返回值

如果成功，则指向分配的内存的指针;否则， `nullptr`.

### <a name="remarks"></a>备注

分配内存并将其与当前`MakeAllocator`对象关联。

分配的内存的大小是当前`MakeAllocator`模板参数指定的类型的大小。

开发人员只需重写`Allocate()`该方法，以实现不同的内存分配模型。

## <a name="makeallocatordetach"></a><a name="detach"></a>制造者：:D埃塔奇

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>备注

将[分配](#allocate)方法分配的内存与当前`MakeAllocator`对象分离。

如果调用`Detach()`，则负责删除`Allocate`方法提供的内存。

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>制造定位器：：制造定位器

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
MakeAllocator();
```

### <a name="remarks"></a>备注

初始化 `MakeAllocator` 类的新实例。

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>制造定位器：：\制造定位器

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>备注

取消初始化类的`MakeAllocator`当前实例。

如有必要，此析构函数还会删除基础分配的内存。
