---
title: static_partitioner 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs:
- C++
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de1b63cf24fbc84130302fcbae2cb965e8d00597
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376015"
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
