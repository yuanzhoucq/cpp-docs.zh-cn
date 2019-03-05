---
title: auto_partitioner 类
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 2d8bbb8e8af17dd19953487c47e5fd40343fe349
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264815"
---
# <a name="autopartitioner-class"></a>auto_partitioner 类


  `auto_partitioner` 类表示 `parallel_for`、`parallel_for_each` 和 `parallel_transform` 用于对其循环访问的范围进行分区的默认方法。 此分区方法使用范围窃取进行负载平衡以及按循环访问取消。

## <a name="syntax"></a>语法

```
class auto_partitioner;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[auto_partitioner](#ctor)|构造 `auto_partitioner` 对象。|
|[~ auto_partitioner 析构函数](#dtor)|销毁 `auto_partitioner` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`auto_partitioner`

## <a name="requirements"></a>要求

**标头：** ppl.h

**命名空间：** 并发

##  <a name="dtor"></a> ~auto_partitioner

销毁 `auto_partitioner` 对象。

```
~auto_partitioner();
```

##  <a name="ctor"></a> auto_partitioner

构造 `auto_partitioner` 对象。

```
auto_partitioner();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
