---
title: "&lt;iterator&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xutility/std::operator!=
- xutility/std::operator&gt;
- xutility/std::operator&gt;=
- xutility/std::operator&lt;
- xutility/std::operator&lt;=
- xutility/std::operator+
- xutility/std::operator-
- xutility/std::operator==
dev_langs:
- C++
ms.assetid: b7c664f0-49d4-4993-b5d1-9ac4859fdddc
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::operator!= (iterator)
- std::operator&gt; (iterator)
- std::operator&gt;= (iterator)
- std::operator&lt; (iterator)
- std::operator&lt;= (iterator), std::operator== (iterator)
ms.openlocfilehash: 8d045aa1f32d3613eb4ed11af63a29e80e37b738
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltiteratorgt-operators"></a>&lt;iterator&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator+](#op_add)|  
|[operator-](#operator-)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>operator!=  
 测试运算符左侧的迭代器对象是否不等于右侧的迭代器对象。  
  
```  
template <class RandomIterator>  
bool operator!=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator!=(const istream_iterator<Type, CharType, Traits, Distance>& left, const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator!=(const istreambuf_iterator<CharType, Traits>& left, const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 **iterator** 类型的对象。  
  
 `right`  
 **iterator** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果迭代器对象不相等，则为 **true**；如果迭代器对象相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果两个迭代器对象对一个容器中的相同元素进行定址，则其中一个迭代器对象等于另一个。 如果两个迭代器指向一个容器中的不同元素，则他们不相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_ne.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 9 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 4 5 6 7 8 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 8.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 7.  
The iterators are not equal.  
```  
  
##  <a name="op_eq_eq"></a>operator==  
 测试运算符左侧的迭代器对象是否等于右侧的迭代器对象。  
  
```  
template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator==(
    const istream_iterator<Type, CharType, Traits, Distance>& left,  
    const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator==(
    const istreambuf_iterator<CharType, Traits>& left,  
    const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 iterator 类型的对象。  
  
 `right`  
 iterator 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果迭代器对象相等，则为 `true`；如果迭代器对象不相等，则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果两个迭代器对象对一个容器中的相同元素进行定址，则其中一个迭代器对象等于另一个。 如果两个迭代器指向一个容器中的不同元素，则他们不相等。  
  
 仅在 `left` 和 `right` 都存储同一迭代器时，前两个模板运算符才会返回 true。 仅在 `left` 和 `right` 都存储同一流指针时，第三个模板运算符才会返回 true。 第四个模板运算符返回 ` left.equal ( right)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_eq.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterators are not equal.  
```  
  
##  <a name="op_lt"></a>operator&lt;  
 测试运算符左侧的迭代器对象是否小于右侧的迭代器对象。  
  
```  
template <class RandomIterator>  
bool operator<(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 **iterator** 类型的对象。  
  
 `right`  
 **iterator** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果表达式左边的迭代器小于表达式右边的迭代器，则为 **true**；如果表达式左边的迭代器大于或等于右边的迭代器，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果一个迭代器对象所定址的元素在容器中早于另一个迭代器对象所定址的元素出现，则这个迭代器对象小于另一个迭代器对象。 如果一个迭代器对象与另一个迭代器对象对同一元素定址或对容器中晚于由另一个迭代器对象所定址元素出现的元素进行定址，则这个迭代器对象不小于另一个迭代器对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_lt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 0 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1& rVPOS2 initially point to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1& rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is not less than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
```  
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
 测试运算符左侧的迭代器对象是否小于或等于右侧的迭代器对象。  
  
```  
template <class RandomIterator>  
bool operator<=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 iterator 类型的对象。  
  
 `right`  
 iterator 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果表达式左边的迭代器小于或等于表达式右边的迭代器，则为 **true**；如果表达式左边的迭代器大于右边的迭代器，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果一个迭代器对象与另一个迭代器对象对同一元素定址或对容器中早于由另一个迭代器对象所定址元素出现的元素进行定址，则这个迭代器对象小于或等于另一个迭代器对象。 如果一个迭代器对象所定址的元素在容器中晚于另一个迭代器对象所定址的元素出现，则这个迭代器对象大于另一个迭代器对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_le.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ) + 1,   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS2 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_gt"></a>operator&gt;  
 测试运算符左侧的迭代器对象是否大于右侧的迭代器对象。  
  
```  
template <class RandomIterator>  
bool operator>(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 iterator 类型的对象。  
  
 `right`  
 iterator 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果表达式左边的迭代器大于表达式右边的迭代器，则为 **true**；如果表达式左边的迭代器小于或等于右边的迭代器，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果一个迭代器对象所定址的元素在容器中晚于另一个迭代器对象所定址的元素出现，则这个迭代器对象大于另一个迭代器对象。 如果一个迭代器对象与另一个迭代器对象对同一元素定址或对容器中早于由另一个迭代器对象所定址元素出现的元素进行定址，则这个迭代器对象不大于另一个迭代器对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_gt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
```  
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
 测试运算符左侧的迭代器对象是否大于或等于右侧的迭代器对象。  
  
```  
template <class RandomIterator>  
bool operator>=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 iterator 类型的对象。  
  
 `right`  
 iterator 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果表达式左边的迭代器大于或等于表达式右边的迭代器，则为 **true**；如果表达式左边的迭代器小于右边的迭代器，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果一个迭代器对象与另一个迭代器对象对同一元素定址或对容器中晚于由另一个迭代器对象所定址元素出现的元素进行定址，则这个迭代器对象大于或等于另一个迭代器对象。 如果一个迭代器对象所定址的元素在容器中早于另一个迭代器对象所定址的元素出现，则这个迭代器对象小于另一个迭代器对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_ge.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( ) + 1;  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_add"></a>  operator+  
 将偏移量添加到迭代器，并返回一个 `move_iterator` 或一个在新偏移位置处对插入元素定址的 `reverse_iterator`。  
  
```  
template <class RandomIterator, class Diff>  
move_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const move_iterator<RandomIterator>& right);

