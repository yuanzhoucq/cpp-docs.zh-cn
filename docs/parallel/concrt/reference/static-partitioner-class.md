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
ms.openlocfilehash: a0d06326b2ecbf3c427ae24b45751f7053778a0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500888"
---
# <a name="staticpartitioner-class"></a>static_partitioner 类

`static_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 只要基础计划程序有工作线程可用，分区程序就会将范围分成尽可能多的区块。

## <a name="syntax"></a>语法

```
class static_partitioner;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[static_partitioner](#ctor)|构造 `static_partitioner` 对象。|
|[~ static_partitioner 析构函数](#dtor)|销毁 `static_partitioner` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`static_partitioner`

## <a name="requirements"></a>要求

**标头：** ppl.h

**命名空间：** 并发

##  <a name="dtor"></a> ~static_partitioner

销毁 `static_partitioner` 对象。

```
~static_partitioner();
```

##  <a name="ctor"></a> static_partitioner

构造 `static_partitioner` 对象。

```
static_partitioner();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
