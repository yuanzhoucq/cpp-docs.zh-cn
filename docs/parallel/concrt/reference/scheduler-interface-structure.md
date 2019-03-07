---
title: scheduler_interface 结构
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 99a3ea8b6ad1f23b4f3d54b7f2f406a3d115b374
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283366"
---
# <a name="schedulerinterface-structure"></a>scheduler_interface 结构

计划程序接口

## <a name="syntax"></a>语法

```
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[scheduler_interface::schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`scheduler_interface`

## <a name="requirements"></a>要求

**标头：** pplinterface.h

**命名空间：** 并发

##  <a name="schedule"></a>  scheduler_interface:: schedule 方法

```
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
