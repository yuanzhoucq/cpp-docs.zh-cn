---
title: scheduler_interface 结构
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 36feff80cab1c5d301c009a581b869d5c2bad5e9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142153"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface 结构

计划程序接口

## <a name="syntax"></a>语法

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[scheduler_interface：： schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`scheduler_interface`

## <a name="requirements"></a>要求

**标头：** pplinterface。h

**命名空间：** 并发

## <a name="schedule"></a>scheduler_interface：： schedule 方法

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
