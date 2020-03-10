---
title: Concurrency::graphics::direct3d 命名空间函数
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 665732700ee6b85425f332a0eb96a5b75864a74e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855790"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空间函数

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

## <a name="get_sampler"></a>get_sampler

获取表示指定的采样器对象的给定快捷键视图上的 D3D 采样器状态接口。

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>parameters

*_Av*<br/>
要在其上创建 D3D 采样器状态的 D3D 加速器视图。

*_Sampler*<br/>
为其创建基础 D3D 采样器状态接口的采样器对象。

### <a name="return-value"></a>返回值

与表示给定采样器的 D3D 采样器状态对应的 IUnknown 接口指针。

## <a name="get_texture"></a>get_texture

获取指定[纹理](texture-class.md)对象基础的 Direct3D 纹理接口。

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

### <a name="parameters"></a>parameters

*value_type*<br/>
纹理的元素类型。

*_Rank*<br/>
纹理的排名。

*_Texture*<br/>
与为其返回基础 Direct3D 纹理接口的 accelerator_view 关联的纹理或纹理视图。

### <a name="return-value"></a>返回值

与纹理基础的 Direct3D 纹理对应的 IUnknown 接口指针。

## <a name="make_sampler"></a>make_sampler

从 D3D 采样器状态接口指针创建采样器。

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>parameters

*_D3D_sampler*<br/>
用于从其创建采样器的 D3D 采样器状态的 IUnknown 接口指针。

### <a name="return-value"></a>返回值

采样器表示提供的 D3D 采样器状态。

## <a name="make_texture"></a>make_texture

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

### <a name="parameters"></a>parameters

*value_type*<br/>
纹理中元素的类型。

*_Rank*<br/>
纹理的排名。

*_Av*<br/>
要在其上创建纹理的 D3D 加速器视图。

*_D3D_texture*<br/>
要从中创建纹理的 D3D 纹理的 IUnknown 接口指针。

*_View_format*<br/>
要用于从此纹理创建的视图的 DXGI 格式。 传递 DXGI_FORMAT_UNKNOWN （默认值），从 _D3D_texture 的基础格式和此模板的 value_type 派生格式。 提供的格式必须与 _D3D_texture 的基础格式兼容。

### <a name="return-value"></a>返回值

使用所提供 D3D 纹理的纹理。

## <a name="msad4"></a>msad4

比较4个字节的引用值和8个字节的源值，并累计4个和的向量。 每个总和对应于引用值和源值之间不同字节对齐的绝对差异的掩码总和。

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>parameters

*_Reference*<br/>
一个 uint 值中4个字节的引用数组

*_Source*<br/>
两个 uint 值的向量中的8个字节的源数组。

*_Accum*<br/>
4个值的向量，将其添加到在引用值和源值之间不同字节对齐的绝对差异的掩码总和。

### <a name="return-value"></a>返回值

返回一个4求和的向量。 每个总和对应于引用值和源值之间不同字节对齐的绝对差异的掩码总和。

## <a name="requirements"></a>要求

**标头：** amp_graphics。h

**命名空间：** Concurrency：： graphics：:d irect3d

## <a name="see-also"></a>另请参阅

[Concurrency::graphics::direct3d 命名空间](concurrency-graphics-direct3d-namespace.md)
