---
title: '&lt;numeric&gt; 函数'
description: 描述C++标准库中 &lt;数值&gt;标头提供的函数模板。
ms.date: 10/30/2019
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::exclusive_scan
- numeric/std::gcd
- numeric/std::inclusive_scan
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::lcm
- numeric/std::partial_sum
- numeric/std::reduce
- numeric/std::transform_exclusive_scan
- numeric/std::transform_inclusive_scan
- numeric/std::transform_reduce
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::exclusive_scan [C++]
- std::gcd [C++]
- std::inclusive_scan [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::lcm [C++]
- std::partial_sum [C++]
- std::reduce [C++]
- std::transform_exclusive_scan [C++]
- std::transform_inclusive_scan [C++]
- std::transform_reduce [C++]
ms.openlocfilehash: 88a97a3d110c684090b78570077927e32541eed7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425363"
---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt; 函数

## <a name="accumulate"></a>持续

通过计算连续的部分和来计算指定范围内的所有元素的总和（包括一些初始值）。 或者，计算指定二元运算的连续部分结果的结果。

```cpp
template <class InputIterator, class Type>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>parameters

*第一个*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op*进行求和或合并。

*最后*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*init*\
一个初始值，将使用*binary_op*将每个元素添加或合并为该初始值。

*binary_op*\
要应用于指定范围内的每个元素及其以前应用程序的结果的二元运算。

### <a name="return-value"></a>返回值

第一个模板函数的指定范围中*init*和所有元素的总和; 对于第二个模板函数，为第二个模板函数应用二元运算的结果，将*Binary_op* （* PartialResult， *in_iter*），其中*PartialResult*是操作之前的应用程序的结果，而*in_iter*是一个迭代器，它指向范围中的下一个元素。

### <a name="remarks"></a>备注

初始值可确保当范围为空时具有明确定义的结果，在这种情况下，将返回*init* 。 二元运算不需要具有关联性或可交换性。 结果初始化为初始值*init* ，然后*结果* = *binary_op*（*result*， *in_iter*）以迭代方式通过范围进行迭代，其中*in_iter*是指向范围中的每个连续元素的迭代器。 范围必须有效，并且复杂性与范围大小为线性。 二元运算符的返回类型必须可转换为 **Type**，以确保在迭代期间闭包。

### <a name="example"></a>示例

```cpp
// numeric_accum.cpp
// compile with: /EHsc
#include <vector>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2(20);
   vector <int>::iterator iter1, iter2;

   int i;
   for (i = 1; i < 21; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   // The first member function for the accumulated sum
   int total;
   total = accumulate(v1.begin(), v1.end(), 0);

   cout << "The sum of the integers from 1 to 20 is: "
        << total << "." << endl;

   // Constructing a vector of partial sums
   int j = 0, partotal;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      partotal = accumulate(v1.begin(), iter1 + 1, 0);
      v2[j] = partotal;
      j++;
   }

   cout << "The vector of partial sums is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function for the accumulated product
   vector <int> v3, v4(10);
   vector <int>::iterator iter3, iter4;

   int s;
   for (s = 1; s < 11; s++)
   {
      v3.push_back(s);
   }

   cout << "The original vector v3 is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl;

   int ptotal;
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());

   cout << "The product of the integers from 1 to 10 is: "
        << ptotal << "." << endl;

   // Constructing a vector of partial products
   int k = 0, ppartotal;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());
      v4[k] = ppartotal;
      k++;
   }

   cout << "The vector of partial products is:\n ( " ;
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)
      cout << *iter4 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The sum of the integers from 1 to 20 is: 210.
The vector of partial sums is:
( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).

The original vector v3 is:
( 1 2 3 4 5 6 7 8 9 10 ).
The product of the integers from 1 to 10 is: 3628800.
The vector of partial products is:
( 1 2 6 24 120 720 5040 40320 362880 3628800 ).
```

## <a name="adjacent_difference"></a>adjacent_difference

计算输入范围中每个元素与其前一元素之间的连续差异。 将结果输出到目标范围。 或者，计算通用化过程的结果，其中差异运算替换为其他指定的二元运算。

```cpp
template <class InputIterator, class OutIterator>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>parameters

