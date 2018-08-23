---
title: 信号量类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb0b3d5dff91bcb1fb1688c7b1a9314fe7ebf00c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598410"
---
# <a name="semaphore-class"></a>Semaphore 类

表示控制可支持有限数量用户的共享资源的同步对象。

## <a name="syntax"></a>语法

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`SyncLock`|类支持同步锁的同义词。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[Semaphore::Semaphore 构造函数](../windows/semaphore-semaphore-constructor.md)|初始化的新实例**信号量**类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|调用其签名包含指定的数量的参数的事件处理程序。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[Semaphore::Lock 方法](../windows/semaphore-lock-method.md)|将等待，直到当前的对象或与指定句柄关联的对象处于已发出信号状态或指定的超时间隔已过。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[Semaphore::operator= 运算符](../windows/semaphore-operator-assign-operator.md)|将从指定句柄**信号量**对象与当前**信号量**对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Semaphore`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)