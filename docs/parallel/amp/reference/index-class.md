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
ms.openlocfilehash: 5226440e49aab5766fc7992e0651e2b5ee5d4981
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180227"
---
# <a name="index-class"></a>index 类

定义*N*-维的索引 pographics cpp amp.md。

## <a name="syntax"></a>语法

```
template <int _Rank>
class index;
```

#### <a name="parameters"></a>参数

*_Rank*<br/>
秩或维数。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[索引构造函数](#index_ctor)|初始化 `index` 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator--](#operator--)|递减的每个元素`index`对象。|
|[operator%=](#operator_mod_eq)|计算的每个元素的模数 （余数）`index`对象时该元素除以一个数字。|
|[operator*=](#operator_star_eq)|每个元素乘以`index`由许多对象。|
|[operator/=](#operator_div_eq)|每个元素除以`index`由许多对象。|
|[index::operator\[\]](#operator_at)|返回位于指定索引处的元素。|
|[operator++](#operator_add_add)|递增的每个元素`index`对象。|
|[operator+=](#operator_add_eq)|将指定的数字添加到的每个元素`index`对象。|
|[operator=](#operator_eq)|将指定的内容复制`index`到此对象。|
|[operator-=](#operator_-_eq)|将指定的每个元素数减去`index`对象。|

### <a name="public-constants"></a>公共常量

|名称|描述|
|----------|-----------------|
|[rank 常量](#rank)|将存储的秩`index`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`index`

## <a name="remarks"></a>备注

`index`结构表示的坐标向量*N*指定中的唯一位置的整数*N*-维空间。 向量中的值按从最重要到最不重要的顺序排列。 您可以检索使用的组件的值[运算符 =](#operator_eq)。

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="index_ctor"></a> 索引构造函数

初始化索引类的新实例。

```
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
带有秩值的一维数组。

*_I*<br/>
中的一维索引的索引位置。

*_I0*<br/>
最高有效位维的长度。

*_I1*<br/>
下一步-到-最高有效维的长度。

*_I2*<br/>
最低有效位维的长度。

*_Other*<br/>
一个新的索引对象所基于的索引对象。

## <a name="operator--"></a>  operator--

递减的索引对象的每个元素。
```
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>返回值

针对前缀运算符，该索引对象 (* 这)。 针对后缀运算符，新的索引对象。

## <a name="operator_mod_eq"></a>  operator%=

该元素除以指定数目时将计算索引对象的每个元素的模数 （余数）。

```
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要通过除法查找模数的数字。

## <a name="return-value"></a>返回值
索引对象中。

## <a name="operator_star_eq"></a>  operator*=

将指定的数字索引对象的每个元素相乘。
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要相乘的数。

## <a name="operator_div_eq"></a>  operator/=

索引对象的每个元素除以指定的数目。

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要除以的数字。

## <a name="operator_at"></a>  operator\[\]

返回位于指定位置的索引的组件。

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
一个介于 0 到负 1 级别。

### <a name="return-value"></a>返回值

位于指定索引处的元素。

### <a name="remarks"></a>备注

下面的示例显示索引的分量值。
```
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator++

递增索引对象的每个元素。
```
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

针对前缀运算符，该索引对象 (* 这)。 针对后缀运算符，新的索引对象。

## <a name="operator_add_eq"></a>  operator+=

将指定的数字添加到每个元素的索引对象。
```
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要添加的数。

### <a name="return-value"></a>返回值

索引对象中。

## <a name="operator_eq"></a>operator=

将指定的索引对象的内容复制到此。
```
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从复制的索引对象。

### <a name="return-value"></a>返回值

对此索引对象的引用。

## <a name="operator_-_eq"></a>  operator-=

减去指定的数字从每个元素的索引对象。
```
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要减去的数。

### <a name="return-value"></a>返回值

索引对象中。

## <a name="rank"></a>  排名
  获取索引对象的秩。
```
static const int rank = _Rank;
```

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
