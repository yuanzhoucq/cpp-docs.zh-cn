---
title: Concurrency::graphics::direct3d 命名空间函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs:
- C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45b9b2b9f6d3ff6b08d7aac2a8ecddafe017fc13
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375688"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空间函数

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

##  <a name="get_sampler"></a>  get_sampler

获取 D3D 采样器状态接口上给定的加速器视图，它表示指定的采样器对象。

```
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>参数

*_Av*<br/>
D3D 采样器状态是要创建 D3D 加速器视图。

*_Sampler*<br/>
为其创建基础 D3D 采样器状态接口的采样器对象。

### <a name="return-value"></a>返回值

对应于表示给定采样器的 D3D 采样器状态 IUnknown 接口指针。

##  <a name="get_texture"></a>  get_texture

获取指定的基础 Direct3D 纹理接口[纹理](texture-class.md)对象。

```
template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const texture<value_type, _Rank>& _Texture) restrict(cpu);

template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const writeonly_texture_view<value_type, _Rank>& _Texture) restrict(cpu);

template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const texture_view<value_type, _Rank>& _Texture) restrict(cpu);

```

### <a name="parameters"></a>参数

*value_type*<br/>
纹理的元素类型。

*_Rank*<br/>
纹理的等级。

*_Texture*<br/>
纹理或纹理视图为其基础 Direct3D 纹理接口返回的 accelerator_view 相关联。

### <a name="return-value"></a>返回值

对应于基础 Direct3D 纹理 IUnknown 接口指针。

##  <a name="make_sampler"></a>  make_sampler

从 D3D 采样器状态接口指针创建采样器。

```
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>参数

*_D3D_sampler*<br/>
若要创建采样器的 D3D 采样器状态 IUnknown 接口指针。

### <a name="return-value"></a>返回值

采样器表示所提供的 D3D 采样器状态。

##  <a name="make_texture"></a>  make_texture

创建[纹理](texture-class.md)对象使用指定的参数。

```
template<
    typename value_type,
    int _Rank
>
texture<value_type, _Rank> make_texture(
    const Concurrency::accelerator_view& _Av,
    _In_ IUnknown* _D3D_texture,
    DXGI_FORMAT _View_format = DXGI_FORMAT_UNKNOWN) restrict(cpu);
```

### <a name="parameters"></a>参数

*value_type*<br/>
纹理中元素的类型。

*_Rank*<br/>
纹理的等级。

*_Av*<br/>
纹理是要创建 D3D 加速器视图。

*_D3D_texture*<br/>
若要创建从纹理的 D3D 纹理 IUnknown 接口指针。

*_View_format*<br/>
要用于从此纹理创建的视图的 DXGI 格式。 传递 DXGI_FORMAT_UNKNOWN （默认值） 以从 _D3D_texture 的基础格式和此模板的 value_type 派生格式。 所提供的格式必须与 _D3D_texture 的基础格式兼容。

### <a name="return-value"></a>返回值

使用提供的 D3D 纹理的纹理。

##  <a name="msad4"></a>  msad4

将 4 字节引用值和一个 8 字节源值进行比较，并累积 4 个和矢量。 每个总和对应引用值和源值之间不同字节对齐的绝对差异的掩码总和。

```
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>参数

*（_r)*<br/>
一个 uint 值为 4 个字节引用数组

*_Source*<br/>
源数组的两个 uint 值矢量中的 8 个字节。

*_Accum*<br/>
若要添加到引用值和源值之间不同字节对齐的绝对差异的掩码总和的 4 个值的向量。

### <a name="return-value"></a>返回值

返回 4 个和矢量。 每个总和对应引用值和源值之间不同字节对齐的绝对差异的掩码总和。

## <a name="requirements"></a>要求

**标头：** amp_graphics.h

**Namespace:** Concurrency::graphics::direct3d

## <a name="see-also"></a>请参阅

[Concurrency::graphics::direct3d 命名空间](concurrency-graphics-direct3d-namespace.md)
