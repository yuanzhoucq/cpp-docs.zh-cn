---
title: "array_view 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
dev_langs: C++
helpviewer_keywords: array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 467d806203687610265d1b199e01295f93557081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="arrayview-class"></a>array_view 类
表示 N 维视图对保存在另一个容器中的数据。  
  
## <a name="syntax"></a>语法  
  
```  
template <
    typename value_type,  
    int _Rank = 1  
>  
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
 
template <
    typename value_type,  
    int _Rank  
>  
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
```  
  
#### <a name="parameters"></a>参数  
 `value_type`  
 中的元素的数据类型`array_view`对象。  
  
 `_Rank`  
 秩`array_view`对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[array_view 构造函数](#ctor)|初始化 `array_view` 类的新实例。 没有默认构造函数没有`array<T,N>`。 所有构造函数被限制为仅在 CPU 上运行，并且在 Direct3D 目标上，无法执行。|  
|[~ array_view 析构函数](#ctor)|销毁`array_view`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[copy_to](#copy_to)|内容复制`array_view`到通过调用指定的目标对象`copy(*this, dest)`。|  
|[data](#data)|将指针返回到原始数据的`array_view`。|  
|[discard_data](#discard_data)|放弃基础此视图的当前数据。|  
|[get_extent](#get_extent)|返回 array_view 对象的范围对象。|  
|[get_ref](#get_ref)|返回对索引的元素的引用。|  
|[get_source_accelerator_view](#get_source_accelerator_view)|返回[accelerator_view](accelerator-view-class.md)其中的数据源的`array_view`所在。|  
|[刷新](#refresh)|通知`array_view`已在外部修改其绑定的内存的对象`array_view`接口。 调用此方法将呈现所有缓存的信息过时。|  
|[reinterpret_as](#reinterpret_as)|返回包含中的所有元素的一维数组`array_view`对象。|  
|[section](#section)|返回的子部分的`array_view`对象位于指定的 origin 和 （可选），具有指定的范围。|  
|[synchronize](#synchronize)|同步对做任何修改`array_view`回其源数据的对象。|  
|[synchronize_async](#synchronize_async)|以异步方式同步对做任何修改`array_view`回其源数据的对象。|  
|[synchronize_to](#synchronize_to)|同步对做任何修改`array_view`到指定的对象[accelerator_view](accelerator-view-class.md)。|  
|[synchronize_to_async](#synchronize_to_async)|以异步方式同步对做任何修改`array_view`到指定的对象[accelerator_view](accelerator-view-class.md)。|  
|[view_as](#view_as)|生成`array_view`的不同排名使用此对象`array_view`对象的数据。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator （)](#operator_call)|返回由参数或参数指定的元素的值。|  
|[operator]](#operator_at)|返回由参数指定的元素。|  
|[operator=](#operator_eq)|将指定的内容复制`array_view`到此对象。|  
  
### <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|[rank 常量](#rank)|将存储的秩`array_view`对象。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[extent](#extent)|获取定义 `extent` 对象形状的 `array_view` 对象。|  
|[source_accelerator_view](#source_accelerator_view)|获取[accelerator_view](accelerator-view-class.md)其中的数据源的`array_view`所在|  
|[value_type](#value_type)|值类型`array_view`和绑定的数组。|  
  
## <a name="remarks"></a>备注  
 `array_view`类表示中包含的数据的视图[数组](array-class.md)对象或子部分的`array`对象。  
  
 你可以访问`array_view`对象，其中源数据的位置 （本地） 或不同的快捷键或一致性域上 （远程）。 远程访问对象时，视图复制和根据需要缓存。 除了自动缓存的效果`array_view`对象具有相似的性能配置文件`array`对象。 通过视图访问数据时对小的性能产生负面影响。  
  
 有三个远程使用方案：  
  
-   通过传递到系统内存指针视图[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)加速器并且在快捷键上访问。  
  
-   通过传递到数组的加速器上位于视图`parallel_for_each`调用另一个快捷键和存在访问。  
  
-   在 CPU 上访问到数组的加速器上位于某视图。  
  
 在任一这些方案，被引用的视图复制由运行时到远程位置，如果修改由调用的`array_view`对象，将复制回本地位置。 运行时可能会优化复制回更改的过程、 可能复制仅更改的元素，或可能也复制不变的部分。 重叠`array_view`上一个数据源的对象不能保证维护在远程位置的引用完整性。  
  
 你必须同步任何多线程的访问相同的数据源。  
  
 运行时发出有关中的数据缓存的以下保证`array_view`对象：  
  
-   所有正确同步访问`array`对象和`array_view`对象在其上的按编程顺序遵循串行发生-之前关系。  
  
-   对重叠的所有正确同步访问`array_view`对象在单个上相同的加速器上`array`对象是通过使用别名`array`对象。 它们引入总共发生-之前遵从编程顺序的关系。 并不存在缓存。 如果`array_view`对象上不同的快捷键一起执行、 访问的顺序是未定义，创建了争用条件。  
  
 当你创建`array_view`对象在系统内存中，使用指针必须更改视图`array_view`对象只能通过`array_view`指针。 或者，你必须调用`refresh()`之一上`array_view`对象附加到系统指针，如果基础的本机内存而不是通过直接更改`array_view`对象。  
  
 以上任一操作通知`array_view`对象的基础的本机内存已更改，位于的加速器任何副本已过时。 如果你遵循这些指导原则，基于指针的视图均与所提供的数据并行数组的视图相同。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Array_view_shape`  
  
 `_Array_view_base`  
  
 `array_view`  
  
## <a name="requirements"></a>惠?  
 **标头：** amp.h  
  
 **命名空间：** 并发  
  
##  <a name="dtor"></a>~ array_view 

 销毁`array_view`对象。  
  
```  
~array_view()restrict(amp,cpu);
```  
  
##  <a name="ctor"></a>array_view 

 初始化 `array_view` 类的新实例。  
  
```  
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view& _Other)restrict(amp,cpu);

 
explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    _Container& _Src) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _Container& _Src);

 
explicit array_view(
    int _E0,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const _Container& _Src) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    const _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const _Container& _Src);

 
array_view(
    int _E0,  
    const value_type* _Src)restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    const value_type* _Src) restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const value_type* _Src) restrict(amp,cpu);

 
```  
  
### <a name="parameters"></a>参数  
 `_Arr_type`  
 从其提供数据的 C 样式数组元素类型。  
  
 `_Container`  
 一个模板参数，必须指定一个支持的线性容器`data()`和`size()`成员。  
  
 `_E0`  
 本部分范围的最重要的组件。  
  
 `_E1`  
 本部分范围的下一步-到-最高有效组件。  
  
 `_E2`  
 本部分范围的最低有效组件。  
  
 `_Extent`  
 中的每个维度的范围`array_view`。  
  
 `_Other`  
 类型的对象`array_view<T,N>`从其初始化新`array_view`。  
  
 `_Size`  
 从其提供数据的 C 样式数组的大小。  
  
 `_Src`  
 指向源数据将复制到新数组的指针。  
  
##  <a name="copy_to"></a>copy_to 

 内容复制`array_view`对象与通过调用指定的目标对象`copy(*this, dest)`。  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Dest`  
 要将复制到的对象。  
  
##  <a name="data"></a>数据 

 将指针返回到原始数据的`array_view`。  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>返回值  
 指向 `array_view` 原始数据的指针。  
  
##  <a name="discard_data"></a>discard_data 

 放弃基础此视图的当前数据。 这是用于避免将视图的当前内容复制到目标的运行时优化提示`accelerator_view`访问，并且其使用建议如果不需要的现有内容。 此方法是一个无操作时在 restrict(amp) 上下文中使用  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="extent"></a>范围 

 获取定义 `extent` 对象形状的 `array_view` 对象。  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_extent"></a>get_extent 

 返回[范围](extent-class.md)对象`array_view`对象。  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>返回值  
 `extent` 对象的  `array_view` 对象。  
  
##  <a name="get_ref"></a>get_ref 

 获取对由 _Index 编制索引的元素的引用。 与其他索引运算符用于访问在 CPU 上的 array_view，此方法不会隐式同步到 CPU 的此 array_view 的内容。 访问远程位置上的 array_view 或执行复制操作涉及此 array_view 后用户有责任显式调用此方法之前同步到 CPU array_view。 如果不这样做会导致未定义的行为。  
  
```  
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 索引。  
  
### <a name="return-value"></a>返回值  
 按 _Index 建立索引的元素引用  
  
##  <a name="get_source_accelerator_view"></a>get_source_accelerator_view 

 返回 accelerator_view array_view 的数据源所在的位置。 此 API 如果 array_view 没有数据源，将引发 runtime_exception  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="operator_call"></a>operator （) 

 返回由参数或参数指定的元素的值。  
  
```  
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 元素的位置。  
  
 `_I0`  
 中的第一个维度的索引。  
  
 `_I1`  
 第二个维度中的索引。  
  
 `_I2`  
 第三个维中的索引。  
  
 `_I`  
 元素的位置。  
  
### <a name="return-value"></a>返回值  
 由参数或参数的指定元素的值。  
  
##  <a name="operator_at"></a>operator] 

 返回由参数指定的元素。  
  
```  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

 
value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 索引。  
  
 `_I`  
 索引。  
  
### <a name="return-value"></a>返回值  
 元素的索引处的值或`array_view`投影到最高有效维度。  
  
##  <a name="operator_eq"></a>运算符 = 

 将指定的内容复制`array_view`于此对象。  
  
```  
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

 
array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `array_view`从中进行复制的对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`array_view`对象。  
  
##  <a name="rank"></a>级别 

 将存储的秩`array_view`对象。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="refresh"></a>刷新 

 通知`array_view`已在外部修改其绑定的内存的对象`array_view`接口。 调用此方法将呈现所有缓存的信息过时。  
  
```  
void refresh() const restrict(cpu);
```  
## <a name="reinterpret_as"></a>reinterpret_as 

重新解释通过一维 array_view，其作为一个选项可以具有不同的值类型比源 array_view array_view。  
  
### <a name="syntax"></a>语法  
  
```  
template <  
    typename _Value_type2  
>  
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
  
template <  
    typename _Value_type2  
>  
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Value_type2`  
 新的数据类型`array_view`对象。  
  
### <a name="return-value"></a>返回值  
 `array_view`对象或 const`array_view`对象基于这`array_view`，与从转换的元素类型`T`到`_Value_type2`，并且从减少排名*N*为 1。  
  
### <a name="remarks"></a>备注  
 有时会很方便以线性、 一维数组，其可能具有不同的值类型比源数组形式查看多维数组。 你可以实现此目的在`array_view`使用此方法。  
  
**警告**Reinterpeting array_view 对象使用不同的值类型是一个潜在的不安全的操作。 应谨慎使用此功能。  
  
 以下是一个示例：  
  
```cpp  
struct RGB { float r; float g; float b; };  
  
array<RGB,3>  a = ...;   
array_view<float,1> v = a.reinterpret_as<float>();   
  
assert(v.extent == 3*a.extent);  
```  
    
##  <a name="section"></a>部分 

 返回的子部分的`array_view`对象位于指定的 origin 和 （可选），具有指定的范围。  
  
```  
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _E0) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _I2,  
    int _E0,  
    int _E1,  
    int _E2) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_E0`  
 本部分范围的最重要的组件。  
  
 `_E1`  
 本部分范围的下一步-到-最高有效组件。  
  
 `_E2`  
 本部分范围的最低有效组件。  
  
 `_Ext`  
 [范围](extent-class.md)指定部分的范围的对象。 原点为 0。  
  
 `_Idx`  
 [索引](index-class.md)对象，它指定原点的位置。 子部分是此盘区的其余部分。  
  
 `_I0`  
 本部分的原点最重要的组件。  
  
 `_I1`  
 本部分的原点下一步-到-最高有效组件。  
  
 `_I2`  
 本部分的原点最低有效组件。  
  
 `_Rank`  
 部分中的秩。  
  
 `_Section_extent`  
 [范围](extent-class.md)指定部分的范围的对象。  
  
 `_Section_origin`  
 [索引](index-class.md)对象，它指定原点的位置。  
  
### <a name="return-value"></a>返回值  
 子部分的`array_view`对象位于指定的 origin 和 （可选），具有指定的范围。 当仅`index`指定对象、 小节包含关联的范围中具有大于中的元素的索引的索引的所有元素`index`对象。  
  
##  <a name="source_accelerator_view"></a>source_accelerator_view 

 获取与此 array_view 源 accelerator_view。  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="synchronize"></a>同步 

 同步对做任何修改`array_view`回其源数据的对象。  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Access_type`  
 所要的[access_type](concurrency-namespace-enums-amp.md#access_type)在目标上[accelerator_view](accelerator-view-class.md)。 此参数具有默认值为`access_type_read`。  
  
##  <a name="synchronize_async"></a>synchronize_async 

 以异步方式同步对做任何修改`array_view`回其源数据的对象。  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Access_type`  
 所要的[access_type](concurrency-namespace-enums-amp.md#access_type)在目标上[accelerator_view](accelerator-view-class.md)。 此参数具有默认值为`access_type_read`。  
  
### <a name="return-value"></a>返回值  
 等待要完成的操作将基于未来。  
  
##  <a name="synchronize_to"></a>synchronize_to 

 同步对此 array_view 到指定的 accelerator_view 做任何修改。  
  
```  
void synchronize_to(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Accl_view`  
 要同步到目标 accelerator_view。  
  
 `_Access_type`  
 在目标 accelerator_view 上所需的 access_type。 此参数的默认值为 access_type_read。  
  
##  <a name="synchronize_to_async"></a>synchronize_to_async 

 以异步方式将同步到指定的 accelerator_view 此 array_view 对做任何修改。  
  
```  
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Accl_view`  
 要同步到目标 accelerator_view。  
  
 `_Access_type`  
 在目标 accelerator_view 上所需的 access_type。 此参数的默认值为 access_type_read。  
  
### <a name="return-value"></a>返回值  
 等待要完成的操作将基于未来。  
  
##  <a name="value_type"></a>value_type 

 Array_view 和绑定的数组的值类型。  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="view_as"></a>view_as 

 重新解释这`array_view`作为`array_view`的不同级别。  
  
```  
template <
    int _New_rank  
>  
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

 
template <
    int _New_rank  
>  
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_New_rank`  
 新的秩`array_view`对象。  
  
 `_View_extent`  
 重新调整`extent`。  
  
 `value_type`  
 在这两个原始元素的数据类型[数组](array-class.md)对象并返回`array_view`对象。  
  
### <a name="return-value"></a>返回值  
 `array_view`构造对象。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
