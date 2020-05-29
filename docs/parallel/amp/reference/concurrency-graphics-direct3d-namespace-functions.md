---
title: Concurrency::graphics::direct3d 命名空间函数
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 330c1aa94b1d122901fc23576686032400249d31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376389"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空间函数

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[姆萨德4](#msad4)|

## <a name="get_sampler"></a><a name="get_sampler"></a>get_sampler

获取表示指定采样器对象的给定加速器视图上的 D3D 采样器状态接口。

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>参数

*_Av*<br/>
要创建 D3D 采样器状态的 D3D 加速器视图。

*_Sampler*<br/>
为其创建基础 D3D 采样器状态接口的采样器对象。

### <a name="return-value"></a>返回值

I未知接口指针对应于表示给定采样器的 D3D 采样器状态。

## <a name="get_texture"></a><a name="get_texture"></a>get_texture

获取指定[纹理](texture-class.md)对象基础的 Direct3D 纹理界面。

```cpp
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
纹理的排名。

*_Texture*<br/>
与返回基础 Direct3D 纹理接口accelerator_view关联的纹理或纹理视图。

### <a name="return-value"></a>返回值

I未知接口指针对应于纹理基础的 Direct3D 纹理。

## <a name="make_sampler"></a><a name="make_sampler"></a>make_sampler

从 D3D 采样器状态接口指针创建采样器。

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>参数

*_D3D_sampler*<br/>
D3D 采样器状态的 I 未知接口指针，用于从中创建采样器。

### <a name="return-value"></a>返回值

采样器表示提供的 D3D 采样器状态。

## <a name="make_texture"></a><a name="make_texture"></a>make_texture

使用指定的参数创建[纹理](texture-class.md)对象。

```cpp
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
纹理的排名。

*_Av*<br/>
要在其中创建纹理的 D3D 快捷键视图。

*_D3D_texture*<br/>
D3D 纹理的 I 未知接口指针，用于从中创建纹理。

*_View_format*<br/>
用于使用此纹理创建的视图的 DXGI 格式。 通过DXGI_FORMAT_UNKNOWN（默认值）从_D3D_texture的基础格式和value_type派生格式。 提供的格式必须与_D3D_texture的基础格式兼容。

### <a name="return-value"></a>返回值

使用提供的 D3D 纹理的纹理。

## <a name="msad4"></a><a name="msad4"></a>姆萨德4

比较 4 字节参考值和 8 字节源值，并累积 4 个总和的矢量。 每个总和对应于参考值和源值之间不同字节对齐的绝对差异的蒙版总和。

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>参数

*_Reference*<br/>
一个 uint 值中 4 个字节的引用数组

*_Source*<br/>
在两个 uint 值的矢量中 8 个字节的源数组。

*_Accum*<br/>
要添加到参考值和源值之间不同字节对齐的掩蔽绝对差异的 4 个值的矢量。

### <a name="return-value"></a>返回值

返回 4 个总和的矢量。 每个总和对应于参考值和源值之间不同字节对齐的绝对差异的蒙版总和。

## <a name="requirements"></a>要求

**标题：** amp_graphics.h

**命名空间：** 并发：：图形：:direct3d

## <a name="see-also"></a>另请参阅

[Concurrency::graphics::direct3d 命名空间](concurrency-graphics-direct3d-namespace.md)
