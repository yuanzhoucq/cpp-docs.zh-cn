---
title: ModuleBase 类
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 4a65b7335626cc36a4eecbe61465778889a9e7e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502123"
---
# <a name="modulebase-class"></a>ModuleBase 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class ModuleBase;
```

## <a name="remarks"></a>备注

表示类的基类[模块](../windows/module-class.md)类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                         | 描述
-------------------------------------------- | ---------------------------------------------------------
[Modulebase:: Modulebase](#modulebase)        | 初始化 `Module` 类的实例。
[ModuleBase:: ~ ModuleBase](#tilde-modulebase) | 取消初始化的当前实例`Module`类。

### <a name="public-methods"></a>公共方法

名称                                                      | 描述
--------------------------------------------------------- | -------------------------------------------------------------------------
[Modulebase:: Decrementobjectcount](#decrementobjectcount) | 实现时，递减的对象数模块所跟踪。
[Modulebase:: Incrementobjectcount](#incrementobjectcount) | 实现时，递增模块所跟踪的对象数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ModuleBase`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="tilde-modulebase"></a>ModuleBase:: ~ ModuleBase

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>备注

取消初始化的当前实例`ModuleBase`类。

## <a name="decrementobjectcount"></a>Modulebase:: Decrementobjectcount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>返回值

递减操作之前的计数。

### <a name="remarks"></a>备注

实现时，递减的对象数模块所跟踪。

## <a name="incrementobjectcount"></a>Modulebase:: Incrementobjectcount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>返回值

递增操作之前的计数。

### <a name="remarks"></a>备注

实现时，递增模块所跟踪的对象数。

## <a name="modulebase"></a>Modulebase:: Modulebase

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ModuleBase();
```

### <a name="remarks"></a>备注

初始化 `Module` 类的实例。