*exec*\
执行策略。

*第一个*\
输入迭代器，此迭代器在其中元素与各自前一元素不同的输入范围内或从中通过其他指定二元运算来操作值对的输入范围内发现第一个元素。

*最后*\
输入迭代器，此迭代器在其中元素与各自前一元素不同的输入范围内或从中通过其他指定二元运算来操作值对的输入范围内发现最后一个元素。

*结果*\
输出迭代器，此迭代器在存储一系列差值或指定运算结果的目标范围内发现第一个元素。

*binary_op*\
要在通用化操作中应用的二元运算，替换差分过程中减法运算。

### <a name="return-value"></a>返回值

用于寻址目标范围末尾的输出迭代器： `result` + （`last` - `first`）。

### <a name="remarks"></a>备注

输出迭代器*结果*允许作为输入迭代器的*第一个*迭代器，以便可以就地计算 `adjacent_difference` 值。

对于输入范围中的*值 a*1 *，a*2， *a*3，第一个模板函数在目标范围中存储连续 `adjacent_difference` 值*为*1、 *2-* *a*1、a3- *a*2。

对于输入范围中的值*a*1， *a*2， *a*3，第二个模板函数在目标范围中存储连续 `adjacent_difference` 值*a*1， *a*2 *binary_op* *1，* 3 *binary_op* *a*2。 *a*

二元*binary_op*运算不需要是关联或可交换的，因为指定了操作的顺序。

### <a name="example"></a>示例

```cpp
// numeric_adj_diff.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend, LIterend2;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t * t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the adjacent_differences of
   // elements in a list output to a vector
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "Output vector containing adjacent_differences is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the adjacent products of the elements in a list
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the adjacent products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of adjacent_differences in place
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="exclusive_scan"></a>exclusive_scan

在给定初始值的情况下，通过使用 `std::plus<>()` 或指定的二元运算符来计算独占前缀 sum 运算。 将结果写入从指定的目标开始的范围。 *独占前缀*sum 意味着第*n*个输入元素不包含在第*n*个 sum 中。 包含执行策略参数的重载根据指定的策略执行。

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init);

template<class InputIterator, class OutputIterator, class Type, class BinaryOperation>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>parameters

*exec*\
执行策略。

*第一个*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op*进行求和或合并。

*最后*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*结果*\
一种输出迭代器，用于寻址第一个元素的目标范围，其中的总和或指定操作的结果将存储在该范围内。

*init*\
一个初始值，将使用*binary_op*将每个元素添加或合并为该初始值。

*binary_op*\
要应用于指定范围内的每个元素及其以前应用程序的结果的二元运算。

### <a name="return-value"></a>返回值

用于寻址目标范围末尾的输出迭代器： *result* + （*最后* - *第一个*）。

## <a name="gcd"></a>gcd

计算整数 m 和 n 的最大公因数。

```cpp
template <class M, class N>
constexpr common_type_t<M,N> gcd(M m, N n);
```

### <a name="parameters"></a>parameters

*m*、 *n*\
整数类型的值。

### <a name="return-value"></a>返回值

返回*m*和*n*的绝对值的最大公因数，如果*m*和*n*均为零，则返回零。 如果*m*或*n*的绝对值不能表示为类型 `common_type_t<M,N>`的值，则结果是不确定的。

## <a name="inclusive_scan"></a>inclusive_scan

在给定初始值的情况下，通过使用 `std::plus<>()` 或指定的二元运算符来计算包含前缀 sum 运算。 将结果写入从指定的目标开始的范围。 包含*前缀*sum 表示*n*次求和中包含第*n*个输入元素。 包含执行策略参数的重载根据指定的策略执行。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template<class InputIterator, class OutputIterator, class BinaryOperation>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class Type>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation, class Type>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    Type init);
```

### <a name="parameters"></a>parameters

*exec*\
执行策略。

*第一个*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op*进行求和或合并。

*最后*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*结果*\
一种输出迭代器，用于寻址第一个元素的目标范围，其中的总和或指定操作的结果将存储在该范围内。

*init*\
一个初始值，将使用*binary_op*将每个元素添加或合并为该初始值。

