---
title: "array_view 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::array_view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array_view 类"
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# array_view 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示对另一个容器中保存的数据的 N 维视图。  
  
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
 中的元素的数据类型 `array_view` 对象。  
  
 `_Rank`  
 秩 `array_view` 对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[array_view:: array_view 构造函数](#array_view__array_view_constructor)|初始化 `array_view` 类的新实例。 没有默认构造函数，为 `array<T,N>`。 所有构造函数被限制为仅在 CPU 上运行，并不能在 Direct3D 目标上执行。|  
|[array_view:: ~ array_view 析构函数](#array_view___dtorarray_view_destructor)|销毁 `array_view` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[array_view:: copy_to 方法](#array_view__copy_to_method)|中的内容复制 `array_view` 对象传递给通过调用指定的目标 `copy(*this, dest)`。|  
|[array_view:: data 方法](#array_view__data_method)|将指针返回到原始数据的 `array_view`。|  
|[array_view:: discard_data 方法](#array_view__discard_data_method)|放弃此视图的基础的当前数据。|  
|[array_view:: get_extent 方法](#array_view__get_extent_method)|返回 array_view 对象的扩展盘区对象。|  
|[array_view:: get_ref 方法](#array_view__get_ref_method)|返回对索引的元素的引用。|  
|[array_view:: get_source_accelerator_view 方法](#array_view__get_source_accelerator_view_method)|返回 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 其中的数据源的 `array_view` 所在。|  
|[array_view:: refresh 方法](#array_view__refresh_method)|通知 `array_view` 对象已在外部修改其绑定的内存 `array_view` 接口。 对此方法的调用将呈现所有缓存的信息过期。|  
|[array_view:: reinterpret_as 方法](#array_view__reinterpret_as_method)|返回包含中的所有元素的一维数组 `array_view` 对象。|  
|[array_view:: section 方法](#array_view__section_method)|返回的子部分的 `array_view` 位于指定的 origin 和 （可选） 该的对象具有指定的范围。|  
|[array_view:: synchronize 方法](#array_view__synchronize_method)|同步对所做的任何修改 `array_view` 回其源数据的对象。|  
|[array_view:: synchronize_async 方法](#array_view__synchronize_async_method)|以异步方式同步对所做的任何修改 [array_view](../../../parallel/amp/reference/array-view-class.md) 回其源数据的对象。|  
|[array_view:: synchronize_to 方法](#array_view__synchronize_to_method)|同步对所做的任何修改 `array_view` 对象传递给指定 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。|  
|[array_view:: synchronize_to_async 方法](#array_view__synchronize_to_async_method)|以异步方式同步对所做的任何修改 `array_view` 对象传递给指定 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。|  
|[array_view:: view_as 方法](#array_view__view_as_method)|生成 `array_view` 的不同排名使用此对象 `array_view` 对象的数据。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[array_view::operator() 运算符](#array_view__operator___operator)|返回由参数或参数指定的元素的值。|  
|[array_view:: operator [] 运算符](#array_view__operator_at_operator)|返回由参数指定的元素。|  
|[array_view:: operator = 运算符](#array_view__operator_eq_operator)|将指定的内容复制 `array_view` 到此对象。|  
  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[array_view:: rank 常量](#array_view__rank_constant)|将存储的排名 `array_view` 对象。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[array_view:: extent 数据成员](#array_view__extent_data_member)|获取定义 `extent` 对象形状的 `array_view` 对象。|  
|[array_view:: source_accelerator_view 数据成员](#array_view__source_accelerator_view_data_member)|获取 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 其中的数据源的 `array_view` 所在|  
|[array_view:: value_type 数据成员](#array_view__value_type_data_member)|值类型 `array_view` 和绑定的数组。|  
  
## <a name="remarks"></a>备注  
  `array_view` 类表示中包含的数据视图 [数组](../../../parallel/amp/reference/array-class.md) 对象或子部分的 `array` 对象。  
  
 您可以访问 `array_view` 对象所在的源数据所在 （本地） 或不同的快捷键或一致性域上 （远程）。 如果远程访问这些对象，视图复制和根据需要缓存。 除了自动缓存的效果 `array_view` 对象有性能配置文件类似于 `array` 对象。 通过视图访问数据时对小的性能产生负面影响。  
  
 有三个远程使用方案︰  
  
-   通过传递到系统内存指针的视图 [parallel_for_each](concurrency%20namespace%20functions.md#parallel_for_each) 号召加速器和在快捷键上访问。  
  
-   通过传递到位于加速器数组视图 `parallel_for_each` 到另一个 accelerator 调用并那里访问。  
  
-   在 CPU 上访问到数组位于加速器的视图。  
  
 在这些方案中的任何一个，被引用的视图将会复制由运行时到远程位置，如果修改由调用的 `array_view` 对象，请复制回本地位置。 运行时可能优化复制返回更改的过程，可能会复制仅更改的元素，或可能还的不变的部分复制。 重叠 `array_view` 不能保证一个数据源上的对象来维护引用完整性在远程位置。  
  
 您必须同步对同一数据源的任何多线程的访问。  
  
 运行库对缓存中的数据有关的以下保证 `array_view` 对象︰  
  
-   对所有正确同步访问 `array` 对象和一个 `array_view` 对象对其按编程顺序遵循串行发生-之前关系。  
  
-   对重叠的所有正确同步访问 `array_view` 对象相同的单个加速器 `array` 对象是通过使用别名 `array` 对象。 它们会引入总共发生-之前服从程序顺序的关系。 并不存在缓存。 如果 `array_view` 对象上不同加速器一起执行、 访问的顺序是未定义，创建一个争用条件。  
  
 当您创建 `array_view` 对象在系统内存中，使用一个指针，则必须更改视图 `array_view` 对象只能通过 `array_view` 指针。 或者，您必须调用 `refresh()` 之一上 `array_view` 对象附加到系统指针，如果基础本机内存而不是通过直接更改 `array_view` 对象。  
  
 以上任一操作通知 `array_view` 对象，将更改基础本机内存并且位于加速器任何副本已过时。 如果您遵循这些准则，基于指针的视图是所提供的视图的数据并行数组相同的。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_Array_view_shape`  
  
 `_Array_view_base`  
  
 `array_view`  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namearrayviewdtorarrayviewdestructora-arrayviewarrayview-destructor"></a><a name="array_view___dtorarray_view_destructor"></a>  array_view:: ~ array_view 析构函数  
 销毁 [array_view](../../../parallel/amp/reference/array-view-class.md) 对象。  
  
```  
~array_view()restrict(amp,cpu);
```  
  
##  <a name="a-namearrayviewarrayviewconstructora-arrayviewarrayview-constructor"></a><a name="array_view__array_view_constructor"></a>  array_view:: array_view 构造函数  
 新实例初始化 [array_view](../../../parallel/amp/reference/array-view-class.md) 类。  
  
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
 必须指定支持的线性容器的模板参数 `data()` 和 `size()` 成员。  
  
 `_E0`  
 本部分范围的最重要的组件。  
  
 `_E1`  
 本部分范围的下一步-到-最高有效的组件。  
  
 `_E2`  
 本部分程度最不重要组件。  
  
 `_Extent`  
 每个维度中的此扩展盘区 `array_view`。  
  
 `_Other`  
 类型的对象 `array_view<T,N>` 从中初始化新 `array_view`。  
  
 `_Size`  
 从其提供数据的 C 样式数组的大小。  
  
 `_Src`  
 指向源数据将复制到新数组的指针。  
  
##  <a name="a-namearrayviewcopytomethoda-arrayviewcopyto-method"></a><a name="array_view__copy_to_method"></a>  array_view:: copy_to 方法  
 中的内容复制 [array_view](../../../parallel/amp/reference/array-view-class.md) 对象与指定的目标对象通过调用 `copy(*this, dest)`。  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Dest`  
 要将复制到的对象。  
  
##  <a name="a-namearrayviewdatamethoda-arrayviewdata-method"></a><a name="array_view__data_method"></a>  array_view:: data 方法  
 将指针返回到原始数据的 [array_view](../../../parallel/amp/reference/array-view-class.md)。  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>返回值  
 指向 `array_view` 原始数据的指针。  
  
##  <a name="a-namearrayviewdiscarddatamethoda-arrayviewdiscarddata-method"></a><a name="array_view__discard_data_method"></a>  array_view:: discard_data 方法  
 放弃此视图的基础的当前数据。 这是向运行时用来避免将视图的当前内容复制到目标的优化提示 `accelerator_view` 的访问，并且如果不需要的现有内容，建议使用它。 此方法不是执行任何操作 restrict （amp） 上下文中使用时  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="a-namearrayviewextentdatamembera-arrayviewextent-data-member"></a><a name="array_view__extent_data_member"></a>  array_view:: extent 数据成员  
 获取定义 `extent` 对象形状的 `array_view` 对象。  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="a-namearrayviewgetextentmethoda-arrayviewgetextent-method"></a><a name="array_view__get_extent_method"></a>  array_view:: get_extent 方法  
 返回 [扩展盘区](../../../parallel/amp/reference/extent-class-cpp-amp.md) 对象 [array_view](../../../parallel/amp/reference/array-view-class.md) 对象。  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>返回值  
 `extent` 对象的  `array_view` 对象。  
  
##  <a name="a-namearrayviewgetrefmethoda-arrayviewgetref-method"></a><a name="array_view__get_ref_method"></a>  array_view:: get_ref 方法  
 获取对由 _Index 索引的元素的引用。 与其他索引运算符用于访问在 CPU 上的 array_view，此方法不会隐式同步此 array_view 内容向 CPU。 访问远程位置上的 array_view 或执行复制操作涉及此 array_view 后用户有责任显式向 CPU array_view 在之前进行同步调用此方法。 如果不这样做会导致未定义的行为。  
  
```  
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 索引。  
  
### <a name="return-value"></a>返回值  
 按 _Index 建立索引的元素引用  
  
##  <a name="a-namearrayviewgetsourceacceleratorviewmethoda-arrayviewgetsourceacceleratorview-method"></a><a name="array_view__get_source_accelerator_view_method"></a>  array_view:: get_source_accelerator_view 方法  
 返回 accelerator_view array_view 的数据源所在的位置。 如果 array_view 不具有数据源，此 API 将引发 runtime_exception  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-namearrayviewoperatoroperatora-arrayviewoperator-operator"></a><a name="array_view__operator___operator"></a>  array_view::operator() 运算符  
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
 第一个维度中的索引。  
  
 `_I1`  
 第二个维度中的索引。  
  
 `_I2`  
 第三个维中的索引。  
  
 `_I`  
 元素的位置。  
  
### <a name="return-value"></a>返回值  
 由参数或参数指定的元素的值。  
  
##  <a name="a-namearrayviewoperatoratoperatora-arrayviewoperator-operator"></a><a name="array_view__operator_at_operator"></a>  array_view:: operator [] 运算符  
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
 中的索引处的元素的值或 `array_view` 投影到最高有效维度上。  
  
##  <a name="a-namearrayviewoperatoreqoperatora-arrayviewoperator-operator"></a><a name="array_view__operator_eq_operator"></a>  array_view:: operator = 运算符  
 将指定的内容复制 [array_view](../../../parallel/amp/reference/array-view-class.md) 对象传递给它。  
  
```  
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

 
array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
  `array_view` 从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 参考这 `array_view` 对象。  
  
##  <a name="a-namearrayviewrankconstanta-arrayviewrank-constant"></a><a name="array_view__rank_constant"></a>  array_view:: rank 常量  
 将存储的排名 [array_view](../../../parallel/amp/reference/array-view-class.md) 对象。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namearrayviewrefreshmethoda-arrayviewrefresh-method"></a><a name="array_view__refresh_method"></a>  array_view:: refresh 方法  
 通知 [array_view](../../../parallel/amp/reference/array-view-class.md) 对象已在外部修改其绑定的内存 `array_view` 接口。 对此方法的调用将呈现所有缓存的信息过期。  
  
```  
void refresh() const restrict(cpu);
```  
  
##  <a name="a-namearrayviewsectionmethoda-arrayviewsection-method"></a><a name="array_view__section_method"></a>  array_view:: section 方法  
 返回的子部分的 [array_view](../../../parallel/amp/reference/array-view-class.md) 位于指定的 origin 和 （可选） 该的对象具有指定的范围。  
  
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
 本部分范围的下一步-到-最高有效的组件。  
  
 `_E2`  
 本部分程度最不重要组件。  
  
 `_Ext`  
  [扩展盘区](../../../parallel/amp/reference/extent-class-cpp-amp.md) 对象，它指定部分中的程度。 原点为 0。  
  
 `_Idx`  
  [索引](../../../parallel/amp/reference/index-class.md) 对象，它指定原点的位置。 子部分是此扩展盘区的其余部分。  
  
 `_I0`  
 本部分的原点最重要的组件。  
  
 `_I1`  
 本部分的原点下一步-到-最高有效组件。  
  
 `_I2`  
 本部分的原点最不重要的组件。  
  
 `_Rank`  
 部分中的排名。  
  
 `_Section_extent`  
  [扩展盘区](../../../parallel/amp/reference/extent-class-cpp-amp.md) 对象，它指定部分中的程度。  
  
 `_Section_origin`  
  [索引](../../../parallel/amp/reference/index-class.md) 对象，它指定原点的位置。  
  
### <a name="return-value"></a>返回值  
 一个子节 `array_view` 位于指定的 origin 和 （可选） 该的对象具有指定的范围。 当仅 `index` 对象指定，则子节包含具有大于中的元素的索引的索引的所有元素关联的扩展盘区 `index` 对象。  
  
##  <a name="a-namearrayviewsourceacceleratorviewdatamembera-arrayviewsourceacceleratorview-data-member"></a><a name="array_view__source_accelerator_view_data_member"></a>  array_view:: source_accelerator_view 数据成员  
 获取源 accelerator_view 此 array_view 相关联。  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="a-namearrayviewsynchronizemethoda-arrayviewsynchronize-method"></a><a name="array_view__synchronize_method"></a>  array_view:: synchronize 方法  
 同步对所做的任何修改 `array_view` 回其源数据的对象。  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Access_type`  
 预期 [access_type](concurrency%20namespace%20enums.md#access_type) 目标系统上 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。 此参数具有默认值为 `access_type_read`。  
  
##  <a name="a-namearrayviewsynchronizeasyncmethoda-arrayviewsynchronizeasync-method"></a><a name="array_view__synchronize_async_method"></a>  array_view:: synchronize_async 方法  
 以异步方式同步对所做的任何修改 [array_view](../../../parallel/amp/reference/array-view-class.md) 回其源数据的对象。  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Access_type`  
 预期 [access_type](concurrency%20namespace%20enums.md#access_type) 目标系统上 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。 此参数具有默认值为 `access_type_read`。  
  
### <a name="return-value"></a>返回值  
 可等待操作完成的依据未来。  
  
##  <a name="a-namearrayviewsynchronizetomethoda-arrayviewsynchronizeto-method"></a><a name="array_view__synchronize_to_method"></a>  array_view:: synchronize_to 方法  
 同步到指定 accelerator_view 此 array_view 对所做的任何修改。  
  
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
 在目标 accelerator_view 上所需的 access_type。 此参数具有默认值为 access_type_read。  
  
##  <a name="a-namearrayviewsynchronizetoasyncmethoda-arrayviewsynchronizetoasync-method"></a><a name="array_view__synchronize_to_async_method"></a>  array_view:: synchronize_to_async 方法  
 以异步方式将同步到指定 accelerator_view 此 array_view 对所做的任何修改。  
  
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
 在目标 accelerator_view 上所需的 access_type。 此参数具有默认值为 access_type_read。  
  
### <a name="return-value"></a>返回值  
 可等待操作完成的依据未来。  
  
##  <a name="a-namearrayviewvaluetypedatamembera-arrayviewvaluetype-data-member"></a><a name="array_view__value_type_data_member"></a>  array_view:: value_type 数据成员  
 Array_view 和绑定的数组的值类型。  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="a-namearrayviewviewasmethoda-arrayviewviewas-method"></a><a name="array_view__view_as_method"></a>  array_view:: view_as 方法  
 重新解释这 `array_view` 作为 `array_view` 的不同级别。  
  
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
 新的秩 `array_view` 对象。  
  
 `_View_extent`  
 重塑 `extent`。  
  
 `value_type`  
 在这两个原始元素的数据类型 [数组](../../../parallel/amp/reference/array-class.md) 对象，并返回 `array_view` 对象。  
  
### <a name="return-value"></a>返回值  
  [Array_view](../../../parallel/amp/reference/array-view-class.md) 构造的对象。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
