---
title: "Concurrency::graphics::direct3d 命名空间函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs: C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 97f03dbf71c0f8b97b750532279e4cc76d01fb64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空间函数
||||  
|-|-|-|  
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|  
|[make_texture](#make_texture)|[msad4](#msad4)|  

 
##  <a name="get_sampler"></a>get_sampler  
 Get D3D 采样器状态接口给定加速器上查看，它表示指定的采样器对象。  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 D3D 采样器状态是要创建 D3D 快捷键视图。  
  
 `_Sampler`  
 为其创建基础 D3D 采样器状态接口的采样器对象。  
  
### <a name="return-value"></a>返回值  
 IUnknown 接口指针表示给定的采样器的 D3D 采样器状态相对应。  
  
##  <a name="get_texture"></a>get_texture  
 获取 Direct3D 纹理接口基础指定[纹理](texture-class.md)对象。  
  
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
 `value_type`  
 元素类型的纹理。  
  
 `_Rank`  
 纹理的秩。  
  
 `_Texture`  
 纹理或与为其返回基础 Direct3D 纹理接口 accelerator_view 相关联的纹理视图。  
  
### <a name="return-value"></a>返回值  
 对应于基础纹理的 Direct3D 纹理 IUnknown 接口指针。  
  
##  <a name="make_sampler"></a>make_sampler  
 创建从 D3D 采样器状态的接口指针的采样器。  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_D3D_sampler`  
 D3D 采样器状态，以便创建的采样器从 IUnknown 接口指针。  
  
### <a name="return-value"></a>返回值  
 采样器表示提供的 D3D 采样器状态。  
  
##  <a name="make_texture"></a>make_texture  
 创建[纹理](texture-class.md)通过使用指定的参数的对象。  
  
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
 `value_type`  
 纹理中的元素的类型。  
  
 `_Rank`  
 纹理的秩。  
  
 `_Av`  
 纹理是要创建 D3D 快捷键视图。  
  
 `_D3D_texture`  
 若要创建从纹理的 D3D 纹理的 IUnknown 接口指针。  
  
 `_View_format`  
 要用于创建从此纹理视图的 DXGI 格式。 将传递 DXGI_FORMAT_UNKNOWN （默认值） 为派生自 _D3D_texture 该基础格式，此模板的 value_type 的格式。 提供的格式必须与 _D3D_texture 基础格式兼容。  
  
### <a name="return-value"></a>返回值  
 使用提供的 D3D 纹理纹理。  
  
##  <a name="msad4"></a>msad4  
 将 4 字节的引用值和一个 8 字节源值进行比较，并累积 4 总和向量。 每个总和对应于掩蔽绝对区别不同的字节的对齐方式的引用值，并在源值的总和。  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Reference`  
 一个 uint 值为 4 个字节的引用数组  
  
 `_Source`  
 源数组的两个 uint 值的向量中的 8 个字节。  
  
 `_Accum`  
 4 个值的要添加到屏蔽绝对区别不同的字节对齐方式的引用值，并在源值的总和向量。  
  
### <a name="return-value"></a>返回值  
 返回一个向量 4 的总和。 每个总和对应于掩蔽绝对区别不同的字节的对齐方式的引用值，并在源值的总和。  

## <a name="requirements"></a>惠?  
 **标头：** amp_graphics.h  
  
 **Namespace:** Concurrency::graphics::direct3d 

## <a name="see-also"></a>请参阅  
 [Concurrency::graphics::direct3d 命名空间](concurrency-graphics-direct3d-namespace.md)
