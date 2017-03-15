---
title: "Concurrency::graphics::direct3d 命名空间函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: aa7e91237eaa9ced297e2c5748359c23bb436df8
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空间函数
||||  
|-|-|-|  
|[get_sampler 函数](#get_sampler)|[get_texture 函数](#get_texture)|[make_sampler 函数](#make_sampler)|  
|[make_texture 函数](#make_texture)|[msad4 函数](#msad4)|  
  
##  <a name="a-namegetsamplera--getsampler-function"></a><a name="get_sampler"></a>get_sampler 函数  
 获取给定加速器的 D3D 采样器状态接口查看一个表示指定的采样器对象。  
  
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
 IUnknown 接口指针表示的给定的采样器的 D3D 采样器状态相对应。  
  
##  <a name="a-namegettexturea--gettexture-function"></a><a name="get_texture"></a>get_texture 函数  
 获取基础指定的 Direct3D 纹理接口[纹理](texture-class.md)对象。  
  
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
  
##  <a name="a-namemakesamplera--makesampler-function"></a><a name="make_sampler"></a>make_sampler 函数  
 从 D3D 采样器状态的接口指针创建一个示例。  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_D3D_sampler`  
 D3D 采样器状态，以便创建的采样器从 IUnknown 接口指针。  
  
### <a name="return-value"></a>返回值  
 采样器表示提供的 D3D 采样器状态。  
  
##  <a name="a-namemaketexturea--maketexture-function"></a><a name="make_texture"></a>make_texture 函数  
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
 纹理中元素的类型。  
  
 `_Rank`  
 纹理的秩。  
  
 `_Av`  
 纹理是要创建 D3D 快捷键视图。  
  
 `_D3D_texture`  
 若要创建从纹理的 D3D 纹理的 IUnknown 接口指针。  
  
 `_View_format`  
 要用于创建从此纹理视图的 DXGI 格式。 将传递 DXGI_FORMAT_UNKNOWN （默认值） 从 _D3D_texture 的基本格式和此模板 value_type 派生格式。 提供的格式必须与 _D3D_texture 基础格式兼容。  
  
### <a name="return-value"></a>返回值  
 使用提供的 D3D 纹理纹理。  
  
##  <a name="a-namemsad4a--msad4-function"></a><a name="msad4"></a>msad4 函数  
 将 4 字节引用值和一个 8 字节的源值进行比较，并累积 4 总和向量。 每个总和对应于不同的字节对齐方式的引用值，并在源值之间的绝对差的掩码总和。  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Reference`  
 引用数组的一个 uint 值为 4 个字节  
  
 `_Source`  
 源向量的两个 uint 值中的 8 字节的数组。  
  
 `_Accum`  
 4 个值添加到不同的字节对齐方式的引用值，并在源值之间的绝对差的掩码总和向量。  
  
### <a name="return-value"></a>返回值  
 返回一个向量 4 总和。 每个总和对应于不同的字节对齐方式的引用值，并在源值之间的绝对差的掩码总和。  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency::graphics::direct3d Namespace](concurrency-graphics-direct3d-namespace.md)

