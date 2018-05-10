---
title: gslice 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 127e1d4d39a79350dc050e1b9fb7636bce63c156
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="gslice-class"></a>gslice 类

对多维定义子集 valarray 的 valarray 的公共类。 如果 valarray 视为带任何元素的矩阵，则多维数组中提取切片矢量从多维数组。

## <a name="remarks"></a>备注

类用于存储确定类型 [gslice_array](../standard-library/gslice-array-class.md) 对象的参数。 当类 gslice 对象显示为类 [valarray](../standard-library/valarray-class.md#op_at)**\<Type>** 时，将间接构造一个 valarray 的子集。 存储的值（用于指定从父级 valarray 选择的子集）包括：

- 一个起始索引。

- 类 **valarray<size_t>** 的长度矢量。

- 类 **valarray<size_t>** 的跨距矢量。

两个矢量必须具有相同长度。

如果 gslice 定义的集合是的子集 valarray 常数，则 gslice 新 valarray。 如果 gslice 定义的集合是的子集 valarray 一个常数，则 gslice 具有引用语义对于 valarray 的原始。 常数的计算 valarrays 机制保存时间和内存。

在 valarrays 操作，确保仅 gslices 定义的源和目标中部分是不同的，并且所有索引都有效。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[gslice](#gslice)|定义包含 `valarray` 的多个切片所有开始的指定元素 `valarray` 的子集。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[size](#size)|查找数组值指定元素个数 `valarray` 中的泛切片。|
|[start](#start)|查找 `valarray` 的泛切片的起始索引。|
|[stride](#stride)|查找在 `valarray` 中的泛切片元素之间的距离。|

## <a name="requirements"></a>要求

**标头：**\<valarray>

**命名空间：** std

## <a name="gslice"></a>gslice::gslice

用于定义 valarray 多维切分的 valarray 实用程序类。

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>参数

`_StartIndex` Valarray 的子集中的第一个元素的索引。

`_LenArray` 数组中每个切片中指定的元素数。

`_IncArray` 在每个切片中指定 stride 数组。

### <a name="return-value"></a>返回值

默认构造函数对起始索引存储零，对于长度和跨距向量存储长度为零的向量。 第二个构造函数对于起始索引存储 `_StartIndex`，对于长度数组存储 `_LenArray`，对于跨距数组存储 `_IncArray`。

### <a name="remarks"></a>备注

**gslice** 定义一个由多个 valarray 的切分组成的 valarray 子集，其中每个都以同一指定元素开始。 `gslice` 和 [slice::slice](../standard-library/slice-class.md#slice) 之间的唯一差别在于使用数组定义多个切分的能力。 第一个切分具有一个带有 `_StartIndex` 的索引的第一个元素、由 `_LenArray` 的第一个元素指定的元素数和由 `_IncArray` 的第一个元素提供的跨距。 下一个正交切分集具有由第一个切分指定的第一个元素。 `_LenArray` 的第二个元素指定元素数。 跨距由 `_IncArray` 的第二个元素指定。 第三个维度的切分会将二维数组的元素视为起始元素，以此类推

### <a name="example"></a>示例

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="size"></a>gslice::size

查找指定 valarray 的泛切分中元素数的数组值。

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>返回值

指定 valarray 泛切分的每个切分中元素数的 valarray。

### <a name="remarks"></a>备注

成员函数将返回切分的存储长度。

### <a name="example"></a>示例

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
 vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="start"></a>gslice::start

查找 valarray 的泛切分的起始索引。

```cpp
size_t start() const;
```

### <a name="return-value"></a>返回值

valarray 的泛切分的起始索引。

### <a name="example"></a>示例

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="stride"></a>gslice::stride

查找 valarray 的泛切分中元素间的距离。

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>返回值

指定 valarray 泛切分的每个切分中元素之间距离的 valarray。

### <a name="example"></a>示例

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
 vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
