---
title: '&lt;numeric&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::partial_sum
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::partial_sum [C++]
ms.openlocfilehash: 47ac885152b0fdfbb9ce1ab77f6597db00c5bc07
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960247"
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

*第一个*的输入迭代器范围中的第一个元素求和或根据指定二元运算合并。

*最后一个*的输入迭代器寻址的范围中的最后一个元素求和或根据指定二元运算，即迭代累计中实际包含最后一个元素之外的一个位置合并。

*val*添加到的每个元素是又或者根据指定二元运算合并的初始值。

*binary_op* ，是要应用于指定的范围和其以前的应用程序的结果中的每个元素的二元运算。

### <a name="return-value"></a>返回值

总和*val*并指定范围内第一个模板函数，或对于第二个模板函数应用，而不是求和运算中，为指定二元运算的结果中的所有元素 ( *PartialResult， \*Iter*)，其中*PartialResult*是上一应用程序的操作结果和`Iter`是指向范围内的元素的迭代器。

### <a name="remarks"></a>备注

初始值确保，将有明确定义的结果时的范围为空，这种情况下*val*返回。 二元运算不需要具有关联性或可交换性。 结果将初始化为初始值*val* ，然后*结果* =  `binary_op` (*结果*， **\***`Iter`) 范围内，通过以迭代方式计算其中`Iter`是指向范围内的连续元素的迭代器。 该范围必须有效，并且其复杂度与该范围的大小呈线性关系。 二元运算符的返回类型必须可转换为 **Type**，以确保在迭代期间闭包。

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

*第一个*其元素将要与各自前不同或对值将由另一个进行运算的输入范围中的第一个元素的输入迭代器指定二元运算。

*最后一个*发现其元素将要与各自前不同或对值将由另一个进行运算的输入范围中最后一个元素的输入迭代器指定二元运算。

*结果*发现目标范围内的一系列差异或指定操作的结果存储的第一个元素的输出迭代器。

*binary_op* ，将替换差分程序中减法运算的通用运算中应用的二元运算。

### <a name="return-value"></a>返回值

发现目标范围末尾的输出迭代器：`result` + ( `last` - `first`)。

### <a name="remarks"></a>备注

输出迭代器 _*结果*可以是与输入迭代器相同的迭代器 * 第一，* 以便`adjacent_difference`s 可以就地计算。

为一系列值1， 2 3，第一个模板函数的输入范围中存储连续`partial_difference`s 12- 1，a3- 2，目标范围内的。

为一系列值1， 2 3，第二个模板函数的输入范围中存储连续`partial_difference`s 1， 2 `binary_op` 1， 3 `binary_op` 2，目标范围内的。

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

*first1*的内部乘积或一般化的内部乘积与第二个范围是要计算的第一个范围中的第一个元素的输入迭代器。

*last1*发现的内部乘积或一般化的内部乘积与第二个范围是要计算的第一个范围中最后一个元素的输入迭代器。

*first2*在第二个中发现的第一个元素的输入迭代器范围的内部乘积或一般化的内部乘积与第一个范围是将进行计算。

*val*初始值的内部乘积或一般化的内部乘积区域之间为添加。

*binary_op1* ，替换应用于在一般化内部乘积逐元素乘积的产品和内部乘积运算的二元运算。

*binary_op2* ，替换内部乘积逐元素乘积运算的乘号在一般化内部乘积二元运算。

### <a name="return-value"></a>返回值

第一个成员函数返回逐元素集乘积的总和，并向其添加指定的初始值。 因此，对于值 *a*i 和 *b*i 的范围，它将返回：

`val` + ( *a*1 \* *b*1 ) + ( *a*2 \* *b*2 ) + ... + ( *a*n \* *b*n )

通过以迭代方式替换*val*与`val`+ ( 我\* *b*我)。

第二个成员函数返回：

`val` *binary_op1* ( 1 *binary_op2* *b*1) *binary_op1* ( 2 *binary_op2* *b*2) *binary_op1* ...*binary_op1* ( n *binary_op2* *b*n)

通过以迭代方式替换*val*与`val` *binary_op1* ( 我*binary_op2* *b*i)。

### <a name="remarks"></a>备注

初始值可确保，将有明确定义的结果时的范围为空，这种情况下*val*返回。 二元运算不需要具有关联性或可交换性。 该范围必须有效，并且其复杂度与该范围的大小呈线性关系。 二元运算符的返回类型必须可转换为 **Type**，以确保在迭代期间闭包。

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

存储一个起始值，从第一个元素开始，并填充该值的连续递增值 (` value++`) 中的每个间隔中元素`[ first,  last)`。

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>参数

*第一个*要填充的范围内的第一个元素的输入迭代器。

*最后一个*要填充的范围内的最后一个元素的输入迭代器。

*值*要存储在第一个元素并连续增加后续元素的起始值。

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

*第一个*的输入迭代器范围中的第一个元素部分求和或根据指定二元运算合并。

*最后一个*的输入迭代器寻址的范围中的最后一个元素部分求和或根据指定二元运算，即迭代累计中实际包含最后一个元素之外的一个位置合并。

*结果*发现目标范围内的部分和或指定操作结果的一系列要存储的第一个元素的输出迭代器。

*binary_op* ，将替换部分求和过程中和运算的通用运算中应用的二元运算。

### <a name="return-value"></a>返回值

发现目标范围末尾的输出迭代器： `result` + (`last` - `first`)，

### <a name="remarks"></a>备注

输出迭代器*结果*可以是与输入迭代器相同的迭代器*第一个*，以便可以就地计算部分总和。

对于输入范围中的 *a*1, *a*2, *a*3 值序列，第一个模板函数在目标范围中存储连续部分和，其中第 *i* 个元素通过 ( ( (*a*1 + *a*2) + *a*3) *a*i) 给定。

为一系列值1， 2 3，在输入范围内，第二个模板函数将存储在目标范围内，其中第 i 个元素的连续部分总和通过给定 ((( 1 `binary_op` 2) `binary_op` 3) 我)。

二元运算*binary_op*不需要具有关联性或可交换性，因为应用的运算顺序完全指定。

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
