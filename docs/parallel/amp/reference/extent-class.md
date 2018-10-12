---
title: extent 类 (c + + AMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca17d81aa1712bcf6222b0ec0888f3a987269f03
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163111"
---
# <a name="extent-class-c-amp"></a>extent 类 (C++ AMP)

表示的向量*N*指定的边界的整数值*N*-原始为 0 维空间。 向量中的值按从最重要到最不重要的顺序排列。

### <a name="syntax"></a>语法

```
template <int _Rank>
class extent;
```

### <a name="parameters"></a>参数

*_Rank*<br/>
秩`extent`对象。

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[范围构造函数](#ctor)|初始化 `extent` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[包含](#contains)|验证指定`extent`对象具有指定的级别。|
|[size](#size)|返回 （以元素单位） 范围的总线性大小。|
|[tile](#tile)|生成`tiled_extent`指定维度与给定的平铺范围的对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator-](#operator_min)|返回一个新`extent`对象创建的减去`index`中的相应元素`extent`元素。|
|[operator--](#operator_min_min)|递减的每个元素`extent`对象。|
|[operator%=](#operator_mod_eq)|计算的每个元素的模数 （余数）`extent`对象时该元素除以一个数字。|
|[operator*=](#operator_star_eq)|每个元素乘以`extent`由许多对象。|
|[operator/=](#operator_min_eq)|每个元素除以`extent`由许多对象。|
|[extent::operator\[\]](#operator_at)|返回位于指定索引处的元素。|
|[operator+](#operator_add)|返回一个新`extent`创建通过对应的对象`index`和`extent`元素。|
|[operator++](#operator_add_add)|递增的每个元素`extent`对象。|
|[operator+=](#operator_add_eq)|将指定的数字添加到的每个元素`extent`对象。|
|[operator=](#operator_eq)|将复制的另一个内容`extent`到此对象。|
|[operator-=](#operator_min_eq)|将指定的每个元素数减去`extent`对象。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[rank 常量](#rank)|获取的排名`extent`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`extent`

## <a name="contains"></a> 包含

指示是否指定[索引](index-class.md)值包含在扩展对象。

### <a name="syntax"></a>语法

```
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
`index`要测试值。

### <a name="return-value"></a>返回值

**true**如果指定*索引*值包含在`extent`对象; 否则为**false**。

##  <a name="ctor"></a> 范围

初始化范围类的新实例。

### <a name="syntax"></a>语法

```
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Array*<br/>
一个数组`_Rank`用于创建新的整数`extent`对象。

*_I*<br/>
内容的长度。

*_I0*<br/>
最高有效位维的长度。

*_I1*<br/>
下一步-到-最高有效维的长度。

*_I2*<br/>
最低有效位维的长度。

*_Other*<br/>
`extent`在其上的对象的新`extent`基于对象。

## <a name="remarks"></a>备注

无参数构造函数初始化`extent`具有三个级别的对象。

如果数组用于构造`extent`对象，该数组的长度必须与匹配的秩`extent`对象。

##  <a name="operator_mod_eq"></a> operator %=

该元素除以一个数字时，计算范围中的每个元素的模数 （余数）。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要查找其模数的数字。

### <a name="return-value"></a>返回值

`extent` 对象。

##  <a name="operator_star_eq"></a> 运算符 * =

将指定的数字的范围对象中的每个元素相乘。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要相乘的数。

### <a name="return-value"></a>返回值

`extent` 对象。

## <a name="operator_add"></a> operator +

返回一个新`extent`对象创建通过对应`index`和`extent`元素。

### <a name="syntax"></a>语法

```
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
`index`对象，其中包含要添加的元素。

### <a name="return-value"></a>返回值

新的 `extent` 对象。

##  <a name="operator_add_add"></a> operator + +

递增扩展对象的每个元素。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

针对前缀运算符`extent`对象 (`*this`)。 针对后缀运算符，新`extent`对象。

##  <a name="operator_add_eq"></a> operator + =

将指定的数字添加到扩展对象的每个元素。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
号、 索引或范围添加。

### <a name="return-value"></a>返回值

生成的 `extent` 对象。

##  <a name="operator_min"></a> 运算符-

创建一个新`extent`对象通过从指定的每个元素中减去`index`对象中的相应元素从`extent`对象。

### <a name="syntax"></a>语法

```
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
`index`对象，其中包含要减去的元素。

### <a name="return-value"></a>返回值

新的 `extent` 对象。

##  <a name="operator_min_min"></a> operator-

递减扩展对象中的每个元素。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

针对前缀运算符`extent`对象 (`*this`)。 针对后缀运算符，新`extent`对象。

##  <a name="operator_div_eq"></a> / = 运算符

在扩展对象中的每个元素除以指定的数目。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要除以的数字。

### <a name="return-value"></a>返回值

`extent` 对象。

##  <a name="operator_min_eq"></a> 运算符 =

减去从扩展对象的每个元素指定的数字。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要减去的数。

### <a name="return-value"></a>返回值

生成的 `extent` 对象。

##  <a name="operator_eq"></a> 运算符 =

范围的另一个对象的内容复制到此。

### <a name="syntax"></a>语法

```
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
`extent`要从复制对象。

### <a name="return-value"></a>返回值

对此引用`extent`对象。

##  <a name="operator_at"></a> extent:: operator \[\]

返回位于指定索引处的元素。

### <a name="syntax"></a>语法

```
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
一个介于 0 到负 1 级别。

### <a name="return-value"></a>返回值

位于指定索引处的元素。

##  <a name="rank_constant"></a> 排名

将存储中的扩展对象的秩。

### <a name="syntax"></a>语法

```
static const int rank = _Rank;
```

##  <a name="size"></a> 大小

返回 `extent` 对象的总线性大小（以元素单位）。

### <a name="syntax"></a>语法

```
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a> 磁贴

生成具有指定的图标维度的 tiled_extent 对象。

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```
### <a name="parameters"></a>参数

*_Dim0*<br/>
平铺范围的最高有效组件。
*_Dim1*<br/>
平铺范围的下一步-到-最高有效组件。
*_Dim2*<br/>
平铺范围的最低有效组件。

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
