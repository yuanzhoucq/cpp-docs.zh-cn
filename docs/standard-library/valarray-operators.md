---
title: '&lt;valarray&gt; 运算符'
ms.date: 03/27/2019
f1_keywords:
- valarray/std::operator!=
- valarray/std::operator%
- valarray/std::operator&amp;
- valarray/std::operator&amp;&amp;
- valarray/std::operator&gt;
- valarray/std::operator&gt;&gt;
- valarray/std::operator&gt;=
- valarray/std::operator&lt;
- valarray/std::operator&lt;&lt;
- valarray/std::operator&lt;=
- valarray/std::operator*
- valarray/std::operator+
- valarray/std::operator-
- valarray/std::operator/
- valarray/std::operator==
- valarray/std::operator^
- valarray/std::operator|
- valarray/std::operator||
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
helpviewer_keywords:
- std::operator!= (valarray), std::operator&amp; (valarray)
- std::operator&amp;&amp; (valarray)
- std::operator&gt; (valarray)
- std::operator&gt;&gt; (valarray)
- std::operator&gt;= (valarray)
- std::operator&lt; (valarray)
- std::operator&lt;&lt; (valarray)
- std::operator&lt;= (valarray), std::operator== (valarray)
ms.openlocfilehash: 6de4b4ad75f9240fb86ff5e363f4a7d9062925d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365483"
---
# <a name="ltvalarraygt-operators"></a>&lt;valarray&gt; 运算符