*binary_op*\
要应用于指定范围内的每个元素及其以前应用程序的结果的二元运算。

### <a name="return-value"></a>返回值

用于寻址目标范围末尾的输出迭代器： *result* + （*最后* - *第一个*）。

## <a name="inner_product"></a>inner_product

计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积二元运算替换为其他指定二元运算的一般化程序的结果。

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);
```

### <a name="parameters"></a>parameters

*first1*\
一个输入迭代器，该迭代器发现第一个范围内的第一个元素，该范围与第二个范围的内部乘积或一般化内部乘积将进行计算。

*last1*\
一个输入迭代器，该迭代器发现第一个范围内的最后一个元素，该范围与第二个范围的内部乘积或一般化内部乘积将进行计算。

*first2*\
一个输入迭代器，该迭代器发现第二个范围内的第一个元素，该范围与第一个范围的内部乘积或一般化内部乘积将进行计算。

*init*\
一个初始值，将对该值添加两个范围间的内部乘积或一般化内部乘积。

*binary_op1*\
在一般化内部乘积中，替换应用于逐元素乘积的内部乘积求和运算的二元运算。

*binary_op2*\
在一般化内部乘积中，替换内部乘积逐元素乘积运算的二元运算。

### <a name="return-value"></a>返回值

第一个成员函数返回逐元素集乘积的总和，并向其添加指定的初始值。 因此，对于值 *a*i 和 *b*i 的范围，它将返回：

*init* + （*a*1 \* *b*1） + （*a*2 \* *b*2） + ... + （*a*n \* *b*n）

通过以迭代方式将*init*替换为*init* + （*a*i \* *b*i）。

第二个成员函数返回：

*init* *binary_op1* （*1* *binary_op2* *b*1） *binary_op1* （*a*2 *binary_op2* *b*2） *binary_op1* .。。*binary_op1* （*n* *binary_op2* *b*n）

通过以迭代方式将*init*替换为*init* *binary_op1* （*a*i *binary_op2* *b*i）。

### <a name="remarks"></a>备注

初始值可确保在范围为空时具有明确定义的结果。 在这种情况下，将返回*init* 。 二元运算不需要具有关联性或可交换性。 范围必须有效，并且复杂性与范围大小为线性。 二元运算符的返回类型必须可转换为 **Type**，以确保在迭代期间闭包。

### <a name="example"></a>示例

```cpp
// numeric_inner_prod.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   vector <int> v1, v2(7), v3(7);
   vector <int>::iterator iter1, iter2, iter3;

   int i;
   for (i = 1; i <= 7; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   list <int> l1, l2(7);
   list <int>::iterator lIter1, lIter2;

   int t;
   for (t = 1; t <= 7; t++)
   {
      l1.push_back(t);
   }

   cout << "The original list l1 is:\n ( " ;
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)
      cout << *lIter1 << " ";
   cout << ")." << endl;

   // The first member function for the inner product
   int inprod;
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);

   cout << "The inner_product of the vector v1 and the list l1 is: "
        << inprod << "." << endl;

   // Constructing a vector of partial inner_products between v1 & l1
   int j = 0, parinprod;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);
      v2[j] = parinprod;
      j++;
   }

   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function used to compute
   // the product of the element-wise sums
   int inprod2;
   inprod2 = inner_product (v1.begin(), v1.end(),
      l1.begin(), 1, multiplies<int>(), plus<int>());

   cout << "The sum of the element-wise products of v1 and l1 is: "
        << inprod2 << "." << endl;

   // Constructing a vector of partial sums of element-wise products
   int k = 0, parinprod2;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      parinprod2 =
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,
         multiplies<int>(), plus<int>());
      v3[k] = parinprod2;
      k++;
   }

   cout << "Vector of partial sums of element-wise products is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl << endl;
}
```

## <a name="iota"></a>iota

存储一个起始值，从第一个元素开始，并用间隔中的每个元素中的值的连续增量填充（`value++`） `[first,  last)`。

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>parameters

*第一个*\
发现范围中要填充的第一个元素的输入迭代器。

*最后*\
发现范围中要填充的最后一个元素的输入迭代器。

*value*\
要存储在第一个元素中的起始值，并且为后面的元素连续递增。

### <a name="example"></a>示例

以下示例通过填充整数`iota`列表[，然后通过 ](../standard-library/list.md) 填充[向量](../standard-library/vector.md)演示了 `list` 函数的一些用途，以便使用 [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle) 函数。

```cpp
// compile by using: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <numeric>
#include <list>
#include <vector>
#include <iostream>

