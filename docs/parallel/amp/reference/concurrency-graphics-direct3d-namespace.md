---
title: Concurrency::graphics::direct3d 命名空间
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
ms.openlocfilehash: 2a07aeab410750e38684f564df4cb89c1846b95e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626819"
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d 命名空间

提供了[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)并[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)方法。

## <a name="syntax"></a>语法

```
namespace direct3d;
```

## <a name="members"></a>成员

### <a name="functions"></a>函数

|名称<br /><br /> 描述|
|--------------------------|
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> 获取 Direct3D 采样器状态接口上给定的加速器视图，它表示指定的采样器对象。|
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> 获取指定的基础 Direct3D 纹理接口[纹理](texture-class.md)对象。|
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> 从 Direct3D 采样器状态接口指针创建采样器。|
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> 创建[纹理](texture-class.md)对象使用指定的参数。|
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> 将 4 字节引用值和一个 8 字节源值进行比较，并累积 4 个和矢量。|

## <a name="requirements"></a>要求

**标头：** amp_graphics.h

**Namespace:** concurrency:: graphics

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
