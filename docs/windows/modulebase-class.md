---
title: ModuleBase 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6d60e5114d189ddede87899bb55fba25a296c57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601466"
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

|名称|描述|
|----------|-----------------|
|[ModuleBase::ModuleBase 构造函数](../windows/modulebase-modulebase-constructor.md)|初始化 `Module` 类的实例。|
|[ModuleBase::~ModuleBase 析构函数](../windows/modulebase-tilde-modulebase-destructor.md)|取消初始化的当前实例`Module`类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[ModuleBase::DecrementObjectCount 方法](../windows/modulebase-decrementobjectcount-method.md)|实现时，递减的对象数模块所跟踪。|
|[ModuleBase::IncrementObjectCount 方法](../windows/modulebase-incrementobjectcount-method.md)|实现时，递增模块所跟踪的对象数。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`ModuleBase`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)