---
title: extent 类 (C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: 3e8dae7b76ea2efc852486a19f5d298cda477012
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126716"
---
# <a name="extent-class-c-amp"></a>extent 类 (C++ AMP)

表示*n*个整数值的向量，这些整数值指定具有0源的*n*维空间的界限。 矢量中的值按从最重要到最不重要的顺序排列。

## <a name="syntax"></a>语法

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>参数

*_Rank*<br/>
`extent` 对象的秩。

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[区构造函数](#ctor)|初始化 `extent` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[contains](#contains)|验证指定的 `extent` 对象是否具有指定的级别。|
|[size](#size)|返回区的总线性大小（单位为个元素）。|
|[磁](#tile)|生成一个 `tiled_extent` 对象，该对象具有指定维度给定的磁贴区。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator-](#operator_min)|返回一个新的 `extent` 对象，该对象通过将相应的 `extent` 元素中的 `index` 元素减来创建。|
|[operator--](#operator_min_min)|递减 `extent` 对象的每个元素。|
|[operator%=](#operator_mod_eq)|计算 `extent` 对象中每个元素的模数（余数）。|
|[operator*=](#operator_star_eq)|将 `extent` 对象的每个元素乘以一个数字。|
|[operator/=](#operator_min_eq)|将 `extent` 对象的每个元素除以一个数字。|
|[区：： operator\[\]](#operator_at)|返回位于指定索引处的元素。|
|[operator+](#operator_add)|返回通过添加相应的 `index` 和 `extent` 元素而创建的新 `extent` 对象。|
|[operator++](#operator_add_add)|递增 `extent` 对象的每个元素。|
|[operator+=](#operator_add_eq)|将指定数字添加到 `extent` 对象的每个元素。|
|[operator=](#operator_eq)|将另一个 `extent` 对象的内容复制到此对象中。|
|[operator-=](#operator_min_eq)|从 `extent` 对象的每个元素中减去指定数字。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[rank 常量](#rank_constant)|获取 `extent` 对象的排名。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`extent`

## <a name="contains"></a>有

指示指定的[索引](index-class.md)值是否包含在 "范围" 对象中。

### <a name="syntax"></a>语法

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
要测试的 `index` 值。

### <a name="return-value"></a>返回值

如果 `extent` 对象中包含指定的*索引*值，则**为 true** ; 否则为。否则**为 false**。

## <a name="ctor"></a>范围

初始化 "范围" 类的新实例。

### <a name="syntax"></a>语法

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Array*<br/>
用于创建新的 `extent` 对象的 `_Rank` 整数的数组。

*_I*<br/>
范围的长度。

*_I0*<br/>
最有效维度的长度。

*_I1*<br/>
最高有效维度的长度。

*_I2*<br/>
最小的有效维度的长度。

*_Other*<br/>
新的 `extent` 对象所基于的 `extent` 对象。

## <a name="remarks"></a>备注

默认构造函数初始化排名为3的 `extent` 对象。

如果使用数组构造 `extent` 对象，则数组的长度必须与 `extent` 对象的级别匹配。

## <a name="operator_mod_eq"></a>运算符% =

计算 "区" 中每个元素的模数（余数）（如果该元素被数字除）。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要查找其模数的数字。

### <a name="return-value"></a>返回值

`extent` 对象。

## <a name="operator_star_eq"></a>运算符 * =

将 "范围" 对象中的每个元素乘以指定的数字。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要相乘的数字。

### <a name="return-value"></a>返回值

`extent` 对象。

## <a name="operator_add"></a>operator +

返回通过添加相应的 `index` 和 `extent` 元素而创建的新 `extent` 对象。

### <a name="syntax"></a>语法

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
包含要添加的元素的 `index` 对象。

### <a name="return-value"></a>返回值

新的 `extent` 对象。

## <a name="operator_add_add"></a>operator + +

递增 "区" 对象的每个元素。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

对于前缀运算符，则为 `extent` 对象（`*this`）。 对于后缀运算符，则为新的 `extent` 对象。

## <a name="operator_add_eq"></a>运算符 + =

将指定的数字添加到 "区" 对象的每个元素。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要添加的数量、索引或范围。

### <a name="return-value"></a>返回值

生成的 `extent` 对象。

## <a name="operator_min"></a>操作员

通过将指定的 `index` 对象中的每个元素减去此 `extent` 对象中的相应元素来创建新的 `extent` 对象。

### <a name="syntax"></a>语法

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
包含要减去的元素的 `index` 对象。

### <a name="return-value"></a>返回值

新的 `extent` 对象。

## <a name="operator_min_min"></a>operator--

递减 "范围" 对象中的每个元素。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

对于前缀运算符，则为 `extent` 对象（`*this`）。 对于后缀运算符，则为新的 `extent` 对象。

## <a name="operator_div_eq"></a>operator/=

将 "范围" 对象中的每个元素除以指定的数字。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要除以的数字。

### <a name="return-value"></a>返回值

`extent` 对象。

## <a name="operator_min_eq"></a>operator-=

从 "片区" 对象的每个元素中减去指定数字。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要减去的数字。

### <a name="return-value"></a>返回值

生成的 `extent` 对象。

## <a name="operator_eq"></a>operator =

将另一个 "区" 对象的内容复制到此对象中。

### <a name="syntax"></a>语法

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从中进行复制的 `extent` 对象。

### <a name="return-value"></a>返回值

对此 `extent` 对象的引用。

## <a name="operator_at"></a>区：： operator \[\]

返回位于指定索引处的元素。

### <a name="syntax"></a>语法

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
0到级别减1之间的整数。

### <a name="return-value"></a>返回值

位于指定索引处的元素。

## <a name="rank_constant"></a>级别

存储 "区" 对象的秩。

### <a name="syntax"></a>语法

```cpp
static const int rank = _Rank;
```

## <a name="size"></a>规格

返回 `extent` 对象的总线性大小（以元素单位）。

### <a name="syntax"></a>语法

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a>磁

生成具有指定图块尺寸的 tiled_extent 对象。

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>参数

*_Dim0*<br/>
平铺区的最重要的组件。
*_Dim1*<br/>
平铺范围的最高有效组件。
*_Dim2*<br/>
平铺区的最不重要的组件。

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
