---
title: static_partitioner 类
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: 7a58daa27bc7a2f51f78a3068a2f152979ffdd72
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142684"
---
# <a name="static_partitioner-class"></a>static_partitioner 类

`static_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 分区程序将范围划分为多个块，因为有可用于基础计划程序的工作线程。

## <a name="syntax"></a>语法

```cpp
class static_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[static_partitioner](#ctor)|构造 `static_partitioner` 对象。|
|[~ static_partitioner 析构函数](#dtor)|销毁 `static_partitioner` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`static_partitioner`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="dtor"></a>~ static_partitioner

销毁 `static_partitioner` 对象。

```cpp
~static_partitioner();
```

## <a name="ctor"></a>static_partitioner

构造 `static_partitioner` 对象。

```cpp
static_partitioner();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
