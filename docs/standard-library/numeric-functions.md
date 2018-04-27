---
title: '&lt;numeric&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::partial_sum
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
caps.latest.revision: 13
manager: ghogen
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::partial_sum [C++]
ms.openlocfilehash: 73c17151ac0fcedd53872273bd248d5825b0161c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt; 函数

||||
|-|-|-|
|[accumulate](#accumulate)|[adjacent_difference](#adjacent_difference)|[inner_product](#inner_product)|
|[iota](#iota)|[partial_sum](#partial_sum)|

## <a name="accumulate"></a>accumulate

通过计算连续部分总和来计算指定范围（包括一些初始值）中所有元素的和，或计算通过指定的二元运算（而不是求和运算）获得的类似的连续部分结果的结果。

```cpp
template <class InputIterator, class Type>
Type accumulate(InputIterator first, InputIterator last, Type val);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type val,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>参数

`first` 输入发现的迭代器范围中的第一个元素求和或根据指定二元运算合并。

`last` 输入寻址的迭代器在范围内的最后一个元素是求和或根据指定二元运算合并即迭代累计中实际包含的最后一个元素之外的一个位置。

`val` 添加到的每个元素是反过来或者根据指定二元运算结合初始值。

`binary_op` 二元运算应用于每个元素中指定的范围和其以前的应用程序的结果。

### <a name="return-value"></a>返回值

`val` 与指定范围内第一个模板函数的所有元素或第二个模板函数的所有元素的总和，将指定的二元运算替代求和运算，应用于 ( *PartialResult, \*Iter*) 的结果，其中 *PartialResult* 是该运算的上一应用的结果，`Iter` 是指向范围内的元素的迭代器。

### <a name="remarks"></a>备注

初始值确保当范围为空时具有明确定义的结果，在这种情况下，将返回 `val`。 二元运算不需要具有关联性或可交换性。 将结果初始化为初始值 `val`，然后以迭代方式计算范围内的 *result* = `binary_op` ( *result*, **\***`Iter`)，其中 `Iter` 是指向范围内连续元素的迭代器。 该范围必须有效，并且其复杂度与该范围的大小呈线性关系。 二元运算符的返回类型必须可转换为 **Type**，以确保在迭代期间闭包。

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

## <a name="adjacent_difference"></a>  adjacent_difference

计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。

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
```

### <a name="parameters"></a>参数

`first` 发现其元素将要与各自前不同或值对的旨在由另一个操作上的输入范围内的第一个元素的输入迭代器指定二元运算。

`last` 发现其元素将要与各自前不同或值对的旨在由另一个操作上的输入范围内的最后一个元素的输入迭代器指定二元运算。

`result` 发现目标范围，其中的一系列差值或指定操作的结果是要存储的第一个元素的输出迭代器。

`binary_op` 是用于替换差分程序中减法运算的通用运算中应用的二元运算。

### <a name="return-value"></a>返回值

发现目标范围末尾的输出迭代器：`result` + ( `last` - `first`)。

### <a name="remarks"></a>备注

输出迭代器 _*结果*可以是相同的迭代器的输入迭代器作为 * 首先，*，以便`adjacent_difference`可能就地计算 s。

值的序列1， 2， 3，输入范围，第一个模板函数中的存储连续**partial_difference**s1， 2- 1，a3- 2，目标范围内的。

对于输入范围中的值序列 *a*1, *a*2, *a*3，第二个模板函数将在目标范围中存储连续的 **partial_difference**：*a*1, *a*2 `binary_op` *a*1, *a*3 `binary_op` *a*2。

二元运算 `binary_op` 无需具有关联性或可交换性，因为应用的运算顺序是完全指定的。

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

## <a name="inner_product"></a>  inner_product

计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积二元运算替换为其他指定二元运算的一般化程序的结果。

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val,
    BinaryOperation1  binary_op1,
    BinaryOperation2  binary_op2);
```

### <a name="parameters"></a>参数

`first1` 发现其内部产品或具有第二个范围的通用的内部产品是要计算的第一个范围中的第一个元素的输入迭代器。

`last1` 发现其内部产品或具有第二个范围的通用的内部产品是要计算的第一个范围中最后一个元素的输入迭代器。

`first2` 发现其内部产品或通用的内部产品与第一个范围时计算第二个范围的第一个元素的输入迭代器。

`val` 内部产品或通用的内部产品之间的范围为添加的初始值。

*binary_op1*替换应用于的内部产品泛化中的元素指向产品和内部产品运算二元运算。

*binary_op2*替换内部产品元素指向中的操作的倍数的内部产品泛化二元运算。

### <a name="return-value"></a>返回值

第一个成员函数返回逐元素集乘积的总和，并向其添加指定的初始值。 因此，对于值 *a*i 和 *b*i 的范围，它将返回：

`val` + ( *a*1 \* *b*1 ) + ( *a*2 \* *b*2 ) + ... + ( *a*n \* *b*n )

通过以迭代方式将`val`与`val`+ ( 我\* *b*我)。

第二个成员函数返回：

`val` *binary_op1* ( 1 *binary_op2* *b*1) *binary_op1* ( 2 *binary_op2* *b*2) *binary_op1* ...*binary_op1* ( n *binary_op2* *b*n)

通过以迭代方式将`val`与`val` *binary_op1* ( 我*binary_op2* *b*我)。

### <a name="remarks"></a>备注

初始值确保当范围为空时具有明确定义的结果，在这种情况下，将返回 `val`。 二元运算不需要具有关联性或可交换性。 该范围必须有效，并且其复杂度与该范围的大小呈线性关系。 二元运算符的返回类型必须可转换为 **Type**，以确保在迭代期间闭包。

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

## <a name="iota"></a>  iota

存储一个起始值，从第一个元素开始，在间隔 `[ first,  last)` 内的每个元素中填充此值的连续递增值 (` value++`)。

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>参数

`first` 输入迭代器，此迭代中要填充的范围的第一个元素。

`last` 输入迭代器，此迭代中要填充的范围的最后一个元素。

`value` 要存储中的第一个元素和连续增量后续元素的起始值。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

以下示例通过填充整数[列表](../standard-library/list.md)，然后通过 `list` 填充[向量](../standard-library/vector.md)演示了 `iota` 函数的一些用途，以便使用 [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle) 函数。

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

## <a name="partial_sum"></a>  partial_sum

计算输入范围中从第一个元素到第 *i* 个元素的一系列总和，并在目标范围的第 *i* 个元素中存储此类每个总和的结果，或计算将求和运算替换为其他指定二元运算的一般化程序的结果。

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

### <a name="parameters"></a>参数

`first` 输入迭代器寻址的范围中的第一个元素要部分求和或根据指定二元运算组合。

`last` 输入寻址的迭代器在范围内的最后一个元素要部分求和或根据指定二元运算合并即迭代累计中实际包含的最后一个元素之外的一个位置。

`result` 发现目标范围，其中的一系列部分和或指定操作的结果是要存储的第一个元素的输出迭代器。

`binary_op` 用于替换部分求和程序中求和运算的通用运算中应用的二元运算。

### <a name="return-value"></a>返回值

发现目标范围末尾的输出迭代器：`result` + ( `last` - `first`),

### <a name="remarks"></a>备注

输出迭代器 `result` 可以与输入迭代器 `first` 相同，因此可就地计算部分和。

对于输入范围中的 *a*1, *a*2, *a*3 值序列，第一个模板函数在目标范围中存储连续部分和，其中第 *i* 个元素通过 ( ( (*a*1 + *a*2) + *a*3) *a*i) 给定。

值的序列1， 2， 3，在输入的范围中第二个模板函数将存储在目标范围，其中第 i 个元素都的连续部分和所提供的 ((( 1 `binary_op` 2) `binary_op` 3) 我)。

二元运算 `binary_op` 无需具有关联性或可交换性，因为应用的运算顺序是完全指定的。

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

## <a name="see-also"></a>请参阅

[\<numeric>](../standard-library/numeric.md)<br/>
