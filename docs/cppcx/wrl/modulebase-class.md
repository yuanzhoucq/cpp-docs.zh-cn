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
ms.openlocfilehash: 13a8ceef3133e9946524e1fcd02e96535eccd7fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371263"
---
# <a name="modulebase-class"></a>ModuleBase 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class ModuleBase;
```

## <a name="remarks"></a>备注

表示[模块](module-class.md)类的基类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                         | 说明
-------------------------------------------- | ---------------------------------------------------------
[模块基础：：模块库](#modulebase)        | 初始化 `Module` 类的实例。
[模块基础：：*模块库](#tilde-modulebase) | 取消初始化类的`Module`当前实例。

### <a name="public-methods"></a>公共方法

名称                                                      | 说明
--------------------------------------------------------- | -------------------------------------------------------------------------
[模块基础：:D对象计数](#decrementobjectcount) | 实现后，将声明模块跟踪的对象数。
[模块基础：：增量对象计数](#incrementobjectcount) | 实现后，将递增模块跟踪的对象数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ModuleBase`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a>模块基础：：*模块库

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>备注

取消初始化类的`ModuleBase`当前实例。

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a>模块基础：:D对象计数

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>返回值

递减操作之前的计数。

### <a name="remarks"></a>备注

实现后，将声明模块跟踪的对象数。

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a>模块基础：：增量对象计数

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>返回值

递增操作之前的计数。

### <a name="remarks"></a>备注

实现后，将递增模块跟踪的对象数。

## <a name="modulebasemodulebase"></a><a name="modulebase"></a>模块基础：：模块库

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ModuleBase();
```

### <a name="remarks"></a>备注

初始化 `Module` 类的实例。
