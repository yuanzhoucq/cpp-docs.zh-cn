---
title: simple_partitioner 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
dev_langs:
- C++
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89114c96beb49c8f843ec8a04b08802632c61ca1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401506"
---
# <a name="simplepartitioner-class"></a>simple_partitioner 类

`simple_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 分区程序将该范围分成区块，以便每个区块都至少具有区块大小指定的迭代数量。

## <a name="syntax"></a>语法

```
class simple_partitioner;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[simple_partitioner](#ctor)|构造 `simple_partitioner` 对象。|
|[~ simple_partitioner 析构函数](#dtor)|销毁 `simple_partitioner` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`simple_partitioner`

## <a name="requirements"></a>要求

**标头：** ppl.h

**命名空间：** 并发

##  <a name="dtor"></a> ~simple_partitioner

销毁 `simple_partitioner` 对象。

```
~simple_partitioner();
```

##  <a name="ctor"></a> simple_partitioner

构造 `simple_partitioner` 对象。

```
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>参数

*_Chunk_size*<br/>
最小分区大小。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