||||
|-|-|-|
|[operator!=](#op_neq)|[operator%](#op_mod)|[operator&amp;](#op_amp)|
|[operator&amp;&amp;](#op_amp_amp)|[operator&gt;](#op_gt)|[operator&gt;&gt;](#op_gt_gt)|
|[operator&gt;=](#op_gt_eq)|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|
|[operator&lt;=](#op_lt_eq)|[operator*](#op_star)|[operator+](#op_add)|
|[operator-](#operator-)|[operator/](#op_div)|[operator==](#op_eq_eq)|
|[operator^](#op_xor)|[operator&#124;](#op_or)|[operator&#124;&#124;](#op_lor)|

## <a name="op_neq"></a>operator!=

测试两个相同大小的 valarray 的对应元素是否不相等，或 valarray 的所有元素是否都不等于指定值。

```cpp
template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator!=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，将对此 valarray 的元素进行不相等测试。

*right*<br/>
两个 valarray 中的第二个，将对此 valarray 的元素进行不相等测试。

### <a name="return-value"></a>返回值

布尔值的 valarray，其中每个：

- 如果对应的元素不相等，则为 **true**。

- 如果对应的元素相等，则为 **false**。

### <a name="remarks"></a>备注

第一个模板运算符返回类的对象[valarray\<bool >](../standard-library/valarray-bool-class.md)，每个元素`I`是`left[I] != right[I]`。

第二个模板运算符存储在元素中`I` `left[I] != right`。

第三个模板运算符存储在元素中`I` `left != right[I]`。

### <a name="example"></a>示例

```cpp
// valarray_op_ne.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL != vaR );
   cout << "The element-by-element result of "
        << "the not equal comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_mod"></a>operator%

获取指定值除以两个大小相同的 valarray 的对应元素所得的余数或除以 valarray 所得的余数，或 valarray 除以指定值所得的余数。

```cpp
template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator%(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个值或 valarray，它充当另一个值或 valarray 的被除数。

*right*<br/>
一个值或 valarray，它充当另一个值或 valarray 的除数。

### <a name="return-value"></a>返回值

一个 valarray，它的元素进行点算合并余数的*左*除以*右*。

### <a name="example"></a>示例

```cpp
// valarray_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   valarray<int> vaREM ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaREM = ( vaL % vaR );
   cout << "The remainders from the element-by-element "
        << "division is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaREM [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
*/
```

## <a name="op_amp"></a>operator&amp;

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 **AND**。

```cpp
template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的每个元素将与按位 `AND` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素按位合并。

*right*<br/>
两个 valarray 中的第二个，它的每个元素将与按位 `AND` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素按位合并。

### <a name="return-value"></a>返回值

一个 valarray，它的元素进行点算合并的按位 AND 运算组合的*左*并*右*。

### <a name="remarks"></a>备注

按位运算仅可用于操作中的位**char**并**int**数据类型和变体而不是在**float**， **double**， **longdouble**， **void**， **bool**或其他更复杂的数据类型。

按位 `AND` 具有与逻辑 `AND` 相同的事实表，但是按位 OR 适用于单个位级别上的数据类型。 [operator&&](#op_amp_amp) 应用于元素级别，它将所有非零值视为 true，结果是布尔值的 valarray。 按位`AND`[运算符 &](#op_amp)，与此相反，可产生 0 或 1，具体取决于按位运算的结果以外的值的 valarray。

### <a name="example"></a>示例

```cpp
// valarray_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaBWA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i+1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBWA = ( vaL & vaR );
   cout << "The element-by-element result of "
        << "the bitwise operator & is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaBWA [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
*/
```

## <a name="op_amp_amp"></a>  operator&amp;&amp;

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 **AND**。

```cpp
template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator&&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的每个元素将与逻辑 `AND` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素合并。

*right*<br/>
两个 valarray 中的第二个，它的每个元素将与逻辑 `AND` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素合并。

### <a name="return-value"></a>返回值

一个 valarray，它的元素属于 bool 类型和逻辑的逐元素乘积组合`AND`的操作*左*并*右*。

### <a name="remarks"></a>备注

逻辑`ANDoperator&&`适用于元素级别，它将所有非零值视为 true，并将该结果是布尔值的 valarray。 位版本的`AND`，[运算符 &、](#op_amp)，与此相反，可产生 0 或 1，具体取决于按位运算的结果以外的值的 valarray。

### <a name="example"></a>示例

```cpp
// valarray_op_logand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL && vaR );
   cout << "The element-by-element result of "
        << "the logical AND operator&& is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_gt"></a>operator&gt;

测试某个 valarray 的元素是否大于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于某个指定值。

```cpp
template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

*right*<br/>
两个 valarray 中的第二个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

### <a name="return-value"></a>返回值

布尔值的 valarray，其中每个：

- **true**如果*左*元素或值大于对应*右*元素或值。

- **false**如果*左*元素或值不大于相应*右*元素或值。

### <a name="remarks"></a>备注

如果两个 valarray 中的元素数不相等，则结果不可确定。

### <a name="example"></a>示例

```cpp
// valarray_op_gt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL > vaR );
   cout << "The element-by-element result of "
        << "the greater than comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_gt_eq"></a>operator&gt;=

测试某个 valarray 的元素是否大于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。

```cpp
template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

*right*<br/>
两个 valarray 中的第二个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

### <a name="return-value"></a>返回值

布尔值的 valarray，其中每个：

- **true**如果*左*元素或值是大于或等于对应*右*元素或值。

- **false**如果*左*元素或值小于相应*右*元素或值。

### <a name="remarks"></a>备注

如果两个 valarray 中的元素数不相等，则结果不可确定。

### <a name="example"></a>示例

```cpp
// valarray_op_ge.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >= vaR );
   cout << "The element-by-element result of "
        << "the greater than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_gt_gt"></a>  operator&gt;&gt;

将 valarray 的每个元素的位以指定数位向右移位，或按由第二个 valarray 指定的元素指向值向右移位。

```cpp
template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator>>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
要移动的值，或要移动其元素的 valarray。

*right*<br/>
指示右移位数或 valarray（其元素指示右移的元素指向值）。

### <a name="return-value"></a>返回值

一个 valarray，它的元素已按指定位数向右移动。

### <a name="remarks"></a>备注

有符号的数字必须保留其符号。

### <a name="example"></a>示例

```cpp
// valarray_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >> vaR );
   cout << "The element-by-element result of "
        << "the right shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*/
```

## <a name="op_lt"></a>operator&lt;

测试某个 valarray 的元素是否小于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于某个指定值。

```cpp
template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

*right*<br/>
两个 valarray 中的第二个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

### <a name="return-value"></a>返回值

布尔值的 valarray，其中每个：

- **true**如果*左*元素或值小于相应*右*元素或值。

- **false**如果*左*元素或值不小于相应*右*元素或值。

### <a name="remarks"></a>备注

如果两个 valarray 中的元素数不相等，则结果不可确定。

### <a name="example"></a>示例

```cpp
// valarray_op_lt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL < vaR );
   cout << "The element-by-element result of "
        << "the less-than comparson test is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_lt_eq"></a>  operator&lt;=

测试某个 valarray 的元素是否小于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。

```cpp
template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

*right*<br/>
两个 valarray 中的第二个，它的元素将进行比较；或一个指定值，此值将与 valarray 的每个元素进行比较。

### <a name="return-value"></a>返回值

布尔值的 valarray，其中每个：

- **true**如果*左*元素或值小于或等于对应*右*元素或值。

- **false**如果*左*元素或值大于对应*右*元素或值。

### <a name="remarks"></a>备注

如果两个 valarray 中的元素数不相等，则结果不可确定。

### <a name="example"></a>示例

```cpp
// valarray_op_le.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL <= vaR );
   cout << "The element-by-element result of "
        << "the less than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_lt_lt"></a>  operator&lt;&lt;

将 valarray 的每个元素的位以指定数位向左移位，或按由第二个 valarray 指定的元素指向值向左移位。

```cpp
template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator<<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
要移动的值，或要移动其元素的 valarray。

*right*<br/>
指示左移位数或 valarray（其元素指示左移的元素指向值）。

### <a name="return-value"></a>返回值

一个 valarray，它的元素已按指定位数向左移动。

### <a name="remarks"></a>备注

有符号的数字必须保留其符号。

### <a name="example"></a>示例

```cpp
// valarray_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL << vaR );
   cout << "The element-by-element result of "
        << "the left shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
*/
```

## <a name="op_star"></a>operator*

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和指定值之间的点积。

```cpp
template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator*(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的元素将进行乘法运算；或一个指定值，此值将与 valarray 的每个元素相乘。

*right*<br/>
两个 valarray 中的第二个，它的元素将进行乘法运算；或一个指定值，此值将与 valarray 的每个元素相乘。

### <a name="return-value"></a>返回值

一个 valarray，它的元素集乘积的*左*并*右*。

### <a name="example"></a>示例

```cpp
// valarray_op_eprod.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL * vaR );
   cout << "The element-by-element result of "
        << "the multiplication is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*/
```

## <a name="op_add"></a>operator+

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的点和。

```cpp
template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator+(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的元素将进行加法运算；或一个指定值，此值将与 valarray 的每个元素相加。

*right*<br/>
两个 valarray 中的第二个，它的元素将进行加法运算；或一个指定值，此值将与 valarray 的每个元素相加。

### <a name="return-value"></a>返回值

一个 valarray，它的元素的元素指向总和的*左*并*右*。

### <a name="example"></a>示例

```cpp
// valarray_op_esum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL + vaR );
   cout << "The element-by-element result of "
        << "the sum is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
*/
```

## <a name="operator-"></a>operator-

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的点差。

```cpp
template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator-(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个值或 valarray，它充当另一个值或 valarray 的被减数，并得出差值。

*right*<br/>
一个值或 valarray，它充当另一个值或 valarray 的减数，并得出差值。

### <a name="return-value"></a>返回值

一个 valarray，它的元素的点差的*左*并*右*。

### <a name="remarks"></a>备注

用于描述减法运算的算术术语：

差 = 被减数 - 减数

### <a name="example"></a>示例

```cpp
// valarray_op_ediff.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL - vaR );
   cout << "The element-by-element result of "
        << "the difference is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*/
```

## <a name="op_div"></a>operator/

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的点商。

```cpp
template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator/(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个值或 valarray，它充当另一个值或 valarray 的被除数，并得出商。

*right*<br/>
一个值或 valarray，它充当另一个值或 valarray 的除数，并得出商。

### <a name="return-value"></a>返回值

一个 valarray，它的元素的元素指向商的*左*除以*右*。

### <a name="remarks"></a>备注

用于描述除法运算的算术术语：

商 = 被除数 / 除数

### <a name="example"></a>示例

```cpp
// valarray_op_equo.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   valarray<double> vaNE ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL / vaR );
   cout << "The element-by-element result of "
        << "the quotient is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*/
```

## <a name="op_eq_eq"></a>operator==

测试两个相同大小的 valarray 的对应元素是否相等，或 valarray 的所有元素是否都等于指定值。

```cpp
template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator==(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，将对此 valarray 的元素进行相等性测试。

*right*<br/>
两个 valarray 中的第二个，将对此 valarray 的元素进行相等性测试。

### <a name="return-value"></a>返回值

布尔值的 valarray，其中每个：

- 如果对应的元素相等，则为 **true**。

- 如果对应的元素不相等，则为 **false**。

### <a name="remarks"></a>备注

第一个模板运算符返回类的对象[valarray\<bool >](../standard-library/valarray-bool-class.md)，每个元素`I`是`left[I] == right[I]`。 第二个模板运算符存储在元素中`I` `left[I] == right`。 第三个模板运算符存储在元素中`I` `left == right[I]`。

### <a name="example"></a>示例

```cpp
// valarray_op_eq.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL == vaR );
   cout << "The element-by-element result of "
        << "the equality comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_xor"></a>operator^

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位异 `OR` ( **XOR**)。

```cpp
template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator^(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的每个元素将与按位 **XOR** 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素按位合并。

*right*<br/>
两个 valarray 中的第二个，它的每个元素将与按位 **XOR** 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素按位合并。

### <a name="return-value"></a>返回值

一个 valarray，它的元素进行点算合并的按位组合**XOR**的操作*左*并*右*。

### <a name="remarks"></a>备注

按位运算仅可用于操作中的位**char**并**int**数据类型和变体而不是在**float**， **double**， **长双精度**， **void**， **bool**或其他更复杂的数据类型。

按位异`OR`( **XOR**) 具有以下语义：假设有位*b*1 和*b*2 *b*1 **XOR** *b*2 是**true**如果正好有一个位为 true;**false**如果两个位都为 false，或如果两个位都为 true。

### <a name="example"></a>示例

```cpp
// valarray_op_xor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL ^ vaR );
   cout << "The element-by-element result of "
        << "the bitwise XOR operator^ is the\n"
        << "valarray: ( ";
           for ( i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*/
```

## <a name="op_or"></a>operator|

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 `OR`。

```cpp
template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator|(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的每个元素将与按位 `OR` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素按位合并。

*right*<br/>
两个 valarray 中的第二个，它的每个元素将与按位 `OR` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素按位合并。

### <a name="return-value"></a>返回值

一个 valarray，它的元素进行点算合并的按位组合`OR`的操作*左*并*右*。

### <a name="remarks"></a>备注

按位运算仅可用于操作中的位**char**并**int**数据类型和变体而不是在**float**， **double**， **longdouble**， **void**， **bool**或其他更复杂的数据类型。

按位 OR 具有与逻辑 `OR` 相同的事实表，但是按位 OR 适用于单个位级别上的数据类型。 假设有位 b1 和 b2，如果至少有一个位为 true，则 b1 `OR` b2 为 **true**；如果两个位都为 false，则为 **false**。 逻辑 `OR`[operator||](../standard-library/valarray-operators.md#op_lor) 在元素级别上适用，将所有非零值视为 **true**，结果为布尔值的 valarray。 相反，按位 OR `operator|` 可产生 0 或 1 以外的值的 valarray，具体取决于按位运算的结果。

### <a name="example"></a>示例

```cpp
// valarray_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL | vaR );
   cout << "The element-by-element result of "
        << "the bitwise OR operator| is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
*/
```

## <a name="op_lor"></a>operator||

获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 `OR`。

```cpp
template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator||(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
两个 valarray 中的第一个，它的每个元素将与逻辑 `OR` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素合并。

*right*<br/>
两个 valarray 中的第二个，它的每个元素将与逻辑 `OR` 合并；或一个元素类型的指定值，此元素类型将与 valarray 的每个元素合并。

### <a name="return-value"></a>返回值

Valarray 的元素的类型**bool**和逻辑或运算的按点合并组合*左*并*右*。

### <a name="remarks"></a>备注

逻辑`OR``operator||`适用于元素级别，所有非零值视为**true**，结果为布尔值的 valarray。 相反，按位版本的 `OR`、[operator|](../standard-library/valarray-operators.md#op_or) 可产生 0 或 1 以外的值的 valarray，具体取决于按位运算的结果。

### <a name="example"></a>示例

```cpp
// valarray_op_logor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLOR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLOR = ( vaL || vaR );
   cout << "The element-by-element result of "
        << "the logical OR operator|| is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaLOR [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
*/
```

## <a name="see-also"></a>请参阅

[\<valarray>](../standard-library/valarray.md)<br/>
