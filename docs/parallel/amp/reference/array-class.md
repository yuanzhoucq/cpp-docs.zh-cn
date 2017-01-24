---
title: "array 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array 类"
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# array 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示用于将数据移动到快捷键的数据容器。  
  
## <a name="syntax"></a>语法  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
friend class array;  
```  
  
#### <a name="parameters"></a>参数  
 `value_type`  
 数据元素类型。  
  
 `_Rank`  
 数组的秩。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[array:: array 构造函数](#array__array_constructor)|初始化 `array` 类的新实例。|  
|[数组:: ~ array 析构函数](#array___dtorarray_destructor)|销毁 `array` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[array:: copy_to 方法](#array__copy_to_method)|将该数组的内容复制到另一个数组。|  
|[array:: data 方法](#array__data_method)|返回指向数组的原始数据的指针。|  
|[array:: get_accelerator_view 方法](#array__get_accelerator_view_method)|返回 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象，表示分配数组的位置。 仅在 CPU 上，可以访问此属性。|  
|[array:: get_associated_accelerator_view 方法](#array__get_associated_accelerator_view_method)|获取第二个 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 暂存构造函数调用来实例化时作为参数传递的对象 [数组](../../../parallel/amp/reference/array-class.md) 对象。|  
|[array:: get_cpu_access_type 方法](#array__get_cpu_access_type_method)|返回 [access_type](access_type%20Enumeration.md) 的数组。 此方法可以访问仅在 CPU 上。|  
|[array:: get_extent 方法](#array__get_extent_method)|返回 [扩展盘区](../../../parallel/amp/reference/extent-class-cpp-amp.md) 数组的对象。|  
|[array:: reinterpret_as 方法](#array__reinterpret_as_method)|返回包含中的所有元素的一维数组 `array` 对象。|  
|[array:: section 方法](#array__section_method)|返回的子部分的 [数组](../../../parallel/amp/reference/array-class.md) 位于指定的 origin 和 （可选） 该的对象具有指定的范围。|  
|[array:: view_as 方法](#array__view_as_method)|返回 [array_view](../../../parallel/amp/reference/array-view-class.md) 从构造的对象 `array` 对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[array:: operator std:: vector&lt;value_type&gt; 运算符](#array__operator_std__vector_lt__value_type_gt__operator)|使用 `copy(*this, vector)` 隐式将数组转换为 std::[向量](../../../standard-library/vector-class.md) 对象。|  
|[array:: operator （) 运算符](#array__operator___operator)|返回由参数指定的元素值。|  
|[array:: operator [] 运算符](#array__operator_at_operator)|返回位于指定索引处的元素。|  
|[array:: operator = 运算符](#array__operator_eq_operator)|将指定的内容复制 `array` 到此对象。|  
  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[array:: rank 常量](#array__rank_constant)|存储数组的秩。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[array:: accelerator_view 数据成员](#array__accelerator_view_data_member)|获取 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象，表示分配数组的位置。 仅在 CPU 上，可以访问此属性。|  
|[array:: associated_accelerator_view 数据成员](#array__associated_accelerator_view_data_member)|获取第二个 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 暂存构造函数调用来实例化时作为参数传递的对象 [数组](../../../parallel/amp/reference/array-class.md) 对象。|  
|[array:: cpu_access_type 数据成员](#array__cpu_access_type_data_member)|获取 [access_type](access_type%20Enumeration.md) 表示如何 CPU 都可以访问该数组的存储。|  
|[array:: extent 数据成员](#array__extent_data_member)|获取定义该数组的形状的范围。|  
  
## <a name="remarks"></a>备注  
 类型 `array<T,N>` 表示一个密集和常规 （没有锯齿） *N*-维数组，它位于特定位置，如加速器或 CPU。 数组中元素的数据类型是 `T`, ，它必须与目标加速器兼容的类型。 尽管排名， `N`, ，(的数组以静态方式确定，并且是该类型的一部分，则数组的范围内运行时确定，并且必须通过使用类表示 `extent<N>`。  
  
 数组可以有任意数量的维度，尽管某些功能专用于 `array` 具有排名一、 二和三个对象。 如果您省略维度参数，默认值为 1。  
  
 数组数据在内存中是连续排列。 是最不重要的维度中的其中一个不同的元素都是在内存中相邻的。  
  
 数组是逻辑上被视为值类型，因为当数组复制到另一个数组中，执行的深层副本。 两个数组永远不会指向相同的数据。  
  
  `array<T,N>` 类型用在几种方案︰  
  
-   作为可以在快捷键上计算中使用的数据容器。  
  
-   作为用于保存主机 CPU 上的内存 （即可以用来复制与其他数组） 的数据容器。  
  
-   为使其作为主机设备副本中的快速中介的临时对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `array`  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namearraydtorarraydestructora-arrayarray-destructor"></a><a name="array___dtorarray_destructor"></a>  数组:: ~ array 析构函数  
 销毁 `array` 对象。  
  
```  
~array() restrict(cpu);
```  
  
##  <a name="a-namearrayacceleratorviewdatamembera-arrayacceleratorview-data-member"></a><a name="array__accelerator_view_data_member"></a>  array:: accelerator_view 数据成员  
 获取 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象，表示分配数组的位置。 仅在 CPU 上，可以访问此属性。  
  
```  
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;  
```  
  
##  <a name="a-namearrayarrayconstructora-arrayarray-constructor"></a><a name="array__array_constructor"></a>  array:: array 构造函数  
 新实例初始化 [array 类](../../../parallel/amp/reference/array-class.md)。 没有默认构造函数，为 `array<T,N>`。 在 CPU 上运行的所有构造函数。 它们不能在 Direct3D 目标上执行。  
  
```  
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

 
explicit array(
    int _E0) restrict(cpu);

 
