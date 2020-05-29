---
title: index 类
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 50222015e6b365dc161fd4334067c26c7f288337
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365151"
---
# <a name="index-class"></a>index 类

定义*N-* 维索引矢量。

## <a name="syntax"></a>语法

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>参数

*_Rank*<br/>
排名或维度数。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[索引构造函数](#index_ctor)|初始化 `index` 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[运算符--](#operator--)|声明`index`对象的每个元素。|
|[运算符%*](#operator_mod_eq)|当该元素除以数字时，`index`计算对象中每个元素的模数（剩余数）。|
|[运算符*](#operator_star_eq)|将`index`对象的每个元素乘以数字。|
|[操作员/*](#operator_div_eq)|将`index`对象的每个元素除以数字。|
|[索引：：运算符\[\]](#operator_at)|返回指定索引处的元素。|
|[运算符*](#operator_add_add)|增加`index`对象的每个元素。|
|[运算符*](#operator_add_eq)|将指定的编号添加到`index`对象的每个元素。|
|[运算符*](#operator_eq)|将指定`index`对象的内容复制到此对象中。|
|[运算符-*](#operator_-_eq)|从`index`对象的每个元素中减去指定的数字。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[排名 常量](#rank)|存储`index`对象的排名。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`index`

## <a name="remarks"></a>备注

该`index`结构表示*N*整数的坐标矢量，该矢量指定*N-* 维空间中的唯一位置。 矢量中的值从最显著到最不显著进行排序。 可以使用[运算符*](#operator_eq)检索组件的值。

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="index-constructor"></a><a name="index_ctor"></a>索引构造函数

初始化索引类的新实例。

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Array*<br/>
具有排名值的一维数组。

*_I*<br/>
一维索引中的索引位置。

*_I0*<br/>
最重要的维度的长度。

*_I1*<br/>
第二个最重要的维度的长度。

*_I2*<br/>
最小尺寸的长度。

*_Other*<br/>
新索引对象所基于的索引对象。

## <a name="operator--"></a><a name="operator--"></a>运算符--

声明索引对象的每个元素。

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>返回值

对于前缀运算符，索引对象 （*THIS）。 对于后缀运算符，一个新的索引对象。

## <a name="operator"></a><a name="operator_mod_eq"></a>运算符%*

在元素被某个指定的数除时，计算 index 对象中每个元素的模数（余数）。

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要通过除法查找模数的数字。

## <a name="return-value"></a>返回值

The index 对象。

## <a name="operator"></a><a name="operator_star_eq"></a>运算符*

将索引对象中的每个元素乘以指定数字。

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要乘法的数字。

## <a name="operator"></a><a name="operator_div_eq"></a>操作员/*

将索引对象中的每个元素除以指定数字。

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要除的编号。

## <a name="operator"></a><a name="operator_at"></a>算子\[\]

返回指定位置的索引的组件。

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
从 0 到排名减去 1 的整数。

### <a name="return-value"></a>返回值

在指定索引处的元素。

### <a name="remarks"></a>备注

以下示例显示索引的组件值。

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a>运算符*

增加索引对象的每个元素。

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

对于前缀运算符，索引对象 （*THIS）。 对于后缀运算符，一个新的索引对象。

## <a name="operator"></a><a name="operator_add_eq"></a>运算符*

将指定的编号添加到索引对象的每个元素。

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要添加的编号。

### <a name="return-value"></a>返回值

The index 对象。

## <a name="operator"></a><a name="operator_eq"></a>运算符*

将指定索引对象的内容复制到此对象中。

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从中复制的索引对象。

### <a name="return-value"></a>返回值

对此索引对象的引用。

## <a name="operator-"></a><a name="operator_-_eq"></a>运算符-*

从索引对象的每个元素中减去指定的数字。

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要减去的数字。

### <a name="return-value"></a>返回值

The index 对象。

## <a name="rank"></a><a name="rank"></a>排名

获取 index 对象的秩。

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
