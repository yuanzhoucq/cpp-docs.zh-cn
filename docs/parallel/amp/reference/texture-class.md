---
title: "纹理类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 7aee3b5135e486474132f455ddceaf86980d3be9
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="texture-class"></a>texture 类
纹理是一种数据聚合上`accelerator_view`范围域中。 它是变量，一个用于扩展盘区域中的每个元素的集合。 每个变量包含 c + + 基元类型相对应的值 ( `unsigned int`， `int`， `float`， `double`)，为标量类型 ( `norm`，或`unorm`)，或短矢量类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <typename value_type,  int _Rank>  
class texture;  
```  
  
#### <a name="parameters"></a>参数  
 `value_type`  
 纹理中的元素的类型。  
  
 `_Rank`  
 纹理的秩。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`scalar_type`|标量类型。|  
|`value_type`|值类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[纹理构造函数](#ctor)|初始化 `texture` 类的新实例。|  
|[~ texture 析构函数](#ctor)|销毁`texture`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[copy_to](#copy_to)|副本`texture`对象到目标，通过执行操作的深层副本。|  
|[data](#data)|CPU 指针返回到此纹理的原始数据。|  
|[get](#get)|返回指定索引处的元素的值。|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|返回[accelerator_view](accelerator-view-class.md) ，它是要复制到此纹理的首选的目标。|  
|[get_depth_pitch](#get_depth_pitch)|在以三维形式暂存纹理在 CPU 上的每个深度扇区之间返回字节的数。|  
|[get_row_pitch](#get_row_pitch)|返回字节的数之间的二维或三维暂存在 CPU 上的纹理中的每一行。|  
|[set](#set)|设置指定索引处的元素的值。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator （)](#operator_call)|返回由参数指定的元素值。|  
|[operator]](#operator_at)|返回位于指定索引处的元素。|  
|[operator=](#operator_eq)|将复制指定[纹理](texture-class.md)于此对象。|  
  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[rank 常量](#rank)|获取的秩`texture`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[associated_accelerator_view](#associated_accelerator_view)|获取[accelerator_view](accelerator-view-class.md) ，它是要复制到此纹理的首选的目标。|  
|[depth_pitch](#depth_pitch)|获取在 CPU 上过渡三维纹理中每个深度扇区之间的字节数。|  
|[row_pitch](#row_pitch)|获取二维或三维中的每一行之间的字节数暂存在 CPU 上的纹理。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_graphics.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="dtor"></a>~ 纹理 

 销毁`texture`对象。  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="associated_accelerator_view"></a>associated_accelerator_view 

 获取[accelerator_view](accelerator-view-class.md) ，它是要复制到此纹理的首选的目标。  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="copy_to"></a>copy_to 

 副本`texture`对象到目标，通过执行操作的深层副本。  
  
```  
void copy_to(texture& _Dest) const; 
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const; 
```  
  
### <a name="parameters"></a>参数  
 `_Dest`  
 要将复制到的对象。  
  
 `_Rank`  
 纹理的秩。  
  
 `value_type`  
 纹理中的元素的类型。  
  
##  <a name="data"></a>数据 

 CPU 指针返回到此纹理的原始数据。  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 指向原始的纹理数据的指针。  
  
##  <a name="depth_pitch"></a>depth_pitch 

 获取在 CPU 上过渡三维纹理中每个深度扇区之间的字节数。  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="get"></a>获取 

 返回指定索引处的元素的值。  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 元素的索引。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的元素的值。  
  
##  <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view 

 返回是要复制到此纹理的首选的目标 accelerator_view。  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 [Accelerator_view](accelerator-view-class.md) ，它是要复制到此纹理的首选的目标。  
  
##  <a name="get_depth_pitch"></a>get_depth_pitch 

 在以三维形式暂存纹理在 CPU 上的每个深度扇区之间返回字节的数。  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 在以三维形式暂存纹理在 CPU 上的每个深度扇区之间的字节数。  
  
##  <a name="get_row_pitch"></a>get_row_pitch 

 返回字节的数之间的 2 维的过渡纹理中的每一行或三维过渡纹理中的深度切片的各行之间。  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
 之间的 2 维的过渡纹理中的每一行或三维过渡纹理中的深度切片的各行之间的字节数。  
  
##  <a name="operator_call"></a>operator （) 

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
 索引的最高有效组件。  
  
 `_I1`  
 索引的下一步-到-最高有效组件。  
  
 `_I2`  
 索引的最低有效组件。  
  
 `_Rank`  
 索引的秩。  
  
### <a name="return-value"></a>返回值  
 指定的参数的元素值。  
  
##  <a name="operator_at"></a>operator] 

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
  
##  <a name="operator_eq"></a>运算符 = 

 将复制指定[纹理](texture-class.md)于此对象。  
  
```  
texture& operator= (
    const texture& _Other);

 
texture& operator= (
    texture<value_type, _Rank>&& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `texture`从中进行复制的对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`texture`对象。  
  
##  <a name="rank"></a>级别 

 获取的秩`texture`对象。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="row_pitch"></a>row_pitch 

 获取二维或三维中的每一行之间的字节数暂存在 CPU 上的纹理。  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="set"></a>设置 

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
 索引的秩。  
  
 `value`  
 该元素的新值。  
  
##  <a name="ctor"></a>纹理 

 初始化 `texture` 类的新实例。  
  
```  
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);
 
texture(int _E0) restrict(cpu);
 
texture(int _E0, int _E1) restrict(cpu);
 
texture(int _E0, int _E1, int _E2) restrict(cpu);
 
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


template<typename _Input_iterator>  
texture(
    const Concurrency::extent<_Rank>& _Ext, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1,  
    int _E2, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    const Concurrency::extent<_Rank>& _Ext, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1,  
    int _E2, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
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
 [Accelerator_view](accelerator-view-class.md) ，它指定的纹理的位置。  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md) ，它指定的纹理的位置。  
  
 `_Associated_av`  
 指定的首选的目标 accelerator_view 将复制到数据库或从此纹理。  
  
 `_Bits_per_scalar_element`  
 每个基础标量类型的纹理中每个标量元素的比特数。 通常情况下，支持的值是 8、 16、 32 和 64。 如果指定 0，比特数是基础 scalar_type 相同。 仅在 64 时有效的双基于纹理。  
  
 `_Ext`  
 纹理的各个维度中的范围。  
  
 `_E0`  
 纹理的最重要的组件。  
  
 `_E1`  
 纹理下一步-到-最高有效组件。  
  
 `_E2`  
 作用域的纹理的最低有效组件。  
  
 `_Input_iterator`  
 输入 interator 的类型。  
  
 `_Mipmap_levels`  
 在基础纹理 mipmap 级别数。 如果指定 0，则纹理将具有的完整范围的指定范围的可能的最小大小下的 mipmap 级别。  
  
 `_Rank`  
 对此盘区进行分级。  
  
 `_Source`  
 指向主机缓冲区的指针。  
  
 `_Src`  
 为要复制的纹理。  
  
 `_Src_byte_size`  
 源缓冲区中的字节数。  
  
 `_Src_first`  
 到源容器经过开头的迭代器。  
  
 `_Src_last`  
 到源容器结束迭代器。  
  
 `_Other`  
 其他数据源。  
  
 `_Rank`  
 部分中的秩。  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)