explicit array(
    int _E0,  
    int _E1) restrict(cpu);

 
explicit array(
    int _E0,  
    int _E1,  
    int _E2) restrict(cpu);

 
array(
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

 
array(
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av,  
    accelerator_view _Associated_Av) restrict(cpu);

 
array(
    const array& _Other) restrict(cpu);

 
array(
    array&& _Other) restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Associated_Av`  
 Accelerator_view 指定首选的目标位置的数组。  
  
 `_Av`  
  [Accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象，它指定数组的位置。  
  
 `_Cpu_access_type`  
 所需 [access_type](access_type%20Enumeration.md)  CPU 上的阵列。 此参数具有默认值为 `access_type_auto` 离开 CPU `access_type` 向运行时确定。 实际 CPU `access_type` 的数组可以使用查询 `get_cpu_access_type` 方法。  
  
 `_Extent`  
 在每个维度中数组的范围。  
  
 `_E0`  
 本部分范围的最重要的组件。  
  
 `_E1`  
 本部分范围的下一步-到-最高有效的组件。  
  
 `_E2`  
 本部分程度最不重要组件。  
  
 `_InputIterator`  
 输入 interator 的类型。  
  
 `_Src`  
 若要复制的对象。  
  
 `_Src_first`  
 到源容器开始迭代器。  
  
 `_Src_last`  
 到源容器的迭代器结束。  
  
 `_Other`  
 其他数据源。  
  
 `_Rank`  
 部分中的排名。  
  
 `value_type`  
 将复制的元素数据类型。  
  
##  <a name="a-namearrayassociatedacceleratorviewdatamembera-arrayassociatedacceleratorview-data-member"></a><a name="array__associated_accelerator_view_data_member"></a>  array:: associated_accelerator_view 数据成员  
 获取第二个 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 暂存构造函数调用来实例化时作为参数传递的对象 [数组](../../../parallel/amp/reference/array-class.md) 对象。  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="a-namearraycopytomethoda-arraycopyto-method"></a><a name="array__copy_to_method"></a>  array:: copy_to 方法  
 中的内容复制 [数组](../../../parallel/amp/reference/array-class.md) 到另一个 `array`。  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const ;  
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;  
```  
  
### <a name="parameters"></a>参数  
 `_Dest`  
  [Array_view](../../../parallel/amp/reference/array-view-class.md) 将复制到的对象。  
  
##  <a name="a-namearraycpuaccesstypedatamembera-arraycpuaccesstype-data-member"></a><a name="array__cpu_access_type_data_member"></a>  array:: cpu_access_type 数据成员  
 获取 CPU access_type 允许为此数组。  
  
```  
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;  
```  
  
##  <a name="a-namearraydatamethoda-arraydata-method"></a><a name="array__data_method"></a>  array:: data 方法  
 将指针返回到原始数据的 [数组](../../../parallel/amp/reference/array-class.md)。  
  
```  
value_type* data() restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>返回值  
 指向数组的原始数据的指针。  
  
##  <a name="a-namearrayextentdatamembera-arrayextent-data-member"></a><a name="array__extent_data_member"></a>  array:: extent 数据成员  
 获取 [扩展盘区](../../../parallel/amp/reference/extent-class-cpp-amp.md) 对象，该定义的形状对象 [数组](../../../parallel/amp/reference/array-class.md)。  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="a-namearraygetacceleratorviewmethoda-arraygetacceleratorview-method"></a><a name="array__get_accelerator_view_method"></a>  array:: get_accelerator_view 方法  
 返回 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 代表位置对象，其中 [数组](../../../parallel/amp/reference/array-class.md) 分配对象。 仅在 CPU 上，可以访问此属性。  
  
```  
Concurrency::accelerator_view get_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>返回值  
  `accelerator_view` 代表位置对象，其中 [数组](../../../parallel/amp/reference/array-class.md) 分配对象。  
  
##  <a name="a-namearraygetassociatedacceleratorviewmethoda-arraygetassociatedacceleratorview-method"></a><a name="array__get_associated_accelerator_view_method"></a>  array:: get_associated_accelerator_view 方法  
 获取第二个 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 暂存构造函数调用来实例化时作为参数传递的对象 [数组](../../../parallel/amp/reference/array-class.md) 对象。  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const ;  
```  
  
### <a name="return-value"></a>返回值  
 第二个 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象传递给暂存构造函数。  
  
##  <a name="a-namearraygetcpuaccesstypemethoda-arraygetcpuaccesstype-method"></a><a name="array__get_cpu_access_type_method"></a>  array:: get_cpu_access_type 方法  
 允许为此数组的返回 CPU access_type。  
  
```  
access_type get_cpu_access_type() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-namearraygetextentmethoda-arraygetextent-method"></a><a name="array__get_extent_method"></a>  array:: get_extent 方法  
 返回 [扩展盘区](../../../parallel/amp/reference/extent-class-cpp-amp.md) 对象 [数组](../../../parallel/amp/reference/array-class.md)。  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```  
  
### <a name="return-value"></a>返回值  
  `extent` 对象 [数组](../../../parallel/amp/reference/array-class.md)。  
  
##  <a name="a-namearrayoperatorstdvectorltvaluetypegtoperatora-arrayoperator-stdvectorltvaluetypegt-operator"></a><a name="array__operator_std__vector_lt__value_type_gt__operator"></a>  array:: operator std:: vector&lt;value_type&gt; 运算符  
 使用 `copy(*this, vector)` 将隐式转换到 std:: vector 对象的数组。  
  
'' 运算符 std:: vector \< value_type > （） const restrict （cpu);
```  
  
### Parameters  
 `value_type`  
 The data type of the elements of the vector.  
  
### Return Value  
 An object of type `vector<T>` that contains a copy of the data that is contained in the array.  
  
##  <a name="array__operator___operator"></a>  array::operator() Operator  
 Returns the element value that is specified by the parameters.  
  
```  
value_type & operator （) (const 索引 \< _Rank > & _Index) restrict(amp,cpu);

 
const value_type 和 operator （） (const 索引 \< _Rank > & _Index) const restrict(amp,cpu);

 
value_type & operator （) （int _I0，int _I1） restrict(amp,cpu);

 
const value_type 和 operator （) （int _I0，int _I1） const restrict(amp,cpu);

 
value_type & operator （) （int _I0、 int _I1、 int _I2） restrict(amp,cpu);

 
const value_type 和 operator （) （int _I0、 int _I1、 int _I2） const restrict(amp,cpu);

 
typename details::_Projection_result_type \< value_type、 _Rank >:: _Result_type operator （) （int （_i）） restrict(amp,cpu);

 
typename details::_Projection_result_type \< value_type、 _Rank >:: _Const_result_type operator （) （int （_i）） const restrict(amp,cpu);
```  
  
### Parameters  
 `_Index`  
 The location of the element.  
  
 `_I0`  
 The most significant component of the origin of this section.  
  
 `_I1`  
 The next-to-most-significant component of the origin of this section.  
  
 `_I2`  
 The least significant component of the origin of this section.  
  
 `_I`  
 The location of the element.  
  
### Return Value  
 The element value specified by the parameters.  
  
##  <a name="array__operator_at_operator"></a>  array::operator[] Operator  
 Returns the element that is at the specified index.  
  
```  
value_type & 运算符 [] (const 索引 \< _Rank > & _Index) restrict(amp,cpu);

 
const value_type & 运算符 [] (const 索引 \< _Rank > & _Index) const restrict(amp,cpu);

 
typename details::_Projection_result_type \< value_type、 _Rank >:: _Result_type 运算符[](int _I) restrict(amp,cpu);

 
typename details::_Projection_result_type \< value_type、 _Rank >:: _Const_result_type 运算符[](int _I) const restrict(amp,cpu);
```  
  
### Parameters  
 `_Index`  
 The index.  
  
 `_I`  
 The index.  
  
### Return Value  
 The element that is at the specified index.  
  
##  <a name="array__operator_eq_operator"></a>  array::operator= Operator  
 Copies the contents of the specified [array](../../../parallel/amp/reference/array-class.md) object.  
  
```  
数组 （&) 运算符 = (const 数组 & _Other) restrict （cpu);

 
数组 （&) 运算符 = (数组 （& a) （& a) _Other) restrict （cpu);

 
数组 （&) 运算符 = (const array_view \< const value_type、 _Rank > & _Src) restrict （cpu);
```  
  
### Parameters  
 `_Other`  
 The `array` object to copy from.  
  
 `_Src`  
 The `array` object to copy from.  
  
### Return Value  
 A reference to this `array` object.  
  
##  <a name="array__rank_constant"></a>  array::rank Constant  
 Stores the rank of the [array](../../../parallel/amp/reference/array-class.md).  
  
```  
静态 const int 排名 = _Rank;  
```  
  
##  <a name="array__section_method"></a>  array::section Method  
 Returns a subsection of the [array](../../../parallel/amp/reference/array-class.md) object that is at the specified origin and, optionally, that has the specified extent.  
  
```  
array_view \< value_type、 _Rank > 部分 (const Concurrency::index \< _Rank > & _Section_origin，  
    const Concurrency::extent \< _Rank > & _Section_extent) restrict(amp,cpu);

 
array_view \< const value_type、 _Rank > 部分 (const Concurrency::index \< _Rank > & _Section_origin，  
    const Concurrency::extent \< _Rank > & _Section_extent) const restrict(amp,cpu);

 
array_view \< value_type、 _Rank > 部分 (const Concurrency::extent \< _Rank > & _Ext) restrict(amp,cpu);

 
array_view \< const value_type、 _Rank > 部分 (const Concurrency::extent \< _Rank > & _Ext) const restrict(amp,cpu);

 
array_view \< value_type、 _Rank > 部分 (const 索引 \< _Rank > & 上 _Idx) restrict(amp,cpu);

 
array_view \< const value_type、 _Rank > 部分 (const 索引 \< _Rank > & 上 _Idx) const restrict(amp,cpu);

 
array_view \< value_type，1 > 部分 (int _I0，  
    int _E0) restrict(amp,cpu);

 
array_view \< const value_type，1 > 部分 (int _I0，  
    int _E0) const restrict(amp,cpu);

 
array_view \< value_type，2 > 部分 (int _I0，  
    int _I1  
    int _E0  
    int _E1) restrict(amp,cpu);

 
array_view \< const value_type，2 > 部分 (int _I0，  
    int _I1  
    int _E0  
    int _E1) const restrict(amp,cpu);

 
array_view \< value_type，3 > 部分 (int _I0，  
    int _I1  
    int _I2  
    int _E0  
    int _E1  
    int _E2) restrict(amp,cpu);

 
array_view \< const value_type，3 > 部分 (int _I0，  
    int _I1  
    int _I2  
    int _E0  
    int _E1  
    int _E2) const restrict(amp,cpu);
```  
  
### Parameters  
 `_E0`  
 The most significant component of the extent of this section.  
  
 `_E1`  
 The next-to-most-significant component of the extent of this section.  
  
 `_E2`  
 The least significant component of the extent of this section.  
  
 `_Ext`  
 The [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) object that specifies the extent of the section. The origin is 0.  
  
 `_Idx`  
 The [index](../../../parallel/amp/reference/index-class.md) object that specifies the location of the origin. The subsection is the rest of the extent.  
  
 `_I0`  
 The most significant component of the origin of this section.  
  
 `_I1`  
 The next-to-most-significant component of the origin of this section.  
  
 `_I2`  
 The least significant component of the origin of this section.  
  
 `_Rank`  
 The rank of the section.  
  
 `_Section_extent`  
 The [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) object that specifies the extent of the section.  
  
 `_Section_origin`  
 The [index](../../../parallel/amp/reference/index-class.md) object that specifies the location of the origin.  
  
 `value_type`  
 The data type of the elements that are copied.  
  
### Return Value  
 Returns a subsection of the `array` object that is at the specified origin and, optionally, that has the specified extent. When only the `index` object is specified, the subsection contains all elements in the associated grid that have indexes that are larger than the indexes of the elements in the `index` object.  
  
##  <a name="array__view_as_method"></a>  array::view_as Method  
 Reinterprets this array as an [array_view](../../../parallel/amp/reference/array-view-class.md) of a different rank.  
  
```  
模板 \< int _New_rank  
>  
array_view \< value_type、 _New_rank > view_as (const Concurrency::extent \< _New_rank > & _View_extent) restrict(amp,cpu);

 
模板 \< int _New_rank  
>  
array_view \< const value_type、 _New_rank > view_as (const Concurrency::extent \< _New_rank > & _View_extent) const restrict(amp,cpu);
```  
  
### Parameters  
 `_New_rank`  
 The rank of the `extent` object passed as a parameter.  
  
 `_View_extent`  
 The extent that is used to construct the new [array_view](../../../parallel/amp/reference/array-view-class.md) object.  
  
 `value_type`  
 The data type of the elements in both the original [array](../../../parallel/amp/reference/array-class.md) object and the returned `array_view` object.  
  
### Return Value  
 The [array_view](../../../parallel/amp/reference/array-view-class.md) object that is constructed.  
  
## See Also  
 [Concurrency Namespace (C++ AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