template <class RandomIterator>  
reverse_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>参数  
 `_Off`  
 const move_iterator 或 const reverse_iterator 要偏移的位置数。  
  
 `right`  
 要偏移的迭代器。  
  
### <a name="return-value"></a>返回值  
 返回 sum `right` + `_Off`。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_insert.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   vector<int>::difference_type diff = 4;  
   rVPOS1 = diff +rVPOS1;  
  
   cout << "The iterator rVPOS1 now points to the fifth "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 now points to the fifth element  
 in the reversed sequence: 2.  
```  
  
##  <a name="operator-"></a>operator-  
 从另一个迭代器中减去一个迭代器并返回差值。  
  
```  
template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 迭代器。  
  
 `right`  
 迭代器。  
  
### <a name="return-value"></a>返回值  
 两个迭代器的差异`.`  
  
### <a name="remarks"></a>备注  
 第一个模板运算符返回 `left.base() - right.base()`。  
  
 第二个模板运算符返回 `right.current - left.current`。  
  
 `Tdiff` 由返回表达式的类型决定。 否则，它是 `RandomIterator1::difference_type`。  
  
### <a name="example"></a>示例  
  
```cpp  
// iterator_op_sub.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
          rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
        << "the first element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   for (i = 1; i < 5; ++i)    
   {  
      rVPOS2++;  
   }  
   cout << "The iterator rVPOS2 now points to the fifth "  
        << "element\n in the reversed sequence: "  
        << *rVPOS2 << "." << endl;  
  
   vector<int>::difference_type diff = rVPOS2 - rVPOS1;  
   cout << "The difference: rVPOS2 - rVPOS1= "  
        << diff << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 now points to the fifth element  
 in the reversed sequence: 2.  
The difference: rVPOS2 - rVPOS1= 4.  
```  
  
## <a name="see-also"></a>请参阅  
 [\<iterator>](../standard-library/iterator.md)

