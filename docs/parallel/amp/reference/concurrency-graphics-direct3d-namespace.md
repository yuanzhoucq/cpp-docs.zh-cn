---
title: Concurrency::graphics::direct3d 命名空间
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
ms.openlocfilehash: 4911787fd17877769eb723cf1e61e29fe626a783
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139427"
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d 命名空间

提供[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)和[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)方法。

## <a name="syntax"></a>语法

```cpp
namespace direct3d;
```

## <a name="members"></a>Members

### <a name="functions"></a>函数

|名称<br /><br /> 说明|
|--------------------------|
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> 获取表示指定的采样器对象的给定快捷键视图上的 Direct3D 采样器状态接口。|
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> 获取指定[纹理](texture-class.md)对象基础的 Direct3D 纹理接口。|
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> 从 Direct3D 采样器状态接口指针创建采样器。|
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> 使用指定的参数创建[纹理](texture-class.md)对象。|
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> 比较4个字节的引用值和8个字节的源值，并累计4个和的向量。|

## <a name="requirements"></a>要求

**标头：** amp_graphics。h

**命名空间：** Concurrency：： graphics

## <a name="see-also"></a>另请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
