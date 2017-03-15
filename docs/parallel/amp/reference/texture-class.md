---
title: "texture 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::texture
dev_langs:
- C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: aafb23ac4d366baed37f1cf667984253160af9c3
ms.lasthandoff: 02/24/2017

---
# <a name="texture-class"></a>texture 类
纹理是一种数据聚合的`accelerator_view`扩展盘区域中。 它是变量，一个用于扩展盘区域中的每个元素的集合。 每个变量可保存到 c + + 基元类型相对应的值 ( `unsigned int`， `int`， `float`， `double`)，为标量类型 ( `norm`，或`unorm`)，或短的矢量类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class texture;  
```  
  
#### <a name="parameters"></a>参数  
 `value_type`  
 纹理中元素的类型。  
  
 `_Rank`  
 纹理的秩。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`scalar_type`|标量类型。|  
|`value_type`|值类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[纹理构造函数](#ctor)|初始化 `texture` 类的新实例。|  
|[~ texture 析构函数](#ctor)|销毁`texture`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[copy_to 方法](#copy_to)|副本`texture`对象传递给目标进行配置后的深层副本。|  
|[数据的方法](#data)|返回一个 CPU 指向此纹理的原始数据。|  
|[get 方法](#get)|返回指定索引处的元素的值。|  
|[get_associated_accelerator_view 方法](#get_associated_accelerator_view)|返回[accelerator_view](accelerator-view-class.md) ，它是为要复制到此纹理的首选攻击目标。|  
|[get_depth_pitch 方法](#get_depth_pitch)|返回临时在 CPU 上的纹理 3D 中每个深度扇区之间的字节数。|  
|[get_row_pitch 方法](#get_row_pitch)|返回字节的数之间 2D 或 3D 临时在 CPU 上的纹理中的每一行。|  
|[set 方法](#set)|设置指定索引处的元素的值。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator （) 运算符](#operator_call)|返回由参数指定的元素值。|  
|[operator [] 运算符](#operator_at)|返回位于指定索引处的元素。|  
|[运算符 = 运算符](#operator_eq)|将复制指定[纹理](texture-class.md)对象传递给它。|  
  
### <a name="public-constants"></a>公共常量  
  
|名称|说明|  
|----------|-----------------|  
|[rank 常量](#rank)|获取的秩`texture`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[associated_accelerator_view 数据成员](#associated_accelerator_view)|获取[accelerator_view](accelerator-view-class.md) ，它是为要复制到此纹理的首选攻击目标。|  
|[depth_pitch 数据成员](#depth_pitch)|获取在 CPU 上 3D 临时纹理中每个深度扇区之间的字节数。|  
|[row_pitch 数据成员](#row_pitch)|获取二维或三维中的每一行之间的字节数的临时在 CPU 上的纹理。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_graphics.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="a-namedtora-texture"></a><a name="dtor"></a>~ 纹理 

 销毁`texture`对象。  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="a-nameassociatedacceleratorviewa-associatedacceleratorview"></a><a name="associated_accelerator_view"></a>associated_accelerator_view 

 获取[accelerator_view](accelerator-view-class.md) ，它是为要复制到此纹理的首选攻击目标。  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="a-namecopytoa-copyto"></a><a name="copy_to"></a>copy_to 

 副本`texture`对象传递给目标进行配置后的深层副本。  
  
```  
void copy_to(
    texture& _Dest) const;

 
 
