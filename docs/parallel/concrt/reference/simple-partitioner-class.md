---
title: simple_partitioner 类
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 503f36b90c5eb3319f9aa2d56528172ffa95bb11
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142496"
---
# <a name="simple_partitioner-class"></a>simple_partitioner 类

`simple_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 分区程序将该范围分成区块，以便每个区块都至少具有区块大小指定的迭代数量。

## <a name="syntax"></a>语法

```cpp
class simple_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[simple_partitioner](#ctor)|构造 `simple_partitioner` 对象。|
|[~ simple_partitioner 析构函数](#dtor)|销毁 `simple_partitioner` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`simple_partitioner`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="dtor"></a>~ simple_partitioner

销毁 `simple_partitioner` 对象。

```cpp
~simple_partitioner();
```

## <a name="ctor"></a>simple_partitioner

构造 `simple_partitioner` 对象。

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>参数

*_Chunk_size*<br/>
最小分区大小。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
