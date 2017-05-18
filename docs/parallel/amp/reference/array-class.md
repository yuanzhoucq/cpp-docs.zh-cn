---
title: "array 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
dev_langs:
- C++
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
caps.latest.revision: 31
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 470918d62357a8dd463db35b4d929e7ec5c2f251
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="array-class"></a>array 类
表示用于将数据移动到快捷键的数据容器。  
  
## <a name="syntax"></a>语法  
  
```  
template <typename value_type, int _Rank>  
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
|[数组构造函数](#ctor)|初始化 `array` 类的新实例。|  
|[~ array 析构函数](#dtor)|销毁`array`对象。|  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[copy_to](#copy_to)|将该数组的内容复制到另一个数组。|  
|[data](#data)|返回指向数组的原始数据的指针。|  
|[get_accelerator_view](#get_accelerator_view)|返回[accelerator_view](accelerator-view-class.md)对象，表示分配数组的位置。 仅在 CPU 上，可以访问此属性。|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。|  
|[get_cpu_access_type](#get_cpu_access_type)|返回[access_type](concurrency-namespace-enums-amp.md#access_type)的数组。 此方法可以访问仅在 CPU 上。|  
|[get_extent](#get_extent)|返回[扩展盘区](extent-class.md)数组的对象。|  
|[reinterpret_as](#reinterpret_as)|返回包含中的所有元素的一维数组`array`对象。|  
|[section](#section)|返回的子部分的`array`位于指定的 origin 和 （可选） 该的对象具有指定的范围。|  
|[view_as](#view_as)|返回[array_view](array-view-class.md)从构造的对象`array`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[运算符 std:: vector&lt;value_type&gt;](#operator_vec)|使用`copy(*this, vector)`隐式将数组转换为 std::[向量](../../../standard-library/vector-class.md)对象。|  
|[operator （)](#operator_call)|返回由参数指定的元素值。|  
|[operator]](#operator_at)|返回位于指定索引处的元素。|  
|[operator=](#operator_eq)|将指定的内容复制`array`到此对象。|  
  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[rank 常量](#rank)|存储数组的秩。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator_view](#accelerator_view)|获取[accelerator_view](accelerator-view-class.md)对象，表示分配数组的位置。 仅在 CPU 上，可以访问此属性。|  
|[associated_accelerator_view](#associated_accelerator_view)|获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。|  
|[cpu_access_type](#cpu_access_type)|获取[access_type](concurrency-namespace-enums-amp.md#access_type)表示如何 CPU 都可以访问该数组的存储。|  
|[extent](#extent)|获取定义该数组的形状的范围。|  
  
## <a name="remarks"></a>备注  
 类型`array<T,N>`表示一个密集和常规 （没有锯齿） *N*-维数组，它位于特定位置，如加速器或 CPU。 数组中元素的数据类型是`T`，它必须与目标加速器兼容的类型。 尽管排名， `N`，(的数组以静态方式确定，并且是该类型的一部分，则数组的范围内运行时确定，并且必须通过使用类表示`extent<N>`。  
  
 数组可以有任意数量的维度，尽管某些功能专用于`array`具有排名一、 二和三个对象。 如果您省略维度参数，默认值为 1。  
  
 数组数据在内存中是连续排列。 是最不重要的维度中的其中一个不同的元素都是在内存中相邻的。  
  
 数组是逻辑上被视为值类型，因为当数组复制到另一个数组中，执行的深层副本。 两个数组永远不会指向相同的数据。  
  
 `array<T,N>`类型用在几种方案︰  
  
-   作为可以在快捷键上计算中使用的数据容器。  
  
-   作为用于保存主机 CPU 上的内存 （即可以用来复制与其他数组） 的数据容器。  
  
-   作为临时对象以充当主机设备副本中快速媒介。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `array`  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  
  
##  <a name="dtor"></a>~ 数组 

 销毁`array`对象。  
  
```  
~array() restrict(cpu);
```  
  
##  <a name="accelerator_view"></a>accelerator_view 

 获取[accelerator_view](accelerator-view-class.md)对象，表示分配数组的位置。 仅在 CPU 上，可以访问此属性。  
  
```  
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;  
```  
  
##  <a name="ctor"></a>数组 

 新实例初始化[array 类](array-class.md)。 没有默认构造函数，为`array<T,N>`。 在 CPU 上运行的所有构造函数。 它们不能在 Direct3D 目标上执行。  
  
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
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first, 
    _InputIterator _Src_last) restrict(cpu);
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(
    int _E0,  
    int _E1,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,    
    Concurrency::accelerator_view _Av,  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
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
  
array(const array& _Other) restrict(cpu);  
  
array(array&& _Other) restrict(cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Associated_Av`  
 Accelerator_view 指定首选的目标位置的数组。  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md)对象，它指定数组的位置。  
  
 `_Cpu_access_type`  
 所需[access_type](concurrency-namespace-enums-amp.md#access_type) CPU 上的阵列。 此参数具有默认值为`access_type_auto`离开 CPU`access_type`向运行时确定。 实际 CPU`access_type`的数组可以使用查询`get_cpu_access_type`方法。  
  
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
  
##  <a name="associated_accelerator_view"></a>associated_accelerator_view 

 获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="copy_to"></a>copy_to 

 中的内容复制`array`到另一个`array`。  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const ;  
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;  
```  
  
### <a name="parameters"></a>参数  
 `_Dest`  
 [Array_view](array-view-class.md)将复制到的对象。  
  
##  <a name="cpu_access_type"></a>cpu_access_type 

 获取 CPU access_type 允许为此数组。  
  
```  
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;  
```  
  
##  <a name="data"></a>数据 

 将指针返回到原始数据的`array`。  
  
```  
value_type* data() restrict(amp, cpu);
  
const value_type* data() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>返回值  
 指向数组的原始数据的指针。  
  
##  <a name="extent"></a>扩展盘区 

 获取[扩展盘区](extent-class.md)对象，该定义的形状对象`array`。  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_accelerator_view"></a>get_accelerator_view 

 返回[accelerator_view](accelerator-view-class.md)代表位置对象，其中`array`分配对象。 仅在 CPU 上，可以访问此属性。  
  
```  
Concurrency::accelerator_view get_accelerator_view() const;  
```    
  
### <a name="return-value"></a>返回值  
 `accelerator_view`代表位置对象，其中`array`分配对象。  
  
##  <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view 

 获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const ;  
```  
  
### <a name="return-value"></a>返回值  
 第二个[accelerator_view](accelerator-view-class.md)对象传递给暂存构造函数。  
  
##  <a name="get_cpu_access_type"></a>get_cpu_access_type 

 允许为此数组的返回 CPU access_type。  
  
```  
access_type get_cpu_access_type() const restrict(cpu);
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="get_extent"></a>get_extent 

 返回[扩展盘区](extent-class.md)对象`array`。  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```  
  
### <a name="return-value"></a>返回值  
 `extent`对象`array`。  
  
##  <a name="operator_vec"></a>运算符 std:: vector&lt;value_type&gt; 

 使用`copy(*this, vector)`将隐式转换到 std:: vector 对象的数组。  
  
```  
operator std::vector<value_type>() const restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `value_type`  
 将向量的元素数据类型。  
  
### <a name="return-value"></a>返回值  
 类型的对象`vector<T>`，包含数组中包含的数据的副本。  
  
##  <a name="operator_call"></a>operator （) 

 返回由参数指定的元素值。  
  
```  
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);  
  
const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);
  
value_type& operator() (int _I0, int _I1) restrict(amp,cpu);  
  
const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;
  
value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);  
  
const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);  
  
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);  
  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 元素的位置。  
  
 `_I0`  
 本部分的原点最重要的组件。  
  
 `_I1`  
 本部分的原点下一步-到-最高有效组件。  
  
 `_I2`  
 本部分的原点最不重要的组件。  
  
 `_I`  
 元素的位置。  
  
### <a name="return-value"></a>返回值  
 在由参数指定的元素值。  
  
##  <a name="operator_at"></a>operator] 

 返回位于指定索引处的元素。  
  
```  
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);  
  