using namespace std;

int main(void)
{
    list <int> intList(10);
    vector <list<int>::iterator> intVec(intList.size());

    // Fill the list
    iota(intList.begin(), intList.end(), 0);

    // Fill the vector with the list so we can shuffle it
    iota(intVec.begin(), intVec.end(), intList.begin());

    random_shuffle(intVec.begin(), intVec.end());

    // Output results
    cout << "Contents of the integer list: " << endl;
    for (auto i: intList) {
        cout << i << ' ';
    }
    cout << endl << endl;

    cout << "Contents of the integer list, shuffled by using a vector: " << endl;
    for (auto i: intVec) {
        cout << *i << ' ';
    }
    cout << endl;
}
```

## <a name="lcm"></a>相连

```cpp
template <class M, class N>
constexpr common_type_t<M,N> lcm(M m, N n);
```

## <a name="partial_sum"></a>partial_sum

计算输入范围中从第一个元素到第*n*个元素的一系列总和，并在目标范围的第*n*个元素中存储每个此类 sum 的结果。 或者，计算通用化过程的结果，其中 sum 操作替换为另一个指定的二元运算。

```cpp
template <class InputIterator, class OutIt>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>parameters

*第一个*\
输入迭代器，此迭代器在要部分求和或根据指定二元运算合并的范围内发现第一个元素。

*最后*\
输入迭代器，此迭代器在要部分求和或根据指定二元运算合并的范围内发现最后一个元素，即迭代累计中实际包含的最后一个元素之外的一个位置。

*结果*\
一种输出迭代器，用于寻址目标范围的第一个元素，以存储部分求和或指定二元运算的后续结果。

*binary_op*\
要在通用化操作中应用的二元运算，用来替换 partial sum 过程中的 sum 运算。

### <a name="return-value"></a>返回值

用于寻址目标范围末尾的输出迭代器： *result* + （*最后* - *第一个*）。

### <a name="remarks"></a>备注

输出迭代器*结果*允许作为输入迭代器的*第一个*迭代器，以便可以就地计算部分总计。

对于值序列*a*1， *a*2 .。。在输入范围中，*第一个模板*函数在目标范围中存储连续部分求和。 第*n*个元素是由指定的（*a*+ *a*2 + *a*3 + ... + *a*n）。

对于输入范围内值*为*1、2*和3的值* *序列，第*二个模板函数在目标范围中存储连续的部分结果。 第*n*个元素由（（...）（（*a*1 *binary_op* *2）* *binary_op* *3）* *binary_op* ...）*binary_op* *n）* 。

二元*binary_op*运算不需要是关联或可交换的，因为指定了操作的顺序。

### <a name="example"></a>示例

```cpp
// numeric_partial_sum.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the partial sums of
   // elements in a list output to a vector
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "The output vector containing the partial sums is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the partial product of the elements in a list
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the partial products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of partial sums in place
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "The in place output partial_sum list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reduce"></a>降

通过计算任意且可能置换的顺序来减少指定范围内的所有元素，可能包括一些初始值。 或者，通过计算指定二元运算的结果减少。 包含执行策略参数的重载根据指定的策略执行。

```cpp
template<class InputIterator>
typename iterator_traits<InputIterator>::value_type reduce(
    InputIterator first,
    InputIterator last);

template<class InputIterator, class Type>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init);

template<class InputIterator, class Type, class BinaryOperation>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator>
typename iterator_traits<ForwardIterator>::value_type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Type>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>parameters

*exec*\
执行策略。

*第一个*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op*进行求和或合并。

*最后*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*结果*\
一种输出迭代器，用于寻址第一个元素的目标范围，其中的总和或指定操作的结果将存储在该范围内。

*init*\
一个初始值，将使用*binary_op*将每个元素添加或合并为该初始值。

