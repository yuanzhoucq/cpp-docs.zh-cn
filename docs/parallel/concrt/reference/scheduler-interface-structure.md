---
title: scheduler_interface 结构
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: da2ebc2f9c2878baefcfa792bac08f420dbbb281
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358787"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface 结构

计划程序接口

## <a name="syntax"></a>语法

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[scheduler_interface：计划](#schedule)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`scheduler_interface`

## <a name="requirements"></a>要求

**标题：** pplinterface.h

**命名空间：** 并发

## <a name="scheduler_interfaceschedule-method"></a><a name="schedule"></a>scheduler_interface：：计划方法

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)
