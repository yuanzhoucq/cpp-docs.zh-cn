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
ms.openlocfilehash: f0e742a0cc1a0809fc08b3862cadb7e3deb36fa8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351503"
---
# <a name="tilebarrier-class"></a>tile_barrier 类

同步使用线程组 （磁贴） 中运行的线程执行`wait`方法。 只有运行时可以实例化此类。

### <a name="syntax"></a>语法

```
class tile_barrier;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[tile_barrier 构造函数](#ctor)|初始化 `tile_barrier` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[wait](#wait)|指示要停止执行，直到平铺中的所有线程都完成等待的线程组 （磁贴） 中的所有线程。|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|阻止执行，直到所有内存访问都完成的磁贴中的所有线程和磁贴中的所有线程都达到此调用。|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|阻止平铺，直到所有全局内存访问都完成且该磁贴中的所有线程都达到此调用中的所有线程的执行。|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|阻止平铺中的所有线程的执行，直到所有`tile_static`内存访问都完成且该磁贴中的所有线程都达到此调用。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`tile_barrier`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="ctor"></a>  tile_barrier 构造函数

通过复制现有初始化类的新实例。

### <a name="syntax"></a>语法

```
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
`tile_barrier`要复制对象。

## <a name="wait"></a>等待

指示线程组 (Tile) 中的所有线程停止执行，直到 Tile 中的所有线程完成等待。

### <a name="syntax"></a>语法

```
void wait() const restrict(amp);
```

## <a name="waitwithallmemoryfence"></a>wait_with_all_memory_fence

阻止平铺中的所有线程都达到此调用之前的磁贴中的所有线程的执行。 这可确保所有内存访问对于线程平铺中的其他线程是可见的并已按程序顺序执行。

### <a name="syntax"></a>语法

```
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="waitwithglobalmemoryfence"></a>wait_with_global_memory_fence

阻止平铺中的所有线程都达到此调用之前的磁贴中的所有线程的执行。 这可确保所有全局内存访问对于线程平铺中的其他线程是可见并已按程序顺序执行。

### <a name="syntax"></a>语法

```
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="waitwithtilestaticmemoryfence"></a>wait_with_tile_static_memory_fence

阻止平铺中的所有线程都达到此调用之前的磁贴中的所有线程的执行。 这可确保`tile_static`内存访问对于线程平铺中的其他线程是可见并已按程序顺序执行。

### <a name="syntax"></a>语法

```
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
