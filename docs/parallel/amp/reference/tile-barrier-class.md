---
title: tile_barrier 类
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427493"
---
# <a name="tile_barrier-class"></a>tile_barrier 类

使用 `wait` 方法同步线程组（磁贴）中正在运行的线程的执行。 只有运行时才可以实例化此类。

## <a name="syntax"></a>语法

```cpp
class tile_barrier;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[tile_barrier 构造函数](#ctor)|初始化 `tile_barrier` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[再](#wait)|指示线程组（磁贴）中的所有线程停止执行，直到磁贴中的所有线程完成等待。|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|阻止在磁贴中的所有线程的执行，直到所有内存访问都完成并且磁贴中的所有线程都达到此调用。|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|阻止在磁贴中所有线程的执行，直到所有全局内存访问都完成并且该磁贴中的所有线程都达到此调用。|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|阻止在磁贴中所有线程的执行，直到所有 `tile_static` 内存访问完成并且该磁贴中的所有线程都达到此调用。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`tile_barrier`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="ctor"></a>tile_barrier 构造函数

通过复制现有类来初始化该类的新实例。

### <a name="syntax"></a>语法

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>parameters

*_Other*<br/>
要复制的 `tile_barrier` 对象。

## <a name="wait"></a>wait

指示线程组 (Tile) 中的所有线程停止执行，直到 Tile 中的所有线程完成等待。

### <a name="syntax"></a>语法

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

阻止在磁贴中的所有线程的执行，直到磁贴中的所有线程都达到此调用。 这可确保所有内存访问对于线程平铺中的其他线程是可见的，并已按程序顺序执行。

### <a name="syntax"></a>语法

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

阻止在磁贴中的所有线程的执行，直到磁贴中的所有线程都达到此调用。 这可确保所有全局内存访问对线程平铺中的其他线程可见，并按程序顺序执行。

### <a name="syntax"></a>语法

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

阻止在磁贴中的所有线程的执行，直到磁贴中的所有线程都达到此调用。 这可确保 `tile_static` 内存访问对线程平铺中的其他线程可见，并已按程序顺序执行。

### <a name="syntax"></a>语法

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
