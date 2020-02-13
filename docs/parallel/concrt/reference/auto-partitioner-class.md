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
ms.openlocfilehash: 4d1d8f19069412240de8e9d69cdcfb34618f2796
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142868"
---
# <a name="auto_partitioner-class"></a>auto_partitioner 类

`auto_partitioner` 类表示 `parallel_for`、`parallel_for_each` 和 `parallel_transform` 用于对其循环访问的范围进行分区的默认方法。 这种分区方法使用范围偷窃来实现负载平衡和按循环访问。

## <a name="syntax"></a>语法

```cpp
class auto_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[auto_partitioner](#ctor)|构造 `auto_partitioner` 对象。|
|[~ auto_partitioner 析构函数](#dtor)|销毁 `auto_partitioner` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`auto_partitioner`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="dtor"></a>~ auto_partitioner

销毁 `auto_partitioner` 对象。

```cpp
~auto_partitioner();
```

## <a name="ctor"></a>auto_partitioner

构造 `auto_partitioner` 对象。

```cpp
auto_partitioner();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