const value_type& operator[]  
    (const index<_Rank>& _Index) const restrict(amp,cpu);  
  
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);
  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```  
    
### <a name="parameters"></a>参数  
 `_Index`  
 索引。  
  
 `_I`  
 索引。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的元素。  
  
##  <a name="operator_eq"></a>运算符 = 

 将指定的内容复制`array`对象。  
  
```  
array& operator= (const array& _Other) restrict(cpu);  
   
array& operator= (array&& _Other) restrict(cpu);  
 
array& operator= (  
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `array`从其中复制对象。  
  
 `_Src`  
 `array`从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 参考这`array`对象。  
  
##  <a name="rank"></a>排名 

 将存储的排名`array`。  
  
```  
static const int rank = _Rank;  
```  
## <a name="reinterpret_as"></a>reinterpret_as 

重新解释通过一维 array_view，（可选） 可能具有比源数组不同的值类型数组。

### <a name="syntax"></a>语法
``` 
template <typename _Value_type2>  
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);  
  
template <typename _Value_type2>  
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);  
``` 
  
### <a name="parameters"></a>参数  
`_Value_type2`返回数据的数据类型。

### <a name="return-value"></a>返回值
Array_view 或基于数组，与从 T 重新解释为 ElementType 和减少从 N 到 1 排名的元素类型的常数 array_view 对象。

### <a name="remarks"></a>备注
有时会很方便地查看多维数组就好像它可能具有不同的值类型比源阵列是线性的一维数组。 可以使用此方法来实现此目的。
**警告︰** ︰ 数组对象重新解释使用不同的值类型是一个潜在的不安全操作。 我们建议您小心地使用此功能。 

下面的代码提供了一个示例。

```cpp  
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...; 
array_view<float,1> v = a.reinterpret_as<float>(); 

assert(v.extent == 3*a.extent);
```  
  
##  <a name="section"></a>部分 

 返回的子部分的`array`位于指定的 origin 和 （可选） 该的对象具有指定的范围。  
  
```  
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);
  
array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);
  
array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);
  
array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);
  
array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);
  
array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);
  
array_view<value_type,1> section(
    int _I0,  
    int _E0) restrict(amp,cpu);
  
array_view<const value_type,1> section(
    int _I0,  
    int _E0) const restrict(amp,cpu);
  
array_view<value_type,2> section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) restrict(amp,cpu);
  
array_view<const value_type,2> section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) const restrict(amp,cpu);
  
array_view<value_type,3> section(
    int _I0,  
    int _I1,  
    int _I2,  
    int _E0,  
    int _E1,  
    int _E2) restrict(amp,cpu);
  
array_view<const value_type,3> section(
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
 [扩展盘区](extent-class.md)对象，它指定部分中的程度。 原点为 0。  
  
 `_Idx`  
 [索引](index-class.md)对象，它指定原点的位置。 子部分是此扩展盘区的其余部分。  
  
 `_I0`  
 本部分的原点最重要的组件。  
  
 `_I1`  
 本部分的原点下一步-到-最高有效组件。  
  
 `_I2`  
 本部分的原点最不重要的组件。  
  
 `_Rank`  
 部分中的排名。  
  
 `_Section_extent`  
 [扩展盘区](extent-class.md)对象，它指定部分中的程度。  
  
 `_Section_origin`  
 [索引](index-class.md)对象，它指定原点的位置。  
  
 `value_type`  
 将复制的元素数据类型。  
  
### <a name="return-value"></a>返回值  
 返回的子部分的`array`位于指定的 origin 和 （可选） 该的对象具有指定的范围。 当仅`index`指定对象时，子部分包含关联的网格中具有大于中的元素的索引的索引的所有元素`index`对象。  
  
##  <a name="view_as"></a>view_as 

 重新解释为此数组[array_view](array-view-class.md)的不同级别。  
  
```  
template <int _New_rank>  
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

 
template <int _New_rank>  
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>参数  
 `_New_rank`  
 秩`extent`对象作为参数传递。  
  
 `_View_extent`  
 用于构造新的程度[array_view](array-view-class.md)对象。  
  
 `value_type`  
 在这两个原始元素的数据类型`array`对象，并返回`array_view`对象。  
  
### <a name="return-value"></a>返回值  
 [Array_view](array-view-class.md)构造的对象。  
  
## <a name="see-also"></a>另请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

