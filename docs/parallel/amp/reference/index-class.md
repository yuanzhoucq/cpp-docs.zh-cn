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
ms.openlocfilehash: 06a5fa9a2d7e645c46b90ace957d31251baed81c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127798"
---
# <a name="index-class"></a>index 类

定义一个*N*维索引向量。

## <a name="syntax"></a>语法

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>参数

*_Rank*<br/>
级别或维度数。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[索引构造函数](#index_ctor)|初始化 `index` 类的新实例。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator--](#operator--)|递减 `index` 对象的每个元素。|
|[operator%=](#operator_mod_eq)|计算 `index` 对象中每个元素的模数（余数）。|
|[operator*=](#operator_star_eq)|将 `index` 对象的每个元素乘以一个数字。|
|[operator/=](#operator_div_eq)|将 `index` 对象的每个元素除以一个数字。|
|[index：： operator\[\]](#operator_at)|返回位于指定索引处的元素。|
|[operator++](#operator_add_add)|递增 `index` 对象的每个元素。|
|[operator+=](#operator_add_eq)|将指定数字添加到 `index` 对象的每个元素。|
|[operator=](#operator_eq)|将指定 `index` 对象的内容复制到此对象中。|
|[operator-=](#operator_-_eq)|从 `index` 对象的每个元素中减去指定数字。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[rank 常量](#rank)|存储 `index` 对象的排名。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`index`

## <a name="remarks"></a>备注

`index` 结构表示在*n*维空间中指定唯一位置的*n*个整数的坐标向量。 矢量中的值按从最重要到最不重要的顺序排列。 您可以使用[operator =](#operator_eq)检索组件的值。

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="index_ctor"></a>索引构造函数

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
最有效维度的长度。

*_I1*<br/>
最高有效维度的长度。

*_I2*<br/>
最小的有效维度的长度。

*_Other*<br/>
新索引对象所基于的索引对象。

## <a name="operator--"></a>operator--

递减索引对象的每个元素。

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>返回值

对于前缀运算符，则为索引对象（* this）。 对于后缀运算符，则为新的索引对象。

## <a name="operator_mod_eq"></a>运算符% =

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

## <a name="operator_star_eq"></a>运算符 * =

将索引对象中的每个元素乘以指定的数字。

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要相乘的数字。

## <a name="operator_div_eq"></a>operator/=

将索引对象中的每个元素除以指定的数字。

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要除以的数字。

## <a name="operator_at"></a>  operator\[\]

返回位于指定位置的索引的组件。

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
0到级别减1之间的整数。

### <a name="return-value"></a>返回值

位于指定索引处的元素。

### <a name="remarks"></a>备注

下面的示例显示索引的组件值。

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>operator + +

递增索引对象的每个元素。

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

对于前缀运算符，则为索引对象（* this）。 对于后缀运算符，则为新的索引对象。

## <a name="operator_add_eq"></a>运算符 + =

将指定数字添加到 index 对象的每个元素。

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
要添加的数目。

### <a name="return-value"></a>返回值

The index 对象。

## <a name="operator_eq"></a>operator=

将指定索引对象的内容复制到此对象中。

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从中进行复制的索引对象。

### <a name="return-value"></a>返回值

对此索引对象的引用。

## <a name="operator_-_eq"></a>operator-=

从 index 对象的每个元素中减去指定数字。

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

## <a name="rank"></a>级别

获取 index 对象的秩。

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