*binary_op*\
要应用于指定范围内的每个元素及其以前应用程序的结果的二元运算。

### <a name="return-value"></a>返回值

将*binary_op*或 `std::plus<>()` 应用到*init* ，并将指定范围中的所有元素应用到（* PartialResult， *in_iter*），其中*PartialResult*是操作之前的应用程序的结果，而*in_iter*是指向范围内某个元素的迭代器。 在未指定*init*的重载中，使用的*init*值等效于 `typename iterator_traits<InputIterator>::value_type{}`。

### <a name="remarks"></a>备注

除非*binary_op*是关联的且可交换的，否则 `reduce` 行为是不确定的。 如果*binary_op*修改任意元素，或使时间间隔 \[*first*， *last*] 中的任何迭代器无效，则该行为是不确定的。

## <a name="transform_exclusive_scan"></a>transform_exclusive_scan

使用指定的一元运算符转换范围的元素，然后使用 `std::plus<>()` 或指定的二元运算符在该范围内计算独占前缀 sum 运算，给定初始值。 将结果写入从指定的目标开始的范围。 *独占前缀*sum 意味着第*n*个输入元素不包含在第*n*个 sum 中。 包含执行策略参数的重载根据指定的策略执行。 可以按任意顺序执行求和。

```cpp
template<class InputIterator, class OutputIterator, class Type, class BinaryOperation, class UnaryOperation>
OutputIterator transform_exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>parameters

*exec*\
执行策略。

*第一个*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op*进行求和或合并。

*最后*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*结果*\
一种输出迭代器，用于寻址第一个元素的目标范围，其中的总和或指定操作的结果将存储在该范围内。

*init*\
一个初始值，将使用*binary_op*将每个元素添加或合并为该初始值。

*binary_op*\
要应用于指定范围内的每个元素及其以前应用程序的结果的二元运算。

*unary_op*\
要应用于指定范围内的每个元素的一元运算。

## <a name="transform_inclusive_scan"></a>transform_inclusive_scan

使用指定的一元运算符转换范围内的元素，然后使用 `std::plus<>()` 或指定的二元运算符在该范围内计算包含初始值。 将结果写入从指定的目标开始的范围。 包含*前缀*sum 表示*n*次求和中包含第*n*个输入元素。 包含执行策略参数的重载根据指定的策略执行。 可以按任意顺序执行求和。

```cpp
template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation, class Type>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation, class Type>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);
```

### <a name="parameters"></a>parameters

*exec*\
执行策略。

*第一个*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op*进行求和或合并。

*最后*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*结果*\
一种输出迭代器，用于寻址第一个元素的目标范围，其中的总和或指定操作的结果将存储在该范围内。

*binary_op*\
要应用于指定范围内的每个元素及其以前应用程序的结果的二元运算。

*unary_op*\
要应用于指定范围内的每个元素的一元运算。

*init*\
一个初始值，将使用*binary_op*将每个元素添加或合并为该初始值。

## <a name="transform_reduce"></a>transform_reduce

转换一系列元素，然后应用一个函子，以任意顺序减少转换后的元素。 实际上，`transform` 后跟一个 `reduce`。

```cpp
template<class InputIterator1, class InputIterator2, class Type>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init);

template<class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class InputIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>parameters

*exec*\
执行策略。

*第一个*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op*进行求和或合并。

*first1*\
一种输入迭代器，用于寻址范围中的第一个元素，以通过使用*binary_op1*进行求和或合并。

*最后*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*last1*\
一种输入迭代器，用于寻址范围中的最后一个元素，该元素是通过使用*binary_op1*进行求和或合并的，而最后一个元素的位置不是实际包含在循环累积中的元素。

*结果*\
一种输出迭代器，用于寻址第一个元素的目标范围，其中的总和或指定操作的结果将存储在该范围内。

*init*\
一个初始值，将使用*binary_op*将每个元素添加或合并为该初始值。

*binary_op*\
要应用于指定范围内的每个元素及其以前应用程序的结果的二元运算。

*unary_op*\
要应用于指定范围内的每个元素的一元运算。

### <a name="return-value"></a>返回值

转换后的结果减少。