void copy_to(
    writeonly_texture_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Dest`  
 要将复制到的对象。  
  
 `_Rank`  
 纹理的秩。  
  
 `value_type`  
 纹理中元素的类型。  
  
##  <a name="a-namedataa-data"></a><a name="data"></a>数据 

 返回一个 CPU 指向此纹理的原始数据。  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 指向纹理的原始数据的指针。  
  
##  <a name="a-namedepthpitcha-depthpitch"></a><a name="depth_pitch"></a>depth_pitch 

 获取在 CPU 上 3D 临时纹理中每个深度扇区之间的字节数。  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="a-namegeta-get"></a><a name="get"></a>获取 

 返回指定索引处的元素的值。  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 元素的索引。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的元素的值。  
  
##  <a name="a-namegetassociatedacceleratorviewa-getassociatedacceleratorview"></a><a name="get_associated_accelerator_view"></a>get_associated_accelerator_view 

 返回是此纹理复制到首选的目标 accelerator_view。  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 [Accelerator_view](accelerator-view-class.md) ，它是为要复制到此纹理的首选攻击目标。  
  
##  <a name="a-namegetdepthpitcha-getdepthpitch"></a><a name="get_depth_pitch"></a>get_depth_pitch 

 返回临时在 CPU 上的纹理 3D 中每个深度扇区之间的字节数。  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 临时在 CPU 上的纹理 3D 中每个深度扇区之间的字节数。  
  
##  <a name="a-namegetrowpitcha-getrowpitch"></a><a name="get_row_pitch"></a>get_row_pitch 

 返回字节的数或每一行中 3 维临时纹理深度扇区之间的二维临时纹理中的每一行。  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 每一行中 3 维临时纹理深度扇区之间或 2 维临时纹理中的每一行之间的字节数。  
  
##  <a name="a-nameoperatorcalla-operator"></a><a name="operator_call"></a>operator （) 

 返回由参数指定的元素值。  
  
```  
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator() (
    int _I0) const restrict(amp);

 
const value_type operator() (
    int _I0,  
    int _I1) const restrict(amp);

 
const value_type operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 索引。  
  
 `_I0`  
 索引的最有效的组件。  
  
 `_I1`  
 索引的下一步-到-最高有效的组件。  
  
 `_I2`  
 索引的最重要的组件。  
  
 `_Rank`  
 索引的级别。  
  
### <a name="return-value"></a>返回值  
 在由参数指定的元素值。  
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

 返回位于指定索引处的元素。  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 索引。  
  
 `_I0`  
 索引。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的元素。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

 将复制指定[纹理](texture-class.md)对象传递给它。  
  
```  
texture& operator= (
    const texture& _Other);

 
texture& operator= (
    texture<value_type, _Rank>&& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `texture`从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 参考这`texture`对象。  
  
##  <a name="a-nameranka-rank"></a><a name="rank"></a>排名 

 获取的秩`texture`对象。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namerowpitcha-rowpitch"></a><a name="row_pitch"></a>row_pitch 

 获取二维或三维中的每一行之间的字节数的临时在 CPU 上的纹理。  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>设置 

 设置指定索引处的元素的值。  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 元素的索引。  
  
 `_Rank`  
 索引的级别。  
  
 `value`  
 该元素的新值。  
  
##  <a name="a-namectora-texture"></a><a name="ctor"></a>纹理 

 初始化 `texture` 类的新实例。  
  
```  
texture(
    const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

 
texture(
    int _E0) restrict(cpu);

 
texture(
    int _E0,  
    int _E1) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    const Concurrency::extent<_Rank>& _Ext, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1,  
    int _E2, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    const Concurrency::extent<_Rank>& _Ext, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1,  
    int _E2, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;  
 
texture(
    int _E0,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av)  ;  
 
texture(
    int _E0,  
    int _E1,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av)  ;  
 
texture(
    int _E0,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    const texture& _Src,  
    const Concurrency::accelerator_view& _Acc_view);

 
texture(
    texture&& _Other);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,   
    unsigned int _Bits_per_scalar_element,   
    const Concurrency::accelerator_view& _Av);

 
texture(
    const texture& _Src);
```  
  
### <a name="parameters"></a>参数  
 `_Acc_view`  
 [Accelerator_view](accelerator-view-class.md)指定纹理的位置。  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md)指定纹理的位置。  
  
 `_Associated_av`  
 指定的首选的目标 accelerator_view 复制到或从该纹理。  
  
 `_Bits_per_scalar_element`  
 每个基础标量类型的纹理中每个标量元素的比特数。 一般情况下，受支持的值是 8、 16、 32 和 64。 如果指定 0，比特数是基础 scalar_type 相同。 64 无效，仅对于基于双的纹理。  
  
 `_Ext`  
 纹理的每个维度中的范围。  
  
 `_E0`  
 纹理的最重要的组件。  
  
 `_E1`  
 下一步-到-最高有效组件的纹理。  
  
 `_E2`  
 纹理程度最不重要组件。  
  
 `_Input_iterator`  
 输入 interator 的类型。  
  
 `_Mipmap_levels`  
 在基础纹理 mipmap 级别数。 如果指定 0，则纹理将具有指定的范围的可能的最小大小下的 mipmap 级别的完整范围。  
  
 `_Rank`  
 此扩展盘区的秩。  
  
 `_Source`  
 指向主机缓冲区的指针。  
  
 `_Src`  
 为要复制的纹理。  
  
 `_Src_byte_size`  
 源缓冲区中的字节数。  
  
 `_Src_first`  
 到源容器开始迭代器。  
  
 `_Src_last`  
 到源容器的迭代器结束。  
  
 `_Other`  
 其他数据源。  
  
 `_Rank`  
 部分中的排名。  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency:: graphics Namespace](concurrency-graphics-namespace.md)

