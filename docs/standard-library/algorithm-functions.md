---
title: "&lt;algorithm&gt; 函数 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- algorithm/std::adjacent_find
- adjacent_find
- algorithm/std::all_of
- all_of
- algorithm/std::any_of
- any_of
- algorithm/std::binary_search
- binary_search
- algorithm/std::copy
- copy
- algorithm/std::copy_backward
- copy_backward
- algorithm/std::copy_if
- copy_if
- algorithm/std::copy_n
- copy_n
- algorithm/std::equal
- equal
- algorithm/std::equal_range
- equal_range
- algorithm/std::fill
- fill
- algorithm/std::fill_n
- fill_n
- algorithm/std::find
- find
- algorithm/std::find_end
- find_end
- algorithm/std::find_first_of
- find_first_of
- algorithm/std::find_if
- find_if
- algorithm/std::find_if_not
- find_if_not
- algorithm/std::for_each
- for_each
- algorithm/std::generate
- generate
- algorithm/std::generate_n
- generate_n
- algorithm/std::includes
- includes
- algorithm/std::inplace_merge
- inplace_merge
- algorithm/std::is_heap
- is_heap
- algorithm/std::is_heap_until
- is_heap_until
- algorithm/std::is_partitioned
- is_partitioned
- algorithm/std::is_permutation
- is_permutation
- algorithm/std::is_sorted
- is_sorted
- algorithm/std::is_sorted_until
- is_sorted_until
- algorithm/std::iter_swap
- iter_swap
- algorithm/std::lexicographical_compare
- lexicographical_compare
- algorithm/std::lower_bound
- lower_bound
- algorithm/std::make_heap
- make_heap
- algorithm/std::max
- max
- algorithm/std::max_element
- max_element
- algorithm/std::merge
- merge
- algorithm/std::min
- min
- algorithm/std::minmax
- minmax
- algorithm/std::minmax_element
- minmax_element
- algorithm/std::min_element
- min_element
- algorithm/std::mismatch
- mismatch
- algorithm/std::move
- move
- algorithm/std::move_backward
- move_backward
- algorithm/std::next_permutation
- next_permutation
- algorithm/std::none_of
- none_of
- algorithm/std::nth_element
- nth_element
- algorithm/std::partial_sort
- partial_sort
- algorithm/std::partial_sort_copy
- partial_sort_copy
- algorithm/std::partition
- partition
- algorithm/std::partition_point
- partition_point
- algorithm/std::pop_heap
- pop_heap
- algorithm/std::prev_permutation
- prev_permutation
- algorithm/std::push_heap
- push_heap
- algorithm/std::random_shuffle
- random_shuffle
- algorithm/std::remove
- remove
- algorithm/std::remove_copy
- remove_copy
- algorithm/std::remove_copy_if
- remove_copy_if
- algorithm/std::remove_if
- remove_if
- algorithm/std::replace
- replace
- algorithm/std::replace_copy
- replace_copy
- algorithm/std::replace_copy_if
- replace_copy_if
- algorithm/std::replace_if
- replace_if
- algorithm/std::reverse
- reverse
- algorithm/std::reverse_copy
- reverse_copy
- algorithm/std::rotate
- rotate
- algorithm/std::rotate_copy
- rotate_copy
- algorithm/std::search
- search
- algorithm/std::search_n
- search_n
- algorithm/std::set_difference
- set_difference
- algorithm/std::set_intersection
- set_intersection
- algorithm/std::set_symmetric_difference
- set_symmetric_difference
- algorithm/std::set_union
- set_union
- algorithm/std::shuffle
- shuffle
- algorithm/std::sort
- sort
- algorithm/std::sort_heap
- sort_heap
- algorithm/std::stable_partition
- stable_partition
- algorithm/std::stable_sort
- stable_sort
- algorithm/std::swap_ranges
- swap_ranges
- algorithm/std::transform
- transform
- algorithm/std::unique
- unique
- algorithm/std::unique_copy
- unique_copy
- algorithm/std::upper_bound
- upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
dev_langs:
- C++
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 6b3c288921fd86c4c02a8e2ffa09a060fe5fd3a1
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="ltalgorithmgt-functions"></a>&lt;algorithm&gt; 函数
||||  
|-|-|-|  
|[move](#alg_move)|[adjacent_find](#adjacent_find)|[all_of](#all_of)|  
|[any_of](#any_of)|[binary_search](#binary_search)|[copy](#copy)|  
|[copy_backward](#copy_backward)|[copy_if](#copy_if)|[copy_n](#copy_n)|  
|[count](#count)|[count_if](#count_if)|[equal](#equal)|  
|[equal_range](#equal_range)|[fill](#fill)|[fill_n](#fill_n)|  
|[find](#find)|[find_end](#find_end)|[find_first_of](#find_first_of)|  
|[find_if](#find_if)|[find_if_not](#find_if_not)|[for_each](#for_each)|  
|[generate](#generate)|[generate_n](#generate_n)|[includes](#includes)|  
|[inplace_merge](#inplace_merge)|[is_heap](#is_heap)|[is_heap_until](#is_heap_until)|  
|[is_partitioned](#is_partitioned)|[is_permutation](#is_permutation)|[is_sorted](#is_sorted)|  
|[is_sorted_until](#is_sorted_until)|[iter_swap](#iter_swap)|[lexicographical_compare](#lexicographical_compare)|  
|[lower_bound](#lower_bound)|[make_heap](#make_heap)|[max](#max)|  
|[max_element](#max_element)|[merge](#merge)|[min](#min)|  
|[min_element](#min_element)|[minmax](#minmax)|[minmax_element](#minmax_element)|  
|[mismatch](#mismatch)|[move_backward](#move_backward)|[next_permutation](#next_permutation)|  
|[none_of](#none_of)|[nth_element](#nth_element)|[partial_sort](#partial_sort)|  
|[partial_sort_copy](#partial_sort_copy)|[partition](#partition)|[partition_copy](#partition_copy)|  
|[partition_point](#partition_point)|[pop_heap](#pop_heap)|[prev_permutation](#prev_permutation)|  
|[push_heap](#push_heap)|[random_shuffle](#random_shuffle)|[remove](#remove)|  
|[remove_copy](#remove_copy)|[remove_copy_if](#remove_copy_if)|[remove_if](#remove_if)|  
|[replace](#replace)|[replace_copy](#replace_copy)|[replace_copy_if](#replace_copy_if)|  
|[replace_if](#replace_if)|[reverse](#reverse)|[reverse_copy](#reverse_copy)|  
|[rotate](#rotate)|[rotate_copy](#rotate_copy)|[search](#search)|  
|[search_n](#search_n)|[set_difference](#set_difference)|[set_intersection](#set_intersection)|  
|[set_symmetric_difference](#set_symmetric_difference)|[set_union](#set_union)|[sort](#sort)|  
|[sort_heap](#sort_heap)|[stable_partition](#stable_partition)|[stable_sort](#stable_sort)|  
|[shuffle](#shuffle)|[swap](#swap)|[swap_ranges](#swap_ranges)|  
|[transform](#transform)|[unique](#unique)|[unique_copy](#unique_copy)|  
|[upper_bound](#upper_bound)|  
  
##  <a name="adjacent_find"></a>  adjacent_find  
 搜索相等或满足指定条件的两个相邻元素。  
  
```  
template<class ForwardIterator>  
    ForwardIterator adjacent_find(  
        ForwardIterator first,   
        ForwardIterator last);
  
template<class ForwardIterator , class BinaryPredicate>  
    ForwardIterator adjacent_find(  
        ForwardIterator first,   
        ForwardIterator last,   
        BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `last`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的前向迭代器。  
  
 `comp`  
 给定要搜索范围内相邻元素的值需满足的条件的二元谓词。  
  
### <a name="return-value"></a>返回值  
 指向相互之间相等（第一个版本中）或满足二元谓词给定条件（第二个版本中）的相邻元素对中第一个元素的前向迭代器，假设找到了此类元素对。 否则，将返回指向 `last` 的迭代器。  
  
### <a name="remarks"></a>备注  
 `adjacent_find` 算法是不改变顺序的算法。 要搜索的范围必须是有效的；所有指针必须是可解除引用的，并且最后一个位置可从第一个位置通过递增到达。 算法的时间复杂性在范围所包含的元素数目上呈线性。  
  
 `operator==` 用于确定元素间的匹配必须在其操作数之间施加等效关系。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_adj_fnd.cpp  
// compile with: /EHsc  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Returns whether second element is twice the first  
bool twice (int elem1, int elem2 )  
{  
   return elem1 * 2 == elem2;  
}  
  
int main()   
{  
   using namespace std;  
   list <int> L;  
   list <int>::iterator Iter;  
   list <int>::iterator result1, result2;  
  
   L.push_back( 50 );  
   L.push_back( 40 );  
   L.push_back( 10 );  
   L.push_back( 20 );  
   L.push_back( 20 );  
  
   cout << "L = ( " ;  
   for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )  
      cout << *Iter << " ";  
   cout << ")" << endl;  
  
   result1 = adjacent_find( L.begin( ), L.end( ) );  
   if ( result1 == L.end( ) )  
      cout << "There are not two adjacent elements that are equal."  
           << endl;  
   else  
      cout << "There are two adjacent elements that are equal."  
           << "\n They have a value of "  
           <<  *( result1 ) << "." << endl;  
  
   result2 = adjacent_find( L.begin( ), L.end( ), twice );  
   if ( result2 == L.end( ) )  
      cout << "There are not two adjacent elements where the "  
           << " second is twice the first." << endl;  
   else  
      cout << "There are two adjacent elements where "  
           << "the second is twice the first."  
           << "\n They have values of " << *(result2++);  
      cout << " & " << *result2 << "." << endl;  
}  
```  
  
```Output  
L = ( 50 40 10 20 20 )  
There are two adjacent elements that are equal.  
 They have a value of 20.  
There are two adjacent elements where the second is twice the first.  
 They have values of 10 & 20.  
```  
  
##  <a name="all_of"></a>  all_of  
 当给定范围中的每个元素均满足条件时返回 `true`。  
  
```  
template<class InputIterator, class Predicate>  
    bool all_of(  
        InputIterator first,   
        InputIterator last,   
        BinaryPredicatecomp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指示检查条件的起始位置。 该迭代器将标记元素范围的起始位置。  
  
 `last`  
 一种输入迭代器，指示在元素范围内检查条件的结束位置。  
  
 `comp`  
 要测试的条件。 这是用户定义的谓词函数对象，定义被检查元素要满足的条件。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="return-value"></a>返回值  
 如果在指示范围内的每个元素检测到条件，则返回 `true`，如果至少一次未检测条件，则返回 `false`。  
  
### <a name="remarks"></a>备注  
 对于范围 `[0,Last - first)` 中的每个 `N`，仅当谓词 `comp(*(_First + N))` 是 `true` 时，模版函数才返回 `true`。  
  
##  <a name="any_of"></a>  any_of  
 当指定元素范围中至少有一个元素满足条件时返回 `true`。  
  
```  
template<class InputIterator, class UnaryPredicate>  
    bool any_of(  
        InputIterator first,   
        InputIterator last,   
        UnaryPredicate comp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指示在元素范围内检查条件的起始位置。  
  
 `last`  
 一种输入迭代器，指示在元素范围内检查条件的结束位置。  
  
 `comp`  
 要测试的条件。 这是由用户定义的谓词函数对象提供的。 谓词定义所测试的元素应满足的条件。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="return-value"></a>返回值  
 如果在指示范围内至少一次检测到条件，则返回 `true`，如果从未检测条件，则返回 `false`。  
  
### <a name="remarks"></a>备注  
 模板函数返回`true`才，对于某些`N`范围内  
  
 `[0, last - first)`谓词`comp(*(first + N))`为 true。  
  
##  <a name="binary_search"></a>  binary_search  
 测试已排序的范围中是否有等于指定值的元素，或在二元谓词指定的意义上与指定值等效的元素。  
  
```  
template<class ForwardIterator, class Type>      
    bool binary_search(
        ForwardIterator first, 
        ForwardIterator last, 
        const Type& value);  
  
template<class ForwardIterator,  class Type,  class BinaryPredicate>  
    bool binary_search(
        ForwardIterator first, 
        ForwardIterator last, 
        const Type& value, 
        BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `last`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的前向迭代器。  
  
 `value`  
 需要与元素的值匹配或者必须满足元素值由二元谓词指定这一条件的值。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数，并且在满足时返回 `true`，未满足时返回 `false`。  
  
### <a name="return-value"></a>返回值  
 如果在范围中找到的元素等于或者等效于指定的值，则返回 `true`；否则，返回 `false`。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有指针必须可取消引用，并且在序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 已排序的范围必须是应用 `binary_search` 算法分别进行排列的前提条件，与排序合并范围时算法要使用的排序标准相同。  
  
 `binary_search` 不会修改源范围。  
  
 前向迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定它们是相等的（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。  
  
 该算法的复杂性是随机访问迭代器对数和线性的成正比的步骤数，否则为 ( `last`  -  `first`)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_bin_srch.cpp  
// compile with: /EHsc  
#include <list>  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser( int elem1, int elem2 )  
{  
    if (elem1 < 0)  
        elem1 = - elem1;  
    if (elem2 < 0)  
        elem2 = - elem2;  
    return elem1 < elem2;  
}  
  
int main( )  
{  
    using namespace std;  
  
    list <int> List1;  
  
    List1.push_back( 50 );  
    List1.push_back( 10 );  
    List1.push_back( 30 );  
    List1.push_back( 20 );  
    List1.push_back( 25 );  
    List1.push_back( 5 );  
  
    List1.sort();  
  
    cout << "List1 = ( " ;  
    for ( auto Iter : List1 )  
        cout << Iter << " ";  
    cout << ")" << endl;  
  
    // default binary search for 10  
    if( binary_search(List1.begin(), List1.end(), 10) )  
        cout << "There is an element in list List1 with a value equal to 10."  
        << endl;  
    else  
        cout << "There is no element in list List1 with a value equal to 10."  
        << endl;  
  
    // a binary_search under the binary predicate greater  
    List1.sort(greater<int>());  
    if( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )  
        cout << "There is an element in list List1 with a value greater than 10 "  
        << "under greater than." << endl;  
    else  
        cout << "No element in list List1 with a value greater than 10 "  
        << "under greater than." << endl;  
  
    // a binary_search under the user-defined binary predicate mod_lesser  
    vector<int> v1;  
  
    for( auto i = -2; i <= 4; ++i )  
    {  
        v1.push_back(i);  
    }  
  
    sort(v1.begin(), v1.end(), mod_lesser);  
  
    cout << "Ordered using mod_lesser, vector v1 = ( " ;  
    for( auto Iter : v1 )  
        cout << Iter << " ";  
    cout << ")" << endl;  
  
    if( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )  
        cout << "There is an element with a value equivalent to -3 "  
        << "under mod_lesser." << endl;  
    else  
        cout << "There is not an element with a value equivalent to -3 "  
        << "under mod_lesser." << endl;  
}   
```  
  
##  <a name="copy"></a>  copy  
 将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向前方向的新位置。  
  
```  
template<class InputIterator, class OutputIterator>  
    OutputIterator copy(
        InputIterator first, 
        InputIterator last, 
        OutputIterator destBeg);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 发现源范围内的第一个元素的位置的输入迭代器。  
  
 `last`  
 一个输入迭代器，用于确定源范围内最后一个元素之后下一个元素的位置。  
  
 *destBeg*  
 一种输出迭代器，用于定址目标范围内第一个元素的位置。  
  
### <a name="return-value"></a>返回值  
 发现即是一个在目标范围中的最后一个元素的位置的输出迭代器，此迭代器址`result`+ ( `last`  -   `first` )。  
  
### <a name="remarks"></a>备注  
 源范围必须有效，且必须具有足够的空间来保存所有要复制的元素。  
  
 因为此算法会从第一个元素开始按顺序复制源元素，所以，只要源范围的 `last` 位置未包含在目标范围中，目标范围便可能与源范围重叠。 可以使用**copy** 将元素移动到左侧，但不能移动到右侧，除非源范围和目标范围之间不存在重叠。 若要向右移动任意数量的位置，请使用 [copy_backward](../standard-library/algorithm-functions.md#copy_backward) 算法。  
  
 **copy** 算法只修改由迭代器指向的值，并为目标范围内的元素赋予新值。 它不能用来创建新元素，也无法直接将元素插入到空容器。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
      v1.push_back( 10 * i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 10 ; ii++ )  
      v2.push_back( 3 * ii );  
  
   cout << "v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To copy the first 3 elements of v1 into the middle of v2  
   copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );  
  
   cout << "v2 with v1 insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To shift the elements inserted into v2 two positions  
   // to the left  
   copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );  
  
   cout << "v2 with shifted insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
v1 = ( 0 10 20 30 40 50 )  
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )  
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )  
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )  
```  
  
##  <a name="copy_backward"></a>  copy_backward  
 将一个源范围中的元素值分配到目标范围，循环访问元素的源序列并将它们分配在一个向后方向的新位置。  
  
```  
template<class BidirectionalIterator1, class BidirectionalIterator2>  
    BidirectionalIterator2 copy_backward(
        BidirectionalIterator1 first, 
        BidirectionalIterator1 last, 
        BidirectionalIterator2 destEnd);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，用于定址源范围内第一个元素的位置。  
  
 `last`  
 一种双向迭代器，用于定址源范围内最后元素之后下一个元素的位置。  
  
 `destEnd`  
 一种双向迭代器，用于定址目标范围内最后元素之后下一个元素的位置。  
  
### <a name="return-value"></a>返回值  
 发现即是一个在目标范围中的最后一个元素的位置的输出迭代器，此迭代器址`destEnd`-( `last`  -   `first` )。  
  
### <a name="remarks"></a>备注  
 源范围必须有效，且必须具有足够的空间来保存所有要复制的元素。  
  
 `copy_backward` 算法的要求比 copy 算法更加严格。 它的输入和输出迭代器都必须是双向的。  
  
 `copy_backward` 和 [move_backward](../standard-library/algorithm-functions.md#move_backward) 算法是唯一的 C++ 标准库算法，这些算法使用指向目标范围末尾的迭代器来指定输出范围。  
  
 因为此算法会从最后一个元素开始按顺序复制源元素，所以，只要源范围的 `first` 位置未包含在目标范围中，目标范围便可能与源范围重叠。 `copy_backward` 可用来将元素移动到右侧，但不能移动到左侧，除非源范围和目标范围之间不存在重叠。 若要向左移动任意数量的位置，请使用 [copy](../standard-library/algorithm-functions.md#copy) 算法。  
  
 `copy_backward` 算法只修改由迭代器指向的值，并为目标范围内的元素赋予新值。 它不能用来创建新元素，也无法直接将元素插入到空容器。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_copy_bkwd.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; ++i )  
      v1.push_back( 10 * i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 10 ; ++ii )  
      v2.push_back( 3 * ii );  
  
   cout << "v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To copy_backward the first 3 elements of v1 into the middle of v2  
   copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );  
  
   cout << "v2 with v1 insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To shift the elements inserted into v2 two positions  
   // to the right  
   copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );  
  
   cout << "v2 with shifted insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
##  <a name="copy_if"></a>  copy_if  
 在元素范围中，复制对于指定条件为 `true` 的元素。  
  
```  
template<class InputIterator, class OutputIterator, class BinaryPredicate>  
    OutputIterator copy_if(  
        InputIterator first,   
        InputIterator last,  
        OutputIterator dest,  
        Predicate pred);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指示在一个范围内检查条件的开始位置。  
  
 `last`  
 一种输入迭代器，指示范围的结束位置。  
  
 `dest`  
 输出迭代器，指示复制元素的目标。  
  
 `_Pred`  
 在范围内每个元素对其进行测试的条件。 由用户定义的谓词函数对象提供这一条件。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="return-value"></a>返回值  
 一种等于 `dest` 的输出迭代器，针对符合条件的每个元素递增一次。 换言之，返回值减去 `dest` 等于复制的元素数目。  
  
### <a name="remarks"></a>备注  
 该模板函数为范围  中的每个  求值  
  
 `if (_Pred(*_First + N)) * dest++ = *(_First + N))`  
  
 一次为每个`N`范围内`[0, last - first)`，严格增加值的`N`从最低值开始 如果 `dest` 和 `first` 指定存储区域，则 `dest` 不得位于范围 `[` `first``,` `last``)` 内。  
  
##  <a name="copy_n"></a>  copy_n  
 复制指定数量的元素。  
  
```  
template<class InputIterator, class Size, class OutputIterator>  
    OutputIterator copy_n(
        InputIterator first, 
        Size count, 
        OutputIterator dest);  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 指示复制元素的位置的输入迭代器。  
  
 `count`  
 指定要复制的元素的数目的有符号或无符号整数类型。  
  
 `dest`  
 指示将元素复制到的位置的输出迭代器。  
  
### <a name="return-value"></a>返回值  
 返回元素已被复制到的输出迭代器。 它与第三个参数 `dest` 的返回值相等。  
  
### <a name="remarks"></a>备注  
 模板函数的计算结果`*(dest + N) = *(first + N))`一次为每个`N`范围内`[0, count)`，严格增加值的`N`从最低值开始。 然后返回 `dest + N`。 如果`dest`和`first`指定存储区域，`dest`不得位于范围`[first, last)`。  
  
##  <a name="count"></a>  count  
 返回范围中其值与指定值匹配的元素的数量。  
  
```  
template<class InputIterator, class Type> 
    typename iterator_traits<InputIterator>::difference_type count(
        InputIterator first, 
        InputIterator last, 
        const Type& val);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，用于寻址要遍历的范围中第一个元素的位置。  
  
 `last`  
 一种输入迭代器，用于寻址要遍历的范围中最后元素之后下一个元素的位置。  
  
 `val`  
 要计算的元素的值。  
  
### <a name="return-value"></a>返回值  
 **InputIterator** 的差异类型，将元素数量计入包含值 `val` 的范围 [  `first`, `last` ) 中。  
  
### <a name="remarks"></a>备注  
 `operator==` 用于确定元素与指定值之间的匹配必须在其操作数之间施加等效关系。  
  
 此算法已泛化，可使用模版函数 [count_if](../standard-library/algorithm-functions.md#count_if) 计入满足任何谓词的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_count.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    v1.push_back(10);  
    v1.push_back(20);  
    v1.push_back(10);  
    v1.push_back(40);  
    v1.push_back(10);  
  
    cout << "v1 = ( " ;  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result;  
    result = count(v1.begin(), v1.end(), 10);  
    cout << "The number of 10s in v2 is: " << result << "." << endl;  
}  
```  
  
```Output  
v1 = ( 10 20 10 40 10 )  
The number of 10s in v2 is: 3.  
```  
  
##  <a name="count_if"></a>  count_if  
 返回范围中其值满足指定条件的元素的数量。  
  
```  
template<class InputIterator, class Predicate>
    typename iterator_traits<InputIterator>::difference_type count_if(
        InputIterator first, 
        InputIterator last, 
        Predicate pred);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 用于确定要搜索范围中的第一个元素的位置的输入迭代器。  
  
 `last`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的输入迭代器。  
  
 `_Pred`  
 用户定义的谓词函数对象，用于定义如果计入元素要满足的条件。 谓词采用一个参数并返回 **true** 或 **false**。  
  
### <a name="return-value"></a>返回值  
 满足谓词指定的条件的元素数目。  
  
### <a name="remarks"></a>备注  
 此模板函数是算法 [count](../standard-library/algorithm-functions.md#count) 的泛化，它将“等于指定值”谓词替换为任何谓词。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_count_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater10(int value)  
{  
    return value >10;  
}  
  
int main()  
{  
    using namespace std;  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    v1.push_back(10);  
    v1.push_back(20);  
    v1.push_back(10);  
    v1.push_back(40);  
    v1.push_back(10);  
  
    cout << "v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(), greater10);  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
}  
```  
  
```Output  
v1 = ( 10 20 10 40 10 )  
The number of elements in v1 greater than 10 is: 2.  
```  
  
##  <a name="equal"></a>  equal  
 逐个元素比较两个范围是否相等或是否在二元谓词指定的意义上等效。  
  
 比较不同容器类型（例如 `vector` 和 `list`）中的元素时、比较不同元素类型时，或是需要比较容器的子范围时，可使用 `std::equal`。 否则，在比较相同容器类型中具有相同类型的元素时，可使用为每个容器提供的非成员运算符 `operator==`。  
  
 在 C++14 代码中使用双范围重载，因为对第二个范围仅采用单个迭代器的重载在第二个范围长于第一个范围时不会检测到差异，并且会在第二个范围短于第一个范围时导致未定义的行为。  
  
```  
template<class InputIterator1, class InputIterator2>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2);   
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2,  
    BinaryPredicate Comp); // C++14  
  
template<class InputIterator1, class InputIterator2>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2,  
    InputIterator2  Last2);  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2,  
    InputIterator2  Last2,  
    BinaryPredicate Comp);  
```  
  
### <a name="parameters"></a>参数  
 `First1`  
 用于确定要测试的第一个范围中第一个元素的位置的输入迭代器。  
  
 `Last1`  
 用于确定要测试的第一个范围中最后元素之后下一个元素的位置的输入迭代器。  
  
 `First2`  
 用于确定要测试的第二个范围中第一个元素的位置的输入迭代器。  
  
 `First2`  
 用于确定要测试的第二个范围中最后元素之后下一个元素的位置的输入迭代器。  
  
 `Comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 当且仅当范围相同或在二元谓词下等效（逐个元素比较时）时为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 要搜索的范围必须是有效的；所有迭代器必须是可解除引用的，并且最后一个位置可从第一个位置通过递增到达。  
  
 如果两个范围的长度相等，则算法的时间复杂性在范围所包含的元素数目上呈线性。 否则，函数会立即返回 `false`。  
  
 `operator==` 和用户定义的谓词都不需要施加在其操作数之间施加对称、反身和可传递的等效关系。  
  
### <a name="example"></a>示例  
  
```cpp  
#include <iostream>  
#include <vector>  
#include <algorithm>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };  
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };  
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };  
  
    // Using range-and-a-half equal:  
    bool b = equal(v1.begin(), v1.end(), v2.begin());  
    cout << "v1 and v2 are equal: "  
       << b << endl; // true, as expected  
  
    b = equal(v1.begin(), v1.end(), v3.begin());  
    cout << "v1 and v3 are equal: "  
       << b << endl; // true, surprisingly  
  
    // Using dual-range equal:  
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());  
    cout << "v1 and v3 are equal with dual-range overload: "  
       << b << endl; // false  
  
    return 0;  
}  
  
```  
  
##  <a name="equal_range"></a>  equal_range  
 在给定的排序范围中，查找其中所有元素都等效于给定值的子范围。  
  
```  
template<class ForwardIterator, class Type>  
pair<ForwardIterator, ForwardIterator> equal_range(  
    ForwardIterator first,  
    ForwardIterator last,   
    const Type& val);

template<class ForwardIterator, class Type, class Predicate>  
pair<ForwardIterator, ForwardIterator> equal_range(  
    ForwardIterator first,  
    ForwardIterator last,   
    const Type& val,   
    Predicate comp);  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `last`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的前向迭代器。  
  
 `val`  
 在已排序范围中搜索的值。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。  
  
### <a name="return-value"></a>返回值  
 一对前向迭代器，指定要搜索的范围中包含的一个子范围，根据所用的二元谓词（即 `comp`，或者默认情况下为“小于”）的定义，该子范围中的所有元素都等效于 `val`。  
  
 如果范围中没有元素等效于 `val`，则返回的一对前向迭代器相等，并指定可以插入 `val` 而不打乱范围顺序的指针位置。  
  
### <a name="remarks"></a>备注  
 该算法返回的一对迭代器中，第一个迭代器是 [lower_bound](../standard-library/algorithm-functions.md#lower_bound)，第二个迭代器是 [upper_bound](../standard-library/algorithm-functions.md#upper_bound)。  
  
 必须根据提供给 `equal_range` 的谓词排序范围。 例如，如果你打算使用“大于”谓词，则必须按降序排序范围。  
  
 根据所用谓词的定义，由 `equal_range` 返回的一对迭代器所定义的可能为空的子范围中的元素将等效于 `val`。  
  
 该算法的复杂性是随机访问迭代器对数和线性的成正比的步骤数，否则为 ( `last`  -  `first`)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_equal_range.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>()  
#include <iostream>  
#include <string>  
using namespace std;  
  
template<class T> void dump_vector( const vector<T>& v, pair< typename vector<T>::iterator, typename vector<T>::iterator > range )  
{  
    // prints vector v with range delimited by [ and ]  
  
    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        if( i == range.first )  
        {  
            cout << "[ ";  
        }  
        if( i == range.second )  
        {  
            cout << "] ";  
        }  
  
        cout << *i << " ";  
    }  
    cout << endl;  
}  
  
template<class T> void equal_range_demo( const vector<T>& original_vector, T val )  
{  
    vector<T> v(original_vector);  
  
    sort( v.begin(), v.end() );  
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';  
    for( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        cout << *i << " ";  
    }  
    cout << endl << endl;  
  
    pair< vector<T>::iterator, vector<T>::iterator > result  
        = equal_range( v.begin(), v.end(), val );  
  
    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';  
    dump_vector( v, result );  
    cout << endl;  
}  
  
template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T val, F pred, string predname )  
{  
    vector<T> v(original_vector);  
  
    sort( v.begin(), v.end(), pred );  
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';  
    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        cout << *i << " ";  
    }  
    cout << endl << endl;  
  
    pair< typename vector<T>::iterator, typename vector<T>::iterator > result  
        = equal_range( v.begin(), v.end(), val, pred );  
  
    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';  
    dump_vector( v, result );  
    cout << endl;  
}  
  
// Return whether absolute value of elem1 is less than absolute value of elem2  
bool abs_lesser( int elem1, int elem2 )  
{  
    return abs(elem1) < abs(elem2);  
}  
  
// Return whether string l is shorter than string r  
bool shorter_than(const string& l, const string& r)  
{  
    return l.size() < r.size();  
}  
  
int main()  
{  
    vector<int> v1;  
  
    // Constructing vector v1 with default less than ordering  
    for( int i = -1; i <= 4; ++i )  
    {  
        v1.push_back(i);  
    }  
  
    for( int i =-3; i <= 0; ++i )  
    {  
        v1.push_back( i );  
    }  
  
    equal_range_demo( v1, 3 );  
    equal_range_demo( v1, 3, greater<int>(), "greater" );  
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );  
  
    vector<string> v2;  
  
    v2.push_back("cute");  
    v2.push_back("fluffy");  
    v2.push_back("kittens");  
    v2.push_back("fun");  
    v2.push_back("meowmeowmeow");  
    v2.push_back("blah");  
  
    equal_range_demo<string>( v2, "fred" );  
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );  
}  
  
```  
  
##  <a name="fill"></a>  fill  
 将相同的新值分配给指定范围中的每个元素。  
  
```  
template<class ForwardIterator, class Type>  
void fill(
    ForwardIterator first, 
    ForwardIterator last, 
    const Type& val);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种向前迭代器，用于寻址要遍历的范围内第一个元素的位置。  
  
 `last`  
 一种向前迭代器，用于寻址要遍历的范围内最后一个元素之后下一个元素的位置。  
  
 `val`  
 要分配给范围 [ `first`， `last`) 中元素的值。  
  
### <a name="remarks"></a>备注  
 目标范围必须是有效的；所有指针必须是可取消引用的，并且最后一个位置可从第一个位置通过递增到达。 其复杂性与该范围的大小呈线性关系。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_fill.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Fill the last 5 positions with a value of 2  
   fill( v1.begin( ) + 5, v1.end( ), 2 );  
  
   cout << "Modified v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )  
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )  
```  
  
##  <a name="fill_n"></a>  fill_n  
 将新值分配给以特定元素开始的范围中指定数量的元素。  
  
```  
template<class OutputIterator, class Size, class Type>  
OutputIterator fill_n(
    OutputIterator First, 
    Size Count, 
    const Type& Val);   
```  
  
### <a name="parameters"></a>参数  
 `First`  
 一种输出迭代器，用于寻址要分配值 `Val` 的范围中第一个元素的位置。  
  
 `Count`  
 指定要分配该值的元素数目的有符号或无符号整数类型。  
  
 `Val`  
 要分配给范围  [ `First`,          *First + Count*) 中的元素的值。  
  
### <a name="return-value"></a>返回值  
 如果 `Count` > 0，则为指向填充的最后一个元素后面那个元素的迭代器，否则，为指向第一个元素的迭代器。  
  
### <a name="remarks"></a>备注  
 目标范围必须是有效的；所有指针必须是可取消引用的，并且最后一个位置可从第一个位置通过递增到达。 其复杂性与该范围的大小呈线性关系。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_fill_n.cpp  
// compile using /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main()   
{  
    using namespace std;  
    vector <int> v;  
  
    for ( auto i = 0 ; i < 9 ; ++i )  
        v.push_back( 0 );  
  
    cout << "  vector v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
  
    // Fill the first 3 positions with a value of 1, saving position.  
    auto pos = fill_n( v.begin(), 3, 1 );  
  
    cout << "modified v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
  
    // Fill the next 3 positions with a value of 2, using last position.  
    fill_n( pos, 3, 2 );  
  
    cout << "modified v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
  
    // Fill the last 3 positions with a value of 3, using relative math.  
    fill_n( v.end()-3, 3, 3 );  
  
    cout << "modified v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
}  
  
```  
  
##  <a name="find"></a>  find  
 在范围中找到具有指定值的元素的第一个匹配项位置。  
  
```  
template<class InputIterator, class T>  
InputIterator find(
    InputIterator first, 
    InputIterator last,   
    const T& val);  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 用于确定要在范围中搜索其指定值的第一个元素的位置的输入迭代器。  
  
 `last`  
 用于确定要在范围中搜索其指定值的最后一个元素之后下一个元素的位置的输入迭代器。  
  
 `val`  
 要搜索的值。  
  
### <a name="return-value"></a>返回值  
 用于确定要在范围中搜索的指定值第一次出现的位置的输入迭代器。 如果找不到具有等效值的元素，则返回 `last`。  
  
### <a name="remarks"></a>备注  
 `operator==` 用于确定元素与指定值之间的匹配必须在其操作数之间施加等效关系。  
  
 有关使用 `find()` 的代码示例，请参阅 [find_if](../standard-library/algorithm-functions.md#find_if)。  
  
##  <a name="find_end"></a>  find_end  
 在范围中查找与指定序列相同的最后一个序列，或在二元谓词指定的意义上等效的最后一个序列。  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
ForwardIterator1 find_end(  
    ForwardIterator1 First1,   
    ForwardIterator1 Last1,  
    ForwardIterator2 First2,   
    ForwardIterator2 Last2);  

template<class ForwardIterator1, class ForwardIterator2, class Pred>  
ForwardIterator1 find_end(  
    ForwardIterator1 First1,   
    ForwardIterator1 Last1,  
    ForwardIterator2 First2,   
    ForwardIterator2 Last2,  
    Pred Comp);  
```  
  
### <a name="parameters"></a>参数  
 `First1`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `Last1`  
 用于确定要搜索范围中最后一个元素之后下一个元素的位置的前向迭代器。  
  
 `First2`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `Last2`  
 用于确定要搜索范围中最后一个元素之后下一个元素的位置的前向迭代器。  
  
 `Comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 用于确定 [First1, Last1) 内最后一个子序列的第一个元素的位置的前向迭代器，[First1, Last1) 与指定序列 [First2, Last2) 匹配。  
  
### <a name="remarks"></a>备注  
 `operator==` 用于确定元素与指定值之间的匹配必须在其操作数之间施加等效关系。  
  
 引用的范围必须是有效的；所有指针必须是可解除引用的，并且在每个序列内，最后一个位置可从第一个位置通过递增到达。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_find_end.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice ( int elem1, int elem2 )  
{  
   return 2 * elem1 == elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   int ii;  
   for ( ii = 1 ; ii <= 4 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 2 ; iii <= 4 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Searching v1 for a match to L1 under identity  
   vector <int>::iterator result1;  
   result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a match of L1 in v1 that begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for a match to L1 under the binary predicate twice  
   vector <int>::iterator result2;  
   result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a sequence of elements in v1 that "  
           << "are equivalent to those\n in v2 under the binary "  
           << "predicate twice and that begins at position "  
           << result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )  
List L1 = ( 5 10 15 20 )  
Vector v2 = ( 20 30 40 )  
There is a match of L1 in v1 that begins at position 7.  
There is a sequence of elements in v1 that are equivalent to those  
 in v2 under the binary predicate twice and that begins at position 8.  
```  
  
##  <a name="find_first_of"></a>  find_first_of  
 在目标范围中搜索若干值中任意值的第一个匹配项，或搜索在二元谓词指定的意义上等效于指定元素集的若干元素中任意元素的第一个匹配项。  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
ForwardIterator1 find_first_of(    
    ForwardIterator1  first1,  
    ForwardIterator1 Last1,  
    ForwardIterator2  first2,  
    ForwardIterator2 Last2);  
  
template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>  
ForwardIterator1 find_first_of(  
    ForwardIterator1  first1,  
    ForwardIterator1 Last1,  
    ForwardIterator2  first2,  
    ForwardIterator2 Last2,  
    BinaryPredicate  comp);  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `last1`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的前向迭代器。  
  
  `first2`  
 用于确定要匹配范围中的第一个元素的位置的前向迭代器。  
  
 `last2`  
 用于确定要匹配范围中的最后元素之后的位置的前向迭代器。  
  
 `comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 用于确定第一个子序列的第一个元素的位置的前向迭代器，这个子序列与指定序列匹配或在二元谓词所指定的某个条件下等效。  
  
### <a name="remarks"></a>备注  
 `operator==` 用于确定元素与指定值之间的匹配必须在其操作数之间施加等效关系。  
  
 引用的范围必须是有效的；所有指针必须是可解除引用的，并且在每个序列内，最后一个位置可从第一个位置通过递增到达。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_find_first_of.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice ( int elem1, int elem2 )  
{  
   return 2 * elem1 == elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   int ii;  
   for ( ii = 3 ; ii <= 4 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 2 ; iii <= 4 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Searching v1 for first match to L1 under identity  
   vector <int>::iterator result1;  
   result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is at least one match of L1 in v1"  
           << "\n and the first one begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for a match to L1 under the binary predicate twice  
   vector <int>::iterator result2;  
   result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a sequence of elements in v1 that "  
           << "are equivalent\n to those in v2 under the binary "  
           << "predicate twice\n and the first one begins at position "  
           << result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )  
List L1 = ( 15 20 )  
Vector v2 = ( 20 30 40 )  
There is at least one match of L1 in v1  
 and the first one begins at position 3.  
There is a sequence of elements in v1 that are equivalent  
 to those in v2 under the binary predicate twice  
 and the first one begins at position 2.  
```  
  
##  <a name="find_if"></a>  find_if  
 在范围中找到满足指定条件的元素的第一个匹配项位置。  
  
```  
template<class InputIterator, class Predicate>  
InputIterator find_if(
    InputIterator first, 
    InputIterator last, 
    Predicate pred);  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 用于确定要搜索范围中的第一个元素的位置的输入迭代器。  
  
 `last`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的输入迭代器。  
  
 `pred`  
 用户定义的谓词函数对象或 [lambda 表达式](../cpp/lambda-expressions-in-cpp.md)，用于定义要搜索的元素应满足的条件。 谓词采用单个参数并返回 `true`（满足条件）或 `false`（不满足条件）。 `pred` 的签名必须是有效的 `bool pred(const T& arg);`，其中，`T` 是 `InputIterator` 在取消引用时可隐式转换为的类型。 显示 `const` 关键字的目的仅为说明函数对象或 lambda 不应修改参数。  
  
### <a name="return-value"></a>返回值  
 用于引用范围中满足谓词所指定条件的元素（谓词产生的结果为 `true`）的输入迭代器。 如果找不到满足谓词的元素，则返回 `last`。  
  
### <a name="remarks"></a>备注  
 此模板函数是算法 [find](../standard-library/algorithm-functions.md#find) 的泛化，它将“等于指定值”谓词替换为任何谓词。 有关相反逻辑（找到不满足谓词的第一个元素），请参阅 [find_if_not](../standard-library/algorithm-functions.md#find_if_not)。  
  
### <a name="example"></a>示例  
  
```cpp  
// cl.exe /W4 /nologo /EHsc /MTd  
#include <vector>  
#include <algorithm>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
    cout << endl;  
}  
  
// Test std::find()  
template <class InputIterator, class T>  
void find_print_result(InputIterator first, InputIterator last, const T& value) {  
  
    // call <algorithm> std::find()  
    auto p = find(first, last, value);  
  
    cout << "value " << value;  
    if (p == last) {  
        cout << " not found." << endl;  
    } else {  
        cout << " found." << endl;  
    }  
}  
  
// Test std::find_if()  
template <class InputIterator, class Predicate>  
void find_if_print_result(InputIterator first, InputIterator last,  
    Predicate Pred, const string& Str) {  
  
    // call <algorithm> std::find_if()  
    auto p = find_if(first, last, Pred);  
  
    if (p == last) {  
        cout << Str << " not found." << endl;  
    } else {  
        cout << "first " << Str << " found: " << *p << endl;  
    }  
}  
  
// Function to use as the UnaryPredicate argument to find_if() in this example  
bool is_odd_int(int i) {  
    return ((i % 2) != 0);  
}  
  
int main()  
{  
    // Test using a plain old array.  
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
    cout << "array x[] contents: ";  
    print(x);  
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.  
    cout << "Test std::find() with array..." << endl;  
    find_print_result(begin(x), end(x), 10);  
    find_print_result(begin(x), end(x), 42);  
    cout << "Test std::find_if() with array..." << endl;  
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name  
    find_if_print_result(begin(x), end(x), // lambda  
        [](int i){ return ((i % 2) == 0); }, "even integer");  
  
    // Test using a vector.  
    vector<int> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back((i + 1) * 10);  
    }  
    cout << endl << "vector v contents: ";  
    print(v);  
    cout << "Test std::find() with vector..." << endl;  
    find_print_result(v.begin(), v.end(), 20);  
    find_print_result(v.begin(), v.end(), 12);  
    cout << "Test std::find_if() with vector..." << endl;  
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");  
    find_if_print_result(v.begin(), v.end(), // lambda  
        [](int i){ return ((i % 2) == 0); }, "even integer");  
}  
  
```  
  
##  <a name="find_if_not"></a>  find_if_not  
 返回指示的范围中不满足条件的第一个元素。  
  
```  
template<class InputIterator, class Predicate>  
InputIterator find_if_not(
    InputIterator first, 
    InputIterator last,   
    Predicate pred);  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 用于确定要搜索范围中的第一个元素的位置的输入迭代器。  
  
 `last`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的输入迭代器。  
  
 `pred`  
 用户定义谓词函数对象或 [lambda 表达式](../cpp/lambda-expressions-in-cpp.md)，用于定义要搜索的元素不满足的条件。 谓词采用单个参数并返回 `true`（满足条件）或 `false`（不满足条件）。 `pred` 的签名必须是有效的 `bool pred(const T& arg);`，其中，`T` 是 `InputIterator` 在取消引用时可隐式转换为的类型。 显示 `const` 关键字的目的仅为说明函数对象或 lambda 不应修改参数。  
  
### <a name="return-value"></a>返回值  
 用于引用范围中不满足由谓词指定的条件（谓词产生的结果为 `false`）的第一个元素的输入迭代器。 如果所有元素均满足该谓词（对于每个元素，谓词产生的结果为 `true`），并返回 `last`。  
  
### <a name="remarks"></a>备注  
 此模板函数是算法 [find](../standard-library/algorithm-functions.md#find) 的泛化，它将“等于指定值”谓词替换为任何谓词。 有关相反逻辑（找到满足谓词的第一个元素），请参阅 [find_if](../standard-library/algorithm-functions.md#find_if)。  
  
 有关易于适应 `find_if_not()` 的代码示例的信息，请参阅 [find_if](../standard-library/algorithm-functions.md#find_if)。  
  
##  <a name="for_each"></a>  for_each  
 将指定的函数对象按向前顺序应用于范围中的每个元素并返回此函数对象。  
  
```  
template<class InputIterator, class Function>  
Function for_each(
    InputIterator first, 
    InputIterator last, 
    Function _Func);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，用于寻址要操作的范围中第一个元素的位置。  
  
 `last`  
 一种输入迭代器，用于寻址要操作的范围中最后一个元素之后下一个元素的位置。  
  
 `_Func`  
 用户定义的应用于范围内每个元素的函数对象。  
  
### <a name="return-value"></a>返回值  
 函数对象应用到范围内所有元素后的副本。  
  
### <a name="remarks"></a>备注  
 算法 `for_each` 非常灵活，允许以用户指定的不同方式修改范围内的每个元素。 模板化函数可能通过传递不同的参数在已修改的窗体中重用。 用户定义的函数可能会累积该算法在处理范围中所有元素后可能返回的内部状态中的信息。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，通过递增必须可从第一个位置到达最后一个位置。  
  
 复杂性是线性的最多 ( `last`  -   `first`) 比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_for_each.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
// The function object multiplies an element by a Factor  
template <class Type>  
class MultValue  
{  
private:  
   Type Factor;   // The value to multiply by  
public:  
   // Constructor initializes the value to multiply by  
   MultValue ( const Type& val ) : Factor ( val ) {  
   }  
  
   // The function call for the element to be multiplied  
   void operator ( ) ( Type& elem ) const  
   {  
      elem *= Factor;  
   }  
};  
  
// The function object to determine the average  
class Average  
{  
private:  
   long num;      // The number of elements  
   long sum;      // The sum of the elements  
public:  
   // Constructor initializes the value to multiply by  
   Average ( ) : num ( 0 ) , sum ( 0 )  
   {  
   }  
  
   // The function call to process the next elment  
   void operator ( ) ( int elem ) \  
   {  
      num++;      // Increment the element count  
      sum += elem;   // Add the value to the partial sum  
   }  
  
   // return Average  
   operator double ( )  
   {  
      return  static_cast <double> (sum) /  
      static_cast <double> (num);  
   }  
};  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   // Constructing vector v1  
   int i;  
   for ( i = -4 ; i <= 2 ; i++ )  
   {  
      v1.push_back(  i );  
   }  
  
   cout << "Original vector  v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Using for_each to multiply each element by a Factor  
   for_each ( v1.begin ( ) , v1.end ( ) , MultValue<int> ( -2 ) );  
  
   cout << "Multiplying the elements of the vector v1\n "  
        <<  "by the factor -2 gives:\n v1mod1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // The function object is templatized and so can be  
   // used again on the elements with a different Factor  
   for_each (v1.begin ( ) , v1.end ( ) , MultValue<int> (5 ) );  
  
   cout << "Multiplying the elements of the vector v1mod\n "  
        <<  "by the factor 5 gives:\n v1mod2 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // The local state of a function object can accumulate  
   // information about a sequence of actions that the  
   // return value can make available, here the Average  
   double avemod2 = for_each ( v1.begin ( ) , v1.end ( ) ,  
      Average ( ) );  
   cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "  
        << avemod2 << "." << endl;  
}  
```  
  
```Output  
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).  
Multiplying the elements of the vector v1  
 by the factor -2 gives:  
 v1mod1 = ( 8 6 4 2 0 -2 -4 ).  
Multiplying the elements of the vector v1mod  
 by the factor 5 gives:  
 v1mod2 = ( 40 30 20 10 0 -10 -20 ).  
The average of the elements of v1 is:  
 Average ( v1mod2 ) = 10.  
```  
  
##  <a name="generate"></a>  generate  
 将函数对象生成的值分配给范围中的每个元素。  
  
```  
template<class ForwardIterator, class Generator>  
void generate(
    ForwardIterator first, 
    ForwardIterator last, 
    Generator _Gen);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种前向迭代器，用于寻址要分配值的范围中第一个元素的位置。  
  
 `last`  
 一种前向迭代器，用于寻址要分配值的范围中最后一个元素之后下一个元素的位置。  
  
 `_Gen`  
 用于生成要分配到范围中的每个元素的值的未使用任何自变量调用的函数对象。  
  
### <a name="remarks"></a>备注  
 为范围中的每个元素调用函数对象，并且每次调用它时，都无需返回相同的值。 例如，它可能会读取文件或引用和修改本地状态。 生成器的结果类型必须可以转换为范围中转发迭代器的值类型。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，通过递增必须可从第一个位置到达最后一个位置。  
  
 复杂性是线性的使用完全 ( `last`  -   `first`) 调用所需的生成器。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_generate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Assigning random values to vector integer elements  
   vector <int> v1 ( 5 );  
   vector <int>::iterator Iter1;  
   deque <int> deq1 ( 5 );  
   deque <int>::iterator d1_Iter;  
  
   generate ( v1.begin ( ), v1.end ( ) , rand );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Assigning random values to deque integer elements  
   generate ( deq1.begin ( ), deq1.end ( ) , rand );  
  
   cout << "Deque deq1 is ( " ;  
   for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )  
      cout << *d1_Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 41 18467 6334 26500 19169 ).  
Deque deq1 is ( 15724 11478 29358 26962 24464 ).  
```  
  
##  <a name="generate_n"></a>  generate_n  
 将函数对象生成的值分配给范围中指定数量的元素，并返回到超出最后一个分配值的下一位置。  
  
```  
template<class OutputIterator, class Diff, class Generator>  
void generate_n( 
    OutputIterator First, 
    Diff Count, 
    Generator Gen);  
```  
  
### <a name="parameters"></a>参数  
 `First`  
 寻址要分配值的范围中的第一个元素位置的输出迭代器。  
  
 `Count`  
 指定生成器函数要将值分配到的元素数的有符号或无符号整型。  
  
 `Gen`  
 用于生成要分配到范围中的每个元素的值的未使用任何自变量调用的函数对象。  
  
### <a name="remarks"></a>备注  
 为范围中的每个元素调用函数对象，并且每次调用它时，都无需返回相同的值。 例如，它可能会读取文件或引用和修改本地状态。 生成器的结果类型必须可以转换为范围中转发迭代器的值类型。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，通过递增必须可从第一个位置到达最后一个位置。  
  
 复杂性是线性的，对将需要的生成器具有确切的 `Count` 次调用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cl.exe /EHsc /nologo /W4 /MTd  
#include <vector>  
#include <deque>  
#include <iostream>  
#include <string>  
#include <algorithm>  
#include <random>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    const int elemcount = 5;  
    vector<int> v(elemcount);  
    deque<int> dq(elemcount);  
  
    // Set up random number distribution  
    random_device rd;  
    mt19937 engine(rd());  
    uniform_int_distribution<int> dist(-9, 9);  
  
    // Call generate_n, using a lambda for the third parameter  
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });  
    print("vector v is: ", v);  
  
    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });  
    print("deque dq is: ", dq);  
}  
  
```  
  
##  <a name="includes"></a>  includes  
 测试一个排序的范围是否包含另一排序范围中的所有元素，其中元素之间的排序或等效条件可通过二元谓词指定。  
  
```  
template<class InputIterator1, class InputIterator2>  
bool includes(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2);  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool includes(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    BinaryPredicate comp );  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一种输入迭代器，用于寻址第一个元素在两个已排序源范围的第一个中的位置，以便测试第二个已排序源范围的所有元素是否包含在第一个中。  
  
 `last1`  
 一种输入迭代器，用于寻址在两个已排序源范围的第一个中最后一个元素之后下一个元素的位置，以便测试第二个已排序源范围中的所有元素是否包含在第一个中。  
  
  `first2`  
 一种输入迭代器，用于寻址第一个元素在两个连续已排序源范围的第二个中的位置，以便测试第二个已排序源范围中的所有元素是否包含在第一个中。  
  
 `last2`  
 一种输入迭代器，用于寻址在两个连续已排序源范围的第二个中最后一个元素之后的下一个元素的位置，以便测试第二个已排序源范围中的所有元素是否包含在第一个中。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 如果第一个排序范围包含第二个排序范围中的所有元素，则为 **true**，否则，为 **false**。  
  
### <a name="remarks"></a>备注  
 考虑这种测试的另一种方式是，它确定第二个源范围是否为第一个源范围的子集。  
  
 引用的已排序源范围必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 必须按照该算法对合并范围排序时要使用的相同顺序对已排序源范围分别进行排列，作为应用该算法的前置条件。  
  
 **merge**算法不会修改源范围。  
  
 输入迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 更准确的说，该算法测试在指定二元谓词下第一个已排序范围中的所有元素，是否与第二个已排序范围中的所有元素具有相同的排序。  
  
 算法的复杂性是线性的最多 2 \* (( *last1-first1*)-(* last2-first2 *))-1 比较对于非空源范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_includes.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b;  
   vector <int>::iterator Iter1a,  Iter1b;  
  
   // Constructing vectors v1a & v1b with default less-than ordering  
   int i;  
   for ( i = -2 ; i <= 4 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-2 ; ii <= 3 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        << "binary predicate less than is v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b );  
   vector <int>::iterator Iter2a,  Iter2b;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
   v2a.pop_back ( );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is v2a = ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is v2b = ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ;  
   vector <int>::iterator Iter3a, Iter3b;  
   reverse (v3a.begin( ), v3a.end( ) );  
   v3a.pop_back ( );  
   v3a.pop_back ( );  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3a = ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3b = ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To test for inclusion under an asscending order  
   // with the default binary predicate less <int> ( )  
   bool Result1;  
   Result1 = includes ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) );  
   if ( Result1 )  
      cout << "All the elements in vector v1b are "  
           << "contained in vector v1a." << endl;  
   else  
      cout << "At least one of the elements in vector v1b "  
           << "is not contained in vector v1a." << endl;  
  
   // To test for inclusion under descending  
   // order specify binary predicate greater<int>( )  
   bool Result2;  
   Result2 = includes ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) , greater <int> ( ) );  
   if ( Result2 )  
      cout << "All the elements in vector v2b are "  
           << "contained in vector v2a." << endl;  
   else  
      cout << "At least one of the elements in vector v2b "  
           << "is not contained in vector v2a." << endl;  
  
   // To test for inclusion under a user  
   // defined binary predicate mod_lesser  
   bool Result3;  
   Result3 = includes ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
   if ( Result3 )  
      cout << "All the elements in vector v3b are "  
           << "contained under mod_lesser in vector v3a."  
           << endl;  
   else  
      cout << "At least one of the elements in vector v3b is "  
           << " not contained under mod_lesser in vector v3a."   
           << endl;  
}  
```  
  
```Output  
Original vector v1a with range sorted by the  
 binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).  
Original vector v1b with range sorted by the  
 binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).  
Original vector v2a with range sorted by the  
 binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).  
Original vector v2b with range sorted by the  
 binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).  
Original vector v3a with range sorted by the  
 binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).  
Original vector v3b with range sorted by the  
 binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).  
All the elements in vector v1b are contained in vector v1a.  
At least one of the elements in vector v2b is not contained in vector v2a.  
At least one of the elements in vector v3b is  not contained under mod_lesser in vector v3a.  
```  
  
##  <a name="inplace_merge"></a>  inplace_merge  
 将两个连续的排序范围中的元素合并为一个排序范围，其中排序条件可通过二元谓词指定。  
  
```  
template<class BidirectionalIterator>  
void inplace_merge(      
    BidirectionalIterator first,   
    BidirectionalIterator middle,  
    BidirectionalIterator last);  
  
template<class BidirectionalIterator, class Predicate>  
void inplace_merge(  
    BidirectionalIterator first,   
    BidirectionalIterator middle,  
    BidirectionalIterator last,  
    Predicate comp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，用于寻址要合并且排序为一个范围的两个连续已排序源范围中，第一个源范围内第一个元素的位置。  
  
 `middle`  
 一种双向迭代器，用于寻址要合并且排序为一个范围的两个连续已排序源范围中，第二个源范围内第一个元素的位置。  
  
 `last`  
 一种双向迭代器，用于寻址要合并且排序为一个范围的两个连续已排序源范围中，第二个源范围内最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="remarks"></a>备注  
 引用的已排序连续范围必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 必须按照 `inplace_merge` 算法对合并范围排序时要使用的相同顺序对已排序连续范围分别进行排列，作为应用该算法的前置条件。 该操作保持不变，因为每个范围内元素的相对顺序均已保留。 当两个源范围中有相等的元素时，在合并范围中，第一个范围中的元素优先于第二个范围中的元素。  
  
 因为该算法会向临时缓冲区分配内存，所以复杂性取决于可用内存。 如果提供足够的内存，最佳情况下是线性的 (* 姓氏-名字*)-1 比较; 如果辅助内存不可用，最坏情况下是*N*日志*(N)*，其中*N* = (* 姓氏-名字*)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_inplace_merge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      //For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1, Iter2, Iter3;  
  
   // Constructing vector v1 with default less-than ordering  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii =-5 ; ii <= 0 ; ii++ )  
   {  
      v1.push_back(  ii  );  
   }  
  
   cout << "Original vector v1 with subranges sorted by the\n "  
        <<  "binary predicate less than is  v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Constructing vector v2 with ranges sorted by greater  
   vector <int> v2 ( v1 );  
   vector <int>::iterator break2;  
   break2 = find ( v2.begin ( ) , v2.end ( ) , -5 );  
   sort ( v2.begin ( ) , break2 , greater<int> ( ) );  
   sort ( break2 , v2.end ( ) , greater<int> ( ) );  
   cout << "Original vector v2 with subranges sorted by the\n "  
        << "binary predicate greater is v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Constructing vector v3 with ranges sorted by mod_lesser  
   vector <int> v3 ( v1 );  
   vector <int>::iterator break3;  
   break3 = find ( v3.begin ( ) , v3.end ( ) , -5 );  
   sort ( v3.begin ( ) , break3 , mod_lesser );  
   sort ( break3 , v3.end ( ) , mod_lesser );  
   cout << "Original vector v3 with subranges sorted by the\n "  
        << "binary predicate mod_lesser is v3 = ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
  
   vector <int>::iterator break1;  
   break1 = find (v1.begin ( ) , v1.end ( ) , -5 );  
   inplace_merge ( v1.begin( ), break1, v1.end( ) );  
   cout << "Merged inplace with default order,\n vector v1mod = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To merge inplace in descending order, specify binary   
   // predicate greater<int>( )  
   inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );  
   cout << "Merged inplace with binary predicate greater specified,\n "  
        << "vector v2mod = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Applying a user defined (UD) binary predicate mod_lesser  
   inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );  
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "  
        << "vector v3mod = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 with subranges sorted by the  
 binary predicate less than is  v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )  
Original vector v2 with subranges sorted by the  
 binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )  
Original vector v3 with subranges sorted by the  
 binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )  
Merged inplace with default order,  
 vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )  
Merged inplace with binary predicate greater specified,  
 vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )  
Merged inplace with binary predicate mod_lesser specified,  
 vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )  
```  
  
##  <a name="is_heap"></a>  is_heap  
 如果指定范围中的元素形成堆，则返回 `true`。  
  
```  
template<class RandomAccessIterator>  
bool is_heap(  
    RandomAccessIterator first,  
    RandomAccessIterator last);  

template<class RandomAccessIterator, class BinaryPredicate>  
bool is_heap(  
    RandomAccessIterator first,  
    RandomAccessIterator last,  
    BinaryPredicate comp);   
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种随机访问迭代器，指示在一个范围内检查堆的开始位置。  
  
 `last`  
 一种随机访问迭代器，指示一个范围内的结束位置。  
  
 `comp`  
 要测试或者排序元素的条件。 二元谓词采用单个参数并返回`true`或`false`。  
  
### <a name="return-value"></a>返回值  
 如果指定范围中的元素形成堆，则返回 `true`；否则，返回 `false`。  
  
### <a name="remarks"></a>备注  
 第一个模板函数返回 [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(` `first``,` `last``) ==` `last`。  
  
 第二个模板函数返回  
  
 `is_heap_until` `(`  `first` `,`  `last` `,`  `comp` `) ==`  `last`。  
  
##  <a name="is_heap_until"></a>  is_heap_until  
 返回一个迭代器，它位于范围 [`begin`,`end`) 中不满足堆排序条件的第一个元素处；如果范围形成一个堆，则返回 `end`。  
  
```  
template<class RandomAccessIterator>  
RandomAccessIterator is_heap_until(  
    RandomAccessIterator begin,   
    RandomAccessIterator end);  
    
template<class RandomAccessIterator, class BinaryPredicate>   
RandomAccessIterator is_heap_until(  
    RandomAccessIterator begin,   
    RandomAccessIterator end,   
    BinaryPredicate compare);  
```  
  
### <a name="parameters"></a>参数  
 `begin`  
 一个随机访问迭代器，它为堆指定范围中要检查的第一个元素。  
  
 `end`  
 一个随机访问迭代器，它为堆指定要检查的范围的末尾。  
  
 `compare`  
 一个二元谓词，它指定定义堆的严格弱排序条件。 未指定 `compare` 时，默认谓词为 `std::less<>`。  
  
### <a name="return-value"></a>返回值  
 如果指定的范围形成堆或包含一个或更少元素，则返回 `end`。 否则，为找到的不满足该堆条件的第一个元素返回迭代器。  
  
### <a name="remarks"></a>备注  
 第一个模板函数返回 `[``begin``,` `end``]` 中的最后一个迭代器 `next`，其中 `[``begin``, next)` 是由函数对象 `std::less<>` 排序的一个堆。 如果距离 `end` `-` `begin` `< 2`，则函数返回 `end`。  
  
 第二个模板函数行为与第一个相同，只不过它将谓词 `compare`（而非 `std::less<>`）作为堆排序条件。  
  
##  <a name="is_partitioned"></a>  is_partitioned  
 如果给定范围中对某个条件测试为 `true` 的所有元素在测试为 `true` 的所有元素之前，则返回 `false`。  
  
```  
template<class InputIterator, class BinaryPredicate>  
bool is_partitioned(  
    InputIterator first,   
    InputIterator last,  
    BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指示一个范围开始检查条件的位置。  
  
 `last`  
 一种输入迭代器，指示范围的结束位置。  
  
 `comp`  
 要测试的条件。 由用户定义的谓词函数对象提供，用于定义被搜索元素要满足的条件。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="return-value"></a>返回值  
 如果给定范围中对某个条件测试为 `true` 的所有元素在测试为 `false` 的所有元素之前，将返回 True，否则，返回 `false`。  
  
### <a name="remarks"></a>备注  
 仅当 `[` `first``,` `last``)` 中的所有元素通过 `comp` 进行分区时，模板函数才返回 `true`；即，`comp``(X)` 为 true 的 `[` `first``,` `last``)` 中的所有元素 `X` 在 `comp``(Y)` 为 `false` 的所有元素 `Y` 之前。  
  
##  <a name="is_permutation"></a>  is_permutation  
 如果这两个范围包含相同元素（无论元素是否处于相同顺序），则返回 true。 在 C++14 代码中使用双范围重载，因为对第二个范围仅采用单个迭代器的重载在第二个范围长于第一个范围时不会检测到差异，并且会在第二个范围短于第一个范围时导致未定义的行为。  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2, 
    Predicate Pred);

// C++14  
template<class ForwardIterator1, class ForwardIterator2>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2, 
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2, 
    ForwardIterator2 Last2, 
    Predicate Pred);  
```  
  
### <a name="parameters"></a>参数  
 `First1`  
 引用范围的第一个元素的向前迭代器。  
  
 `Last1`  
 引用范围最后一个元素过去一个元素的向前迭代器。  
  
 `First2`  
 引用第二个范围的第一个元素的向前迭代器（用于比较）。  
  
 `Last2`  
 引用第二个范围最后一个元素过去一个元素的向前迭代器（用于比较）。  
  
 `Pred`  
 针对等效性进行测试并返回 `bool` 的谓词。  
  
### <a name="return-value"></a>返回值  
 当范围可以重新排列以便根据比较运算符谓词相同时为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 `is_permutation` 在最坏情况下具有二次复杂性。  
  
 第一个模板函数假设以 `First2` 开头的范围中的元素与 [ `First1`, `Last1`) 指定的范围中的元素一样多。 如果第二个范围中存在更多元素，则忽略它们；如果元素更少，则会发生未定义的行为。 第三个模板函数（C++14 及更高版本）不会进行此假设。  仅当对于 [`First1`, `Last1`) 指定的范围中的每个元素 X，X == Y 的相同范围中的元素 Y 数量与从 `First2` 或 [`First2, Last2).` 开始的范围中的数量相同时，两者才返回 `true`。在这里，`operator==` 必须在其操作数之间执行成对比较。  
  
 第二个和第四个模板函数的行为相同，只不过它们会将 `operator==(X, Y)` 替换为 `Pred(X, Y)`。 若要行为正确，谓词必须是对称、自反且可传递。  
  
### <a name="example"></a>示例  
  下面的示例演示如何使用 `is_permutation`：  
  
```cpp  
#include <vector>  
#include <iostream>  
#include <algorithm>  
#include <string>  
  
using namespace std;  
  
int main()  
{  
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };  
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };  
  
    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };  
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };  
  
    cout << "(1) Compare using built-in == operator: ";  
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),  
        vec_2.begin(), vec_2.end()) << endl; // true  
  
    cout << "(2) Compare after modifying vec_2: ";  
    vec_2[0] = 6;  
    cout << is_permutation(vec_1.begin(), vec_1.end(),  
        vec_2.begin(), vec_2.end()) << endl; // false  
  
    // Define equivalence as "both are odd or both are even"  
    cout << "(3) vec_3 is a permutation of vec_4: ";  
    cout << is_permutation(vec_3.begin(), vec_3.end(),  
        vec_4.begin(), vec_4.end(),  
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true  
  
    // Initialize a vector using the 's' string literal to specify a std::string  
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };  
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };  
  
    // Define equivalence as "first letters are equal":  
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),  
        [](const string& lhs, const string& rhs)  
    {  
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator  
    });  
  
    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true  
  
    cout << "Press a letter" << endl;  
    char c;  
    cin >> c;  
  
    return 0;  
}  
  
```  
  
##  <a name="is_sorted"></a>  is_sorted  
 如果指定范围中的元素按顺序排序，则返回 `true`。  
  
```  
template<class ForwardIterator>  
bool is_sorted(  
    ForwardIterator first,   
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>  
bool is_sorted(  
    ForwardIterator first,   
    ForwardIterator last,   
    BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种前向迭代器，指示范围开始检查的位置。  
  
 `last`  
 一种前向迭代器，指示范围的结束位置。  
  
 `comp`  
 要进行测试以确定两个元素之间顺序的条件。 谓词采用一个参数并返回 `true` 或 `false`。 此设置执行与 `operator<` 相同的任务。  
  
### <a name="remarks"></a>备注  
 第一个模板函数返回 [is_sorted_until](http://msdn.microsoft.com/en-us/bbad99d0-deaa-4fe6-ae58-eb5b3e4dded0)`(` `first``,` `last``) ==` `last`。 operator< 函数执行排序比较。  
  
 第二个模板函数返回 `is_sorted_until``(` `first``,` `last``,` `comp``) ==` `last`。 `comp` 谓词函数执行排序比较。  
  
##  <a name="is_sorted_until"></a>  is_sorted_until  
 返回一个 `ForwardIterator`，设置为指定范围中按顺序排序的最后一个元素。  
  
 第二个版本可让你提供一个 `BinaryPredicate` 函数，当两个给定元素按顺序排序时，返回 `true`；否则，返回 `false`。  
  
```  
template<class ForwardIterator>  
    ForwardIterator is_sorted_until(  
        ForwardIterator first,   
        ForwardIterator last  
    );  
template<class ForwardIterator, class BinaryPredicate>  
    ForwardIterator is_sorted_until(  
        ForwardIterator first,   
        ForwardIterator last,   
        BinaryPredicate comp  
    );  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种前向迭代器，指示范围开始检查的位置。  
  
 `last`  
 一种前向迭代器，指示范围的结束位置。  
  
 `comp`  
 要进行测试以确定两个元素之间顺序的条件。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="return-value"></a>返回值  
 返回 `ForwardIterator`，设置为最后一个元素按顺序排序。 排序的序列从 `first` 开始。  
  
### <a name="remarks"></a>备注  
 第一个模板函数返回 `[` `first``,` `last``]` 中的最后一个迭代器 `next`，以便 `[` `first``, next)` 是由 `operator<` 排序的一个排序序列。 如果 `distance()` `< 2`，该函数将返回 `last`。  
  
 第二个模板函数的行为相同，只不过它将 `operator<(X, Y)` 替换为 `comp``(X, Y)`。  
  
##  <a name="iter_swap"></a>  iter_swap  
 交换由一对指定迭代器引用的两个值。  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );  
  
```  
  
### <a name="parameters"></a>参数  
 `left`  
 其值将进行交换的其中一个前向迭代器。  
  
 `right`  
 其值将进行交换的前向迭代器中的第二个前向迭代器。  
  
### <a name="remarks"></a>备注  
 `swap` 应优先于 **iter_swap** 使用，它包含在 C++ Standard 中用于实现向后兼容。 如果 `Fit1` 和 `Fit2` 是前向迭代器，则 `iter_swap` ( `Fit1`, `Fit2` ) 等效于 `swap` ( * `Fit1`, \* `Fit2` )。  
  
 输入前向迭代器的值类型必须具有相同的值。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_iter_swap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) { m_nVal =  
   rhs.m_nVal; return *this; }  
   bool operator<( const CInt& rhs ) const  
      { return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt(" << rhs.m_nVal << ")";  
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )  
      elem1 = - elem1;  
   if ( elem2 < 0 )  
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   CInt c1 = 5, c2 = 1, c3 = 10;  
   deque<CInt> deq1;  
   deque<CInt>::iterator d1_Iter;  
  
   deq1.push_back ( c1 );  
   deq1.push_back ( c2 );  
   deq1.push_back ( c3 );  
  
   cout << "The original deque of CInts is deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   // Exchanging first and last elements with iter_swap  
   iter_swap ( deq1.begin ( ) , --deq1.end ( ) );  
  
   cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   // Swapping back first and last elements with swap  
   swap ( *deq1.begin ( ) , *(deq1.end ( ) -1 ) );  
  
   cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   // Swapping a vector element with a deque element  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
   deque <int> deq2;  
   deque <int>::iterator d2_Iter;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 4 ; ii <= 5 ; ii++ )  
   {  
      deq2.push_back( ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Deque deq2 is ( " ;  
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )  
      cout << *d2_Iter << " ";  
   cout << ")." << endl;  
  
   iter_swap ( v1.begin ( ) , deq2.begin ( ) );  
  
   cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl << " & deque deq2 is: deq2 = ( ";  
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )  
      cout << *d2_Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).  
The deque of CInts with first & last elements swapped is:  
 deq1 = ( CInt(10), CInt(1), CInt(5) ).  
The deque of CInts with first & last elements swapped back is:  
 deq1 = ( CInt(5), CInt(1), CInt(10) ).  
Vector v1 is ( 0 1 2 3 ).  
Deque deq2 is ( 4 5 ).  
After exchanging first elements,  
 vector v1 is: v1 = ( 4 1 2 3 ).  
 & deque deq2 is: deq2 = ( 0 5 ).  
```  
  
##  <a name="lexicographical_compare"></a>  lexicographical_compare  
 逐个元素比较两个序列以确定其中的较小序列。  
  
```  
template<class InputIterator1, class InputIterator2>  
 bool lexicographical_compare(  
     InputIterator1  first1,  
     InputIterator1 Last1,  
     InputIterator2  first2,  
     InputIterator2 Last2  );  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool lexicographical_compare(  
     InputIterator1  first1,  
     InputIterator1 Last1,  
     InputIterator2  first2,  
     InputIterator2 Last2,  
     BinaryPredicate  comp  );  
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一种输入迭代器，用于寻址要比较的第一个范围中第一个元素的位置。  
  
 `last1`  
 一种输入迭代器，用于寻址要比较的第一个范围中最后一个元素之后下一个元素的位置。  
  
  `first2`  
 一种输入迭代器，用于寻址要比较的第二个范围中第一个元素的位置。  
  
 `last2`  
 一种输入迭代器，用于寻址要比较的第二个范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 如果第一个范围按字典顺序小于第二个范围，则为 **true**；否则，为 **false**。  
  
### <a name="remarks"></a>备注  
 序列之间按字典顺序进行的比较将逐个比较元素，直到：  
  
-   它查找到两个不相等的相应元素，比较结果作为序列之间比较的结果。  
  
-   未找到任何不相等的元素，但一个序列的元素数比另一个序列多，并且较短的序列小于较长的序列。  
  
-   未找到任何不相等的元素，并且序列具有相同的元素数，因此序列相等，比较的结果为 false。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_lex_comp.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice ( int elem1, int elem2 )  
{  
   return 2 * elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   int ii;  
   for ( ii = 0 ; ii <= 6 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 0 ; iii <= 5 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Self lexicographical_comparison of v1 under identity  
   bool result1;  
   result1 = lexicographical_compare (v1.begin( ), v1.end( ),  
                  v1.begin( ), v1.end( ) );  
   if ( result1 )  
      cout << "Vector v1 is lexicographically_less than v1." << endl;  
   else  
      cout << "Vector v1 is not lexicographically_less than v1." << endl;  
  
   // lexicographical_comparison of v1 and L2 under identity  
   bool result2;  
   result2 = lexicographical_compare (v1.begin( ), v1.end( ),  
                  L1.begin( ), L1.end( ) );  
   if ( result2 )  
      cout << "Vector v1 is lexicographically_less than L1." << endl;  
   else  
      cout << "Vector v1 is lexicographically_less than L1." << endl;  
  
   bool result3;  
   result3 = lexicographical_compare (v1.begin( ), v1.end( ),  
                  v2.begin( ), v2.end( ), twice );  
   if ( result3 )  
      cout << "Vector v1 is lexicographically_less than v2 "  
           << "under twice." << endl;  
   else  
      cout << "Vector v1 is not lexicographically_less than v2 "  
           << "under twice." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 )  
List L1 = ( 0 5 10 15 20 25 30 )  
Vector v2 = ( 0 10 20 30 40 50 )  
Vector v1 is not lexicographically_less than v1.  
Vector v1 is lexicographically_less than L1.  
Vector v1 is not lexicographically_less than v2 under twice.  
```  
  
##  <a name="lower_bound"></a>  lower_bound  
 在排序的范围中查找其值大于或等效于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。  
  
```  
 template<class ForwardIterator, class Type>  
 ForwardIterator lower_bound(  
     ForwardIterator first,  
     ForwardIterator last,  
     const Type& value );  
  
template<class ForwardIterator, class Type, class BinaryPredicate>  
ForwardIterator lower_bound(   
     ForwardIterator first,  
     ForwardIterator last,  
     const Type& value,  
     BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `last`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的前向迭代器。  
  
 `value`  
 正在已排序范围中搜索其第一个位置或可能的第一个位置的值。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 已排序范围中其值大于或等效于指定值的第一个元素位置处的前向迭代器，其中等效性通过二元谓词指定。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有迭代器必须可取消引用，并且在序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 已排序的范围是使用 `lower_bound` 的前置条件，其中顺序与通过二元谓词指定的顺序相同。  
  
 `lower_bound` 算法不会修改该范围。  
  
 前向迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。  
  
 该算法的复杂性与随机访问迭代器是对数关系，而对于其他迭代器是线性关系，并且与步骤数成比例 ( `last - first`)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_lower_bound.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser( int elem1, int elem2 )  
{  
    if ( elem1 < 0 )  
        elem1 = - elem1;  
    if ( elem2 < 0 )  
        elem2 = - elem2;  
    return elem1 < elem2;  
}  
  
int main( )  
{  
    using namespace std;  
  
    vector<int> v1;  
    // Constructing vector v1 with default less-than ordering  
    for ( auto i = -1 ; i <= 4 ; ++i )  
    {  
        v1.push_back(  i );  
    }  
  
    for ( auto ii =-3 ; ii <= 0 ; ++ii )  
    {  
        v1.push_back(  ii  );  
    }  
  
    cout << "Starting vector v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    sort(v1.begin(), v1.end());  
    cout << "Original vector v1 with range sorted by the\n "  
        << "binary predicate less than is v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vector v2 with range sorted by greater  
    vector<int> v2(v1);  
  
    sort(v2.begin(), v2.end(), greater<int>());  
  
    cout << "Original vector v2 with range sorted by the\n "  
        << "binary predicate greater is v2 = ( " ;  
    for (const auto &Iter : v2)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vectors v3 with range sorted by mod_lesser  
    vector<int> v3(v1);  
    sort(v3.begin(), v3.end(), mod_lesser);  
  
    cout << "Original vector v3 with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3 = ( " ;  
    for (const auto &Iter : v3)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Demonstrate lower_bound  
  
    vector<int>::iterator Result;  
  
    // lower_bound of 3 in v1 with default binary predicate less<int>()  
    Result = lower_bound(v1.begin(), v1.end(), 3);  
    cout << "The lower_bound in v1 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // lower_bound of 3 in v2 with the binary predicate greater<int>( )  
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());  
    cout << "The lower_bound in v2 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // lower_bound of 3 in v3 with the binary predicate  mod_lesser  
    Result = lower_bound(v3.begin(), v3.end(), 3,  mod_lesser);  
    cout << "The lower_bound in v3 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
}  
  
```  
  
##  <a name="make_heap"></a>  make_heap  
 将指定范围中的元素转换到第一个元素是最大元素的堆中，其中排序条件可通过二元谓词指定。  
  
```  
 template<class RandomAccessIterator>  
 void make_heap(  
     RandomAccessIterator first,  
     RandomAccessIterator last );  
  
template<class RandomAccessIterator, class BinaryPredicate>   
void make_heap(   
     RandomAccessIterator first,  
     RandomAccessIterator last,  
     BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种随机访问迭代器，用于寻址要转换为堆的范围中第一个元素的位置。  
  
 `last`  
 一种随机访问迭代器，用于寻址要转换为堆的范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="remarks"></a>备注  
 堆有两个属性：  
  
-   第一个元素始终最大。  
  
-   可以在对数时间内添加或删除元素。  
  
 堆是实施优先级队列的理想方式，用于实施 C++ 标准库容器适配器 [priority_queue 类](../standard-library/priority-queue-class.md)。  
  
 复杂性是线性的需要 3 \* (* 姓氏-名字 *) 比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_make_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   random_shuffle( v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Make v1 a heap with default less than ordering  
   make_heap ( v1.begin( ), v1.end( ) );  
   cout << "The heaped version of vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Make v1 a heap with greater than ordering  
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The greater-than heaped version of v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="max"></a>  max  
 比较两个对象并返回较大对象，其中排序条件可通过二元谓词指定。  
  
```  
template<class Type>  
    const Type& max(  
        const Type& left,   
        const Type& right  
    );  
template<class Type, class Pr>  
    const Type& max(  
        const Type& left,   
        const Type& right,  
        BinaryPredicate comp  
    );  
template<class Type>   
    Type& max (  
        initializer_list<Type> _Ilist  
    );  
template<class Type, class Pr>   
    Type& max(  
        initializer_list<Type> _Ilist,   
        BinaryPredicate comp  
    );  
```  
  
### <a name="parameters"></a>参数  
 `left`  
 要比较的两个对象中的第一个对象。  
  
 `right`  
 要比较的两个对象中的第二个对象。  
  
 `comp`  
 用于比较两个对象的二元谓词。  
  
 `_IList`  
 包含要比较的对象的初始值设定项列表。  
  
### <a name="return-value"></a>返回值  
 两个对象中的较大者，除非两个对象都不大；在此情况下，它将返回两个对象中的第一个对象。 在 initializer_list 中，它将返回列表中的最大对象。  
  
### <a name="remarks"></a>备注  
 `max` 算法很少将对象作为参数传递。 大多数 C++ 标准库算法对一系列其位置由作为参数传递的迭代器指定的元素进行操作。 如果你需要一个对一系列元素进行操作的函数，请改用 [max_element](../standard-library/algorithm-functions.md#max_element)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_max.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) {m_nVal =   
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const   
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";   
   return osIn;  
}  
  
// Return whether absolute value of elem1 is greater than   
// absolute value of elem2  
bool abs_greater ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = -elem1;  
   if ( elem2 < 0 )   
      elem2 = -elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   int a = 6, b = -7;  
   // Return the integer with the larger absolute value  
   const int& result1 = max(a, b, abs_greater);  
   // Return the larger integer  
   const int& result2 = max(a, b);  
  
   cout << "Using integers 6 and -7..." << endl;  
   cout << "The integer with the greater absolute value is: "   
        << result1 << "." << endl;  
   cout << "The integer with the greater value is: "   
        << result2 << "." << endl;  
   cout << endl;  
  
// Comparing the members of an initializer_list  
const int& result3 = max({ a, b });  
const int& result4 = max({ a, b }, abs_greater);  
  
cout << "Comparing the members of an initializer_list..." << endl;  
cout << "The member with the greater value is: " << result3 << endl;  
cout << "The integer with the greater absolute value is: " << result4 << endl;  
  
   // Comparing set containers with elements of type CInt   
   // using the max algorithm  
   CInt c1 = 1, c2 = 2, c3 = 3;  
   set<CInt> s1, s2, s3;  
   set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;  
  
   s1.insert ( c1 );  
   s1.insert ( c2 );  
   s2.insert ( c2 );  
   s2.insert ( c3 );  
  
   cout << "s1 = (";  
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter << ",";  
   s1_Iter = --s1.end( );  
   cout << " " << *s1_Iter << " )." << endl;  
  
   cout << "s2 = (";  
   for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )  
      cout << " " << *s2_Iter << ",";  
   s2_Iter = --s2.end( );  
   cout << " " << *s2_Iter << " )." << endl;  
  
   s3 = max ( s1, s2 );  
   cout << "s3 = max ( s1, s2 ) = (";  
   for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )  
      cout << " " << *s3_Iter << ",";  
   s3_Iter = --s3.end( );  
   cout << " " << *s3_Iter << " )." << endl << endl;  
  
   // Comparing vectors with integer elements using the max algorithm  
   vector <int> v1, v2, v3, v4, v5;  
   vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;  
  
   int i;  
   for ( i = 0 ; i <= 2 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 2 ; ii++ )  
   {  
      v2.push_back( ii );  
   }  
  
   int iii;  
   for ( iii = 0 ; iii <= 2 ; iii++ )  
   {  
      v3.push_back( 2 * iii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v3 is ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
  
   v4 = max ( v1, v2 );  
   v5 = max ( v1, v3 );  
  
   cout << "Vector v4 = max (v1,v2) is ( " ;  
   for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )  
      cout << *Iter4 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v5 = max (v1,v3) is ( " ;  
   for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )  
      cout << *Iter5 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Using integers 6 and -7...  
The integer with the greater absolute value is: -7  
The integer with the greater value is: 6.  
Comparing the members of an initializer_list...The member with the greater value is: 6The integer wiht the greater absolute value is: -7  
s1 = ( CInt( 1 ), CInt( 2 ) ).  
s2 = ( CInt( 2 ), CInt( 3 ) ).  
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).  
  
Vector v1 is ( 0 1 2 ).  
Vector v2 is ( 0 1 2 ).  
Vector v3 is ( 0 2 4 ).  
Vector v4 = max (v1,v2) is ( 0 1 2 ).  
Vector v5 = max (v1,v3) is ( 0 2 4 ).  
```  
  
##  <a name="max_element"></a>  max_element  
 在指定范围中查找最大元素的第一个匹配项，其中排序条件可通过二元谓词指定。  
  
```  
template<class ForwardIterator>  
ForwardIterator max_element(ForwardIterator first, ForwardIterator last );  
  
template<class ForwardIterator, class BinaryPredicate>  
ForwardIterator max_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个前向迭代器，用于确定要在其中搜索最大元素的范围中的第一个元素的位置。  
  
 `last`  
 一个前向迭代器，用于确定要在其中搜索最大元素的范围中的最后一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="return-value"></a>返回值  
 一个前向迭代器，用于确定搜索范围内的最大元素的第一个匹配项的位置。  
  
### <a name="remarks"></a>备注  
 引用范围必须是有效的；所有指针必须是可解除引用的，在每个序列中，最后一个位置可从第一个位置通过递增到达。  
  
 复杂性是线性: ( `last`  -   `first`)-1 比较所需的非空范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_max_element.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt& operator=( const CInt& rhs ) {m_nVal =   
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const   
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<(ostream& osIn, const CInt& rhs)  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";   
   return osIn;  
}  
  
// Return whether modulus of elem1 is greater than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   // Searching a set container with elements of type CInt   
   // for the maximum element   
   CInt c1 = 1, c2 = 2, c3 = -3;  
   set<CInt> s1;  
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;  
  
   s1.insert ( c1 );  
   s1.insert ( c2 );  
   s1.insert ( c3 );  
  
   cout << "s1 = (";  
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter << ",";  
   s1_Iter = --s1.end( );  
   cout << " " << *s1_Iter << " )." << endl;  
  
   s1_R1_Iter = max_element ( s1.begin ( ) , s1.end ( ) );  
  
   cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;  
   cout << endl;  
  
   // Searching a vector with elements of type int for the maximum  
   // element under default less than & mod_lesser binary predicates  
   vector <int> v1;  
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 1 ; ii <= 4 ; ii++ )  
   {  
      v1.push_back( - 2 * ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )  
      cout << *v1_Iter << " ";  
   cout << ")." << endl;  
  
   v1_R1_Iter = max_element ( v1.begin ( ) , v1.end ( ) );  
   v1_R2_Iter = max_element ( v1.begin ( ) , v1.end ( ), mod_lesser);  
  
   cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;  
   cout << "The largest element in v1 under the mod_lesser"  
        << "\n binary predicate is: " << *v1_R2_Iter << endl;  
}  
```  
  
##  <a name="merge"></a>  merge  
 将两个已排序源范围中的所有元素合并为一个已排序目标范围，其中排序条件可通过二元谓词指定。  
  
```  
template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator merge(   
     InputIterator1 first1,   
     InputIterator1 last1,   
     InputIterator2 first2,   
     InputIterator2 last2,   
     OutputIterator result );   
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator merge(   
     InputIterator1 first1,   
     InputIterator1 last1,   
     InputIterator2 first2,   
     InputIterator2 last2,   
     OutputIterator result,  
     BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一个输入迭代器，用于确定要合并且排序为一个范围的两个已排序源范围中第一个源范围内第一个元素的位置。  
  
 `last1`  
 一个输入迭代器，用于确定要合并且排序为一个范围的两个已排序源范围中第一个源范围内最后一个元素之后下一个元素的位置。  
  
  `first2`  
 一个输入迭代器，用于确定要合并且排序为一个范围的两个连续已排序源范围中第二个源范围内第一个元素的位置。  
  
 `last2`  
 一个输入迭代器，用于确定要合并且排序为一个范围的两个连续已排序源范围中第二个源范围内最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，用于确定要将两个源范围合并为一个已排序范围的目标范围内第一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，用于确定已排序目标范围中最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 目标范围不能与任一源范围重叠，并且应当足够大，以便包含目标范围。  
  
 必须按照 **merge** 算法对合并范围排序时要使用的相同顺序对已排序源范围分别进行排列，作为应用该算法的前置条件。  
  
 该操作保持不变，因为每个范围内元素的相对顺序均保留在目标范围中。 **merge**算法不会修改源范围。  
  
 输入迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 当两个源范围中有相等的元素时，在目标范围中，第一个范围中的元素优先于第二个源范围中的元素。  
  
 算法的复杂性是线性的最多 (* last1-first1*)-(* last2-first2*)-1 比较。  
  
 [list 类](../standard-library/list-class.md)提供成员函数“merge”来合并两个列表的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_merge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>   // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 ) {  
   if (elem1 < 0)   
      elem1 = - elem1;  
   if (elem2 < 0)   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1;  
  
   // Constructing vector v1a and v1b with default less than ordering  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
      v1a.push_back(  i );  
  
   int ii;  
   for ( ii =-5 ; ii <= 0 ; ii++ )  
      v1b.push_back(  ii  );  
  
   cout << "Original vector v1a with range sorted by the\n "  
        << "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        << "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vector v2 with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a,  Iter2b, Iter2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vector v3 with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        << "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        << "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To merge inplace in ascending order with default binary   
   // predicate less <int> ( )  
   merge ( v1a.begin ( ) , v1a.end ( ) , v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Merged inplace with default order,\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To merge inplace in descending order, specify binary   
   // predicate greater<int>( )  
   merge ( v2a.begin ( ) , v2a.end ( ) , v2b.begin ( ) , v2b.end ( ) ,  
       v2.begin ( ) ,  greater <int> ( ) );  
   cout << "Merged inplace with binary predicate greater specified,\n "  
        << "vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // Applying A user-defined (UD) binary predicate mod_lesser  
   merge ( v3a.begin ( ) , v3a.end ( ) , v3b.begin ( ) , v3b.end ( ) ,  
       v3.begin ( ) ,  mod_lesser );  
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "  
        << "vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="min"></a>  min  
 比较两个对象并返回较小对象，其中排序条件可通过二元谓词指定。  
  
```  
template<class Type>  
    const Type& min(  
        const Type& left,   
        const Type& right  
    );  
template<class Type, class Pr>  
    const Type& min(  
        const Type& left,   
        const Type& right,  
        BinaryPredicate comp  
    );  
template<class Type>   
    Type min ( initializer_list<Type> _Ilist  
    );  
template<class Type, class Pr>    Type min (  
        initializer_list<Type> _Ilist,   
        BinaryPredicate comp  
    );  
  
```  
  
### <a name="parameters"></a>参数  
 `left`  
 要比较的两个对象中的第一个对象。  
  
 `right`  
 要比较的两个对象中的第二个对象。  
  
 `comp`  
 用于比较两个对象的二元谓词。  
  
 `_IList`  
 包含要比较的成员的 initializer_list。  
  
### <a name="return-value"></a>返回值  
 两个对象中的较小者，除非两个对象都不小；在此情况下，它将返回两个对象中的第一个对象。 在 initializer_list 中，它将返回列表中的最小对象。  
  
### <a name="remarks"></a>备注  
 `min` 算法很少将对象作为参数传递。 大多数 C++ 标准库算法对一系列其位置由作为参数传递的迭代器指定的元素进行操作。 如果你需要一个使用一系列元素的函数，请使用 [min_element](../standard-library/algorithm-functions.md#min_element)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_min.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
    CInt( int n = 0 ) : m_nVal( n ){}  
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
    CInt& operator=( const CInt& rhs ) {m_nVal =   
    rhs.m_nVal; return *this;}  
    bool operator<( const CInt& rhs ) const   
        {return ( m_nVal < rhs.m_nVal );}  
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);  
  
private:  
    int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
    osIn << "CInt( " << rhs.m_nVal << " )";   
       return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
    if ( elem1 < 0 )   
        elem1 = - elem1;  
    if ( elem2 < 0 )   
        elem2 = - elem2;  
    return elem1 < elem2;  
};  
  
int main( )  
{  
    // Comparing integers directly using the min algorithm with  
    // binary predicate mod_lesser & with default less than  
    int a = 6, b = -7, c = 7 ;  
    const int& result1 = min ( a, b, mod_lesser );  
    const int& result2 = min ( b, c );  
  
    cout << "The mod_lesser of the integers 6 & -7 is: "   
        << result1 << "." << endl;  
     cout << "The lesser of the integers -7 & 7 is: "   
        << result2 << "." << endl;  
    cout << endl;  
  
// Comparing the members of an initializer_list  
    const int& result3 = min({ a, c });  
    const int& result4 = min({ a, b }, mod_lesser);  
  
    cout << "The lesser of the integers 6 & 7 is: "  
        << result3 << "." << endl;  
    cout << "The mod_lesser of the integers 6 & -7 is: "  
        << result4 << "." << endl;  
    cout << endl;  
  
    // Comparing set containers with elements of type CInt   
       // using the min algorithm  
    CInt c1 = 1, c2 = 2, c3 = 3;  
    set<CInt> s1, s2, s3;  
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;  
  
    s1.insert ( c1 );  
    s1.insert ( c2 );  
    s2.insert ( c2 );  
    s2.insert ( c3 );  
  
    cout << "s1 = (";  
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
        cout << " " << *s1_Iter << ",";  
    s1_Iter = --s1.end( );  
        cout << " " << *s1_Iter << " )." << endl;  
  
    cout << "s2 = (";  
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )  
        cout << " " << *s2_Iter << ",";  
    s2_Iter = --s2.end( );  
    cout << " " << *s2_Iter << " )." << endl;  
  
    s3 = min ( s1, s2 );  
    cout << "s3 = min ( s1, s2 ) = (";  
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )  
        cout << " " << *s3_Iter << ",";  
    s3_Iter = --s3.end( );  
    cout << " " << *s3_Iter << " )." << endl << endl;  
  
    // Comparing vectors with integer elements using min algorithm  
    vector <int> v1, v2, v3, v4, v5;  
    vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;  
  
    int i;  
    for ( i = 0 ; i <= 2 ; i++ )  
    {  
        v1.push_back( i );  
    }  
  
    int ii;  
    for ( ii = 0 ; ii <= 2 ; ii++ )  
    {  
        v2.push_back( ii );  
    }  
  
    int iii;  
    for ( iii = 0 ; iii <= 2 ; iii++ )  
    {  
        v3.push_back( 2 * iii );  
    }  
  
    cout << "Vector v1 is ( " ;  
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
        cout << *Iter1 << " ";  
    cout << ")." << endl;  
  
    cout << "Vector v2 is ( " ;  
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
        cout << *Iter2 << " ";  
    cout << ")." << endl;  
  
    cout << "Vector v3 is ( " ;  
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
        cout << *Iter3 << " ";  
    cout << ")." << endl;  
  
    v4 = min ( v1, v2 );  
    v5 = min ( v1, v3 );  
  
    cout << "Vector v4 = min ( v1,v2 ) is ( " ;  
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )  
        cout << *Iter4 << " ";  
    cout << ")." << endl;  
  
    cout << "Vector v5 = min ( v1,v3 ) is ( " ;  
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )  
        cout << *Iter5 << " ";  
    cout << ")." << endl;  
}  
```  
  
```Output  
The mod_lesser of the integers 6 & -7 is: 6.  
The lesser of the integers -7 & 7 is: -7.  
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.  
s1 = ( CInt( 1 ), CInt( 2 ) ).  
s2 = ( CInt( 2 ), CInt( 3 ) ).  
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).  
  
Vector v1 is ( 0 1 2 ).  
Vector v2 is ( 0 1 2 ).  
Vector v3 is ( 0 2 4 ).  
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).  
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).  
```  
  
##  <a name="min_element"></a>  min_element  
 在指定范围中查找最小元素的第一个匹配项，其中排序条件可通过二元谓词指定。  
  
```  
 template<class ForwardIterator>  
 ForwardIterator min_element(ForwardIterator first, ForwardIterator last );  
  
template<class ForwardIterator, class BinaryPredicate>  
ForwardIterator min_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 一种前向迭代器，用于寻址要在其中搜索最小元素的范围中第一个元素的位置。  
  
 `last`  
 一种前向迭代器，用于寻址要在其中搜索最小元素的范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="return-value"></a>返回值  
 一种前向迭代器，用于寻址搜索范围内最小元素的第一个匹配项的位置。  
  
### <a name="remarks"></a>备注  
 引用范围必须是有效的；所有指针必须是可解除引用的，在每个序列中，最后一个位置可从第一个位置通过递增到达。  
  
 复杂性是线性: ( `last`  -  `first`)-1 比较所需的非空范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_min_element.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt& operator=( const CInt& rhs ) {m_nVal =   
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const   
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";   
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main()  
{  
   // Searching a set container with elements of type CInt   
   // for the minimum element   
   CInt c1 = 1, c2 = 2, c3 = -3;  
   set<CInt> s1;  
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;  
  
   s1.insert ( c1 );  
   s1.insert ( c2 );  
   s1.insert ( c3 );  
  
   cout << "s1 = (";  
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter << ",";  
   s1_Iter = --s1.end( );  
   cout << " " << *s1_Iter << " )." << endl;  
  
   s1_R1_Iter = min_element ( s1.begin ( ) , s1.end ( ) );  
  
   cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;  
   cout << endl;  
  
   // Searching a vector with elements of type int for the maximum  
   // element under default less than & mod_lesser binary predicates  
   vector <int> v1;  
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 1 ; ii <= 4 ; ii++ )  
   {  
      v1.push_back( - 2 * ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )  
      cout << *v1_Iter << " ";  
   cout << ")." << endl;  
  
   v1_R1_Iter = min_element ( v1.begin ( ) , v1.end ( ) );  
   v1_R2_Iter = min_element ( v1.begin ( ) , v1.end ( ), mod_lesser);  
  
   cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;  
   cout << "The smallest element in v1 under the mod_lesser"  
        << "\n binary predicate is: " << *v1_R2_Iter << endl;  
}  
```  
  
```Output  
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).  
The smallest element in s1 is: CInt( -3 )  
  
Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).  
The smallest element in v1 is: -8  
The smallest element in v1 under the mod_lesser  
 binary predicate is: 0  
```  
  
##  <a name="minmax_element"></a>  minmax_element  
 在一次调用中执行由 `min_element` 和 `max_element` 执行的操作。  
  
```  
template<class ForwardIterator>  
    pair< ForwardIterator, ForwardIterator >  
        minmax_element(  
            ForwardIterator  first,   
            ForwardIterator Last  
                 );  
template<class ForwardIterator, class BinaryPredicate>  
    pair< ForwardIterator, ForwardIterator >  
        minmax_element(  
            ForwardIterator  first,   
            ForwardIterator Last,   
            BinaryPredicate  comp  
                );  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种前向迭代器，指示范围的开始位置。  
  
 `last`  
 一种前向迭代器，指示范围的结束位置。  
  
 `comp`  
 用于排序元素的可选测试。  
  
### <a name="return-value"></a>返回值  
 返回  
  
 `pair<ForwardIterator, ForwardIterator>`  
  
 `(` [min_element](../standard-library/algorithm-functions.md#min_element)(  `first`, `last`)，[max_element](../standard-library/algorithm-functions.md#max_element)(  `first`, `last`))。  
  
### <a name="remarks"></a>备注  
 第一个模板函数返回  
  
 `pair<ForwardIterator,ForwardIterator>`  
  
 `(min_element(_First,Last),max_element(_First,Last))`。  
  
 第二个模板函数的行为相同，只不过它将 `operator<(X, Y)` 替换为 `comp``(X, Y)`。  
  
 如果序列为非空，此函数将最多执行 `3 * (``last` `-` `first` `- 1) / 2` 次比较。  
  
##  <a name="minmax"></a>  minmax  
 比较两个输入参数，并按较小到较大的顺序将它们作为参数对返回。  
  
```  
template<class Type>  
    pair<const Type&, const Type&>  
        minmax(  
            const Type& left,   
            const Type& right  
        );  
template<class Type, class BinaryPredicate>  
    pair<const Type&, const Type&>  
        minmax(  
            const Type& left,  
            const Type& right,  
            BinaryPredicate comp  
        );  
template<class Type>     pair<Type&, Type&>         minmax(  
            initializer_list<Type> _Ilist  
        );  
template<class Type, class BinaryPredicate>   
    pair<Type&, Type&>         minmax(  
            initializer_list<Type> _Ilist,   
            BinaryPredicate comp  
        );  
  
```  
  
### <a name="parameters"></a>参数  
 `left`  
 要比较的两个对象中的第一个对象。  
  
 `right`  
 要比较的两个对象中的第二个对象。  
  
 `comp`  
 用于比较两个对象的二元谓词。  
  
 `_IList`  
 包含要比较的成员的 initializer_list。  
  
### <a name="remarks"></a>备注  
 如果 `right` 小于 `left`，第一个模板函数返回 `pair<const Type&, const Type&>(``right``,` `left``)`。 否则，将返回 `pair<const Type&, const Type&>(``left``,` `right``)`。  
  
 当通过谓词 `comp` 进行比较时，第二个成员函数返回一对元素，其中第一个元素较小，第二个元素较大。  
  
 其余模板函数的行为相同，只不过它们会将 `left` 和 `right` 参数替换为 `_IList`。  
  
 此函数仅执行一次比较。  
  
##  <a name="mismatch"></a>  mismatch  
 逐个元素对比两个范围，并找到出现不同的第一个位置。  
  
 在 C++14 代码中使用双范围重载，因为对第二个范围仅采用单个迭代器的重载在第二个范围长于第一个范围时不会检测到差异，并且会在第二个范围短于第一个范围时导致未定义的行为。  
  
```  
 template<class InputIterator1, class InputIterator2> pair<InputIterator1, InputIterator2>>   
 mismatch(  
     InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2 );   
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>  
mismatch(  
     InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2,  
     BinaryPredicate Comp );  
  
//C++14  
template<class InputIterator1, class InputIterator2> pair<InputIterator1, InputIterator2>>  
mismatch(  
    InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2,  
     InputIterator2 Last2 );  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>  
mismatch(  
     InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2,  
     InputIterator2 Last2,  
     BinaryPredicate Comp);  
```  
  
### <a name="parameters"></a>参数  
 `First1`  
 用于确定要测试的第一个范围中第一个元素的位置的输入迭代器。  
  
 `Last1`  
 用于确定要测试的第一个范围中最后元素之后下一个元素的位置的输入迭代器。  
  
 `First2`  
 用于确定要测试的第二个范围中第一个元素的位置的输入迭代器。  
  
 `Last2`  
 用于确定要测试的第二个范围中最后元素之后下一个元素的位置的输入迭代器。  
  
 `Comp`  
 用户定义的谓词函数对象，该对象将每个范围中的当前元素进行比较，并确定它们是否等效。 满足条件时，它将返回 **true**，不满足时将返回 **false**。  
  
### <a name="return-value"></a>返回值  
 一对迭代器，用于确定两个范围中不匹配的位置，第一个组件迭代器指向第一个范围中的位置，第二个组件迭代器指向第二个范围中的位置。 如果比较的范围内的元素之间没有区别，或者两个范围内的所有元素对都满足第二个版本中的二进制谓词的两个范围，那么第一个组件迭代器会指向第一个范围中最后元素之后下一个元素的位置，第二个组件迭代器会指向第二个范围中测试的最后元素之后的下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 第一个模板函数假设从 first2 开始的范围中存在的元素数与 [first1, last1) 指定的范围中的元素数相同。 如果第二个范围中存在更多元素，则忽略它们；如果元素更少，则会导致未定义的行为。  
  
 要搜索的范围必须是有效的；所有迭代器必须是可解除引用的，并且最后一个位置可从第一个位置通过递增到达。  
  
 算法的时间复杂性在较短范围所包含的元素数目上呈线性。  
  
 用户定义的谓词不需要施加在其操作数之间施加对称、反身和可传递的等效关系。  
  
### <a name="example"></a>示例  
  下面的示例演示如何使用不匹配。 显示 C++03 重载只是为了演示它能如何产生意外结果。  
  
```cpp  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
#include <string>  
#include <utility>  
  
using namespace std;  
  
// Return whether first element is twice the second  
// Note that this is not a symmetric, reflexive and transitive equivalence.  
// mismatch and equal accept such predicates, but is_permutation does not.  
bool twice(int elem1, int elem2)  
{  
    return elem1 == elem2 * 2;  
}  
  
void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,  
    const vector<int>& left, const vector<int>& right)  
{  
    // If either iterator stops before reaching the end of its container,  
    // it means a mismatch was detected.  
    if (result.first != left.end() || result.second != right.end())  
    {  
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));  
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));  
        cout << msg << "mismatch. Left iterator at " << leftpos  
            << " right iterator at " << rightpos << endl;  
    }  
    else  
    {  
        cout << msg << " match." << endl;  
    }  
}  
  
int main()  
{  
  
    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };  
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };  
  
    // Testing different length vectors for mismatch (C++03)  
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());  
    bool is_mismatch = match_vecs.first != vec_1.end();  
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;  
  
    // Using dual-range overloads:  
  
    // Testing different length vectors for mismatch (C++14)  
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());  
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);  
  
    // Identify point of mismatch between vec_1 and modified vec_2.   
    vec_2[3] = 42;  
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());  
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);  
  
    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)    
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };  
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };  
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);  
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);  
  
    vec_4[5] = 31;  
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);  
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);  
  
    // Compare a vector<int> to a list<int>  
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };  
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());  
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();  
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;  
  
    char c;  
    cout << "Press a key" << endl;  
    cin >> c;  
  
}  
  
/*  
Output:  
C++03: vec_1 and vec_2 are a mismatch: false  
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30  
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42  
C++14 vec_3 v. vec_4 with pred:  match.  
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31  
C++14: vec_1 and list_1 are a mismatch: false  
Press a key  
*/  
  
```  
  
##  <a name="alg_move"></a>  &lt;alg&gt; move  
 移动与指定范围关联的元素。  
  
```  
template<class InputIterator, class OutputIterator>  
    OutputIterator move(  
        InputIterator first,   
        InputIterator last,  
        OutputIterator dest  
                  );  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个输入迭代器，指示在范围内移动元素的起始位置。  
  
 `last`  
 一个输入迭代器，指示在范围内移动元素的结束位置。  
  
 `dest`  
 将包含已移动元素的输出迭代器。  
  
### <a name="remarks"></a>备注  
 模板函数的计算结果`*(dest + N) = move(*(first + N))`一次为每个`N`范围内`[0, last - first)`，严格增加值的`N`从最低值开始。 然后返回 `dest + N`。 如果`dest`和`first`指定存储区域，`dest`不得位于范围`[first, last)`。  
  
##  <a name="move_backward"></a>  move_backward  
 将一个迭代器的元素移动到另一迭代器。 移动从指定范围的最后一个元素开始，并在此范围的第一个元素结束。  
  
```  
template<class BidirectionalIterator1, class BidirectionalIterator2>  
   BidirectionalIterator2 move_backward(  
       BidirectionalIterator1 first,   
       BidirectionalIterator1 last,  
       BidirectionalIterator2 destEnd);
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 指示范围内移动元素的开始位置的迭代器。  
  
 `last`  
 指示在范围内移动元素的结束位置的迭代器。 此元素未移动。  
  
 `destEnd`  
 一种双向迭代器，用于定址目标范围内最后元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 模板函数的计算结果`*(destEnd - N - 1) = move(*(last - N - 1))`一次为每个`N`范围内`[0, last - first)`，严格增加值的`N`从最低值开始。 然后返回 `destEnd - (last - first)`。 如果`destEnd`和`first`指定存储区域，`destEnd`不得位于范围`[first, last)`。  
  
 `move` 和 `move_backward` 在功能上等效于将 `copy` 和 `copy_backward` 与移动迭代器结合使用。  
  
##  <a name="next_permutation"></a>  next_permutation  
 重新排序范围中的元素，以便使用按字典顺序的下一个更大排列（如果有）替换原有排序，其中“下一个”的意义可通过二元谓词指定。  
  
```  
template<class BidirectionalIterator>  
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last);  
  
template<class BidirectionalIterator, class BinaryPredicate>  
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，指向要重新排序的范围内第一个元素的位置。  
  
 `last`  
 一种双向迭代器，指向要重新排序的范围内最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 如果按字典顺序下一个排列存在并且已替换范围的原始顺序，则返回 **true**；否则，返回 **false**。这种情况下，顺序转换为按字典顺序最小的排列。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 默认二元谓词是“小于”，并且范围中的元素必须是小于比较项，以确保正确定义下一个排列。  
  
 复杂性是线性的最多 (* 姓氏-名字 *) / 2 交换。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_next_perm.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) {m_nVal =  
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const  
      { return ( m_nVal < rhs.m_nVal );}  
   friend   ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";  
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )  
      elem1 = - elem1;  
   if ( elem2 < 0 )  
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   // Reordering the elements of type CInt in a deque  
   // using the prev_permutation algorithm  
   CInt c1 = 5, c2 = 1, c3 = 10;  
   bool deq1Result;  
   deque<CInt> deq1, deq2, deq3;  
   deque<CInt>::iterator d1_Iter;  
  
   deq1.push_back ( c1 );  
   deq1.push_back ( c2 );  
   deq1.push_back ( c3 );  
  
   cout << "The original deque of CInts is deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   deq1Result = next_permutation ( deq1.begin ( ) , deq1.end ( ) );  
  
   if ( deq1Result )  
      cout << "The lexicographically next permutation "  
           << "exists and has\nreplaced the original "  
           << "ordering of the sequence in deq1." << endl;  
   else  
      cout << "The lexicographically next permutation doesn't "  
           << "exist\n and the lexicographically "  
           << "smallest permutation\n has replaced the "  
           << "original ordering of the sequence in deq1." << endl;  
  
   cout << "After one application of next_permutation,\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl << endl;  
  
   // Permuting vector elements with binary function mod_lesser  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = -3 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
  
   cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= 5 ) {  
      next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
      cout << "After another next_permutation of vector v1,\n v1 =   ( " ;  
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )  
         cout << *Iter1  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
```Output  
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).  
The lexicographically next permutation exists and has  
replaced the original ordering of the sequence in deq1.  
After one application of next_permutation,  
 deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).  
  
Vector v1 is ( -3 -2 -1 0 1 2 3 ).  
After the first next_permutation, vector v1 is:  
 v1 = ( -3 -2 -1 0 1 3 2 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 2 1 3 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 2 3 1 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 3 1 2 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 3 2 1 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 1 0 2 3 ).  
```  
  
##  <a name="nth_element"></a>  nth_element  
 对范围内的元素分区，正确找到范围中序列的第 *n* 个元素，以使序列中位于此元素之前的所有元素小于或等于此元素，位于此元素之后的所有元素大于或等于此元素。  
  
```  
template<class RandomAccessIterator>  
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last);  
  
 template<class RandomAccessIterator, class BinaryPredicate>  
 void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种随机访问迭代器，用于寻址要分区的范围中第一个元素的位置。  
  
 *_Nth*  
 一种随机访问迭代器，用于寻址要在分区边界上进行正确排序的元素的位置。  
  
 `last`  
 一种随机访问迭代器，用于寻址要分区的范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 `nth_element` 算法不保证会存储子范围中第 *n* 个元素两边的任意元素。 因而，它保证的内容比 `partial_sort` 更少，它对范围中某些所选元素下面的元素进行排序，并且在不需要较低范围的排序时，可以用作替代 `partial_sort` 的一种较快算法。  
  
 元素是等效的，但是如果两者都不小于对方，则不一定要相等。  
  
 排序复杂性的平均值是相对于线性 * 姓氏-名字 *。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_nth_elem.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater ( int elem1, int elem2 ) {  
   return elem1 > elem2;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
      v1.push_back( 3 * i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 5 ; ii++ )  
      v1.push_back( 3 * ii + 1 );  
  
   int iii;  
   for ( iii = 0 ; iii <= 5 ; iii++ )  
      v1.push_back( 3 * iii +2 );  
  
   cout << "Original vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );  
   cout << "Position 3 partitioned vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order, specify binary predicate  
   nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),  
          greater<int>( ) );  
   cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   random_shuffle( v1.begin( ), v1.end( ) );  
   cout << "Shuffled vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );  
   cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
##  <a name="none_of"></a>  none_of  
 当给定范围中没有元素满足条件时返回 `true`。  
  
```  
template<class InputIterator, class BinaryPredicate>  
bool none_of(InputIterator first, InputIterator last, BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指示在元素范围内检查条件的起始位置。  
  
 `last`  
 一种输入迭代器，指示元素范围的结束位置。  
  
 `comp`  
 要测试的条件。 由定义条件的用户定义的谓词函数对象提供。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="return-value"></a>返回值  
 如果在指示范围内至少一次未检测到条件，则返回 `true`，如果检测条件，则返回 `false`。  
  
### <a name="remarks"></a>备注  
 模板函数返回`true`才，对于某些`N`范围内`[0, last - first)`，谓词`comp(*(first + N))`始终`false`。  
  
##  <a name="partial_sort"></a>  partial_sort  
 将范围中指定数量的较小元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。  
  
```  
template<class RandomAccessIterator>  
   void partial_sort(  
      RandomAccessIterator first,   
      RandomAccessIterator sortEnd,  
      RandomAccessIterator last);
  
template<class RandomAccessIterator, class BinaryPredicate>  
   void partial_sort(  
      RandomAccessIterator first,   
      RandomAccessIterator sortEnd,  
      RandomAccessIterator last  
      BinaryPredicate comp);
  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。  
  
 `sortEnd`  
 一种随机访问迭代器，用于寻址要排序的子范围中最后元素之后下一个元素的位置。  
  
 `last`  
 一种随机访问迭代器，用于寻址要部分排序的子范围中最后元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 元素是等效的，但是如果两者都不小于对方，则不一定要相等。 **sort** 算法不稳定，不保证保留等效元素的相对顺序。 算法 `stable_sort` 会保留此原始顺序。  
  
 部分排序复杂性平均值为 *O*(( `last`- `first`) log ( `sortEnd`- `first`))。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_partial_sort.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater ( int elem1, int elem2 )  
{  
   return elem1 > elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 5 ; ii++ )  
   {  
      v1.push_back( 2 * ii +1 );  
   }  
  
   cout << "Original vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );  
   cout << "Partially sorted vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To partially sort in descending order, specify binary predicate  
   partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );  
   cout << "Partially resorted (greater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ),   
 UDgreater );  
   cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector:  
 v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )  
Partially sorted vector:  
 v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )  
Partially resorted (greater) vector:  
 v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )  
Partially resorted (UDgreater) vector:  
 v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )  
```  
  
##  <a name="partial_sort_copy"></a>  partial_sort_copy  
 将源范围中的元素复制到目标范围，其中源元素按降序或二元谓词指定的其他顺序排序。  
  
```  
 template<class InputIterator, class RandomAccessIterator>  
 RandomAccessIterator partial_sort_copy(  
    InputIterator first1,  
    InputIterator last1,  
    RandomAccessIterator first2,  
    RandomAccessIterator last2 );  
  
template<class InputIterator, class RandomAccessIterator, class BinaryPredicate>  
 RandomAccessIterator partial_sort_copy(  
     InputIterator first1,  
     InputIterator last1,  
     RandomAccessIterator first2,  
     RandomAccessIterator last2,  
     BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 发现源范围内的第一个元素的位置的输入迭代器。  
  
 `last1`  
 一个输入迭代器，用于寻址源范围内最后一个元素之后下一个元素的位置。  
  
  `first2`  
 一种随机访问迭代器，用于寻址排序目标范围中第一个元素的位置。  
  
 `last2`  
 一种随机访问迭代器，用于寻址排序目标范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数，并且在满足时返回 `true`，未满足时返回 `false`。  
  
### <a name="return-value"></a>返回值  
 一种随机访问迭代器，用于将目标范围中的元素寻址到从源范围插入的最后一个元素之外的位置。  
  
### <a name="remarks"></a>备注  
 源范围和目标范围务必不能重叠，并且必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置可从第一个位置通过递增到达。  
  
 二元谓词必须提供严格的弱排序，以便对不等效的元素进行排序，但是不对等效的元素进行排序。 两个元素在小于下是等效的，但是如果两者都不小于对方，则不一定要相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_partial_sort_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main() {  
    using namespace std;  
    vector<int> v1, v2;  
    list<int> list1;  
    vector<int>::iterator iter1, iter2;  
    list<int>::iterator list1_Iter, list1_inIter;  
  
    int i;  
    for (i = 0; i <= 9; i++)  
        v1.push_back(i);  
  
    random_shuffle(v1.begin(), v1.end());  
  
    list1.push_back(60);  
    list1.push_back(50);  
    list1.push_back(20);  
    list1.push_back(30);  
    list1.push_back(40);  
    list1.push_back(10);  
  
    cout << "Vector v1 = ( " ;  
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)  
        cout << *iter1 << " ";  
    cout << ")" << endl;  
  
    cout << "List list1 = ( " ;  
    for (list1_Iter = list1.begin();  
         list1_Iter!= list1.end();  
         list1_Iter++)  
        cout << *list1_Iter << " ";  
    cout << ")" << endl;  
  
    // Copying a partially sorted copy of list1 into v1  
    vector<int>::iterator result1;  
    result1 = partial_sort_copy(list1.begin(), list1.end(),  
             v1.begin(), v1.begin() + 3);  
  
    cout << "List list1 Vector v1 = ( " ;  
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)  
        cout << *iter1 << " ";  
    cout << ")" << endl;  
    cout << "The first v1 element one position beyond"  
         << "\n the last L 1 element inserted was " << *result1  
         << "." << endl;  
  
    // Copying a partially sorted copy of list1 into v2  
    int ii;  
    for (ii = 0; ii <= 9; ii++)  
        v2.push_back(ii);  
  
    random_shuffle(v2.begin(), v2.end());  
    vector<int>::iterator result2;  
    result2 = partial_sort_copy(list1.begin(), list1.end(),  
             v2.begin(), v2.begin() + 6);  
  
    cout << "List list1 into Vector v2 = ( " ;  
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)  
        cout << *iter2 << " ";  
    cout << ")" << endl;  
    cout << "The first v2 element one position beyond"  
         << "\n the last L 1 element inserted was " << *result2  
         << "." << endl;  
}  
```  
  
##  <a name="partition"></a>  partition  
 将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前。  
  
```  
template<class BidirectionalIterator, class Predicate>  
   BidirectionalIterator partition(  
      BidirectionalIterator first,   
      BidirectionalIterator last,   
      Predicate comp);
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，用于寻址要分区的范围中第一个元素的位置。  
  
 `last`  
 一种双向迭代器，用于寻址要分区的范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义如果元素要分类时应满足的条件。 谓词采用一个参数并返回 **true** 或 **false**。  
  
### <a name="return-value"></a>返回值  
 一种双向迭代器，用于寻址范围中不满足谓词条件的第一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 元素 *a* 和 *b* 是等效的，但是如果 *Pr* ( *a*,  *b*) 和  *Pr* ( *b*,  *a*) 均为 false（其中 *Pr* 是指定参数的谓词），则不一定要相等。 **partition** 算法不稳定，不保证保留等效元素的相对顺序。 算法 **stable_ partition** 会保留此原始顺序。  
  
 复杂性是线性︰ 有 ( `last`  -   `first`) 的应用程序`comp`且最多 ( `last`  -   `first`) / 2 交换。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_partition.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater5 ( int value ) {  
   return value >5;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 10 ; i++ )  
   {  
      v1.push_back( i );  
   }  
   random_shuffle( v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Partition the range with predicate greater10  
   partition ( v1.begin( ), v1.end( ), greater5 );  
   cout << "The partitioned set of elements in v1 is: ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="partition_copy"></a>  partition_copy  
 将条件为 `true` 的元素复制到一个目标，将条件为 `false` 的元素复制到另一目标。 元素必须来自于指定范围。  
  
```  
template<class InputIterator, class OutputIterator1, class OutputIterator2, class Predicate>  
    pair<OutputIterator1, OutputIterator2>  
        partition_copy(  
            InputIterator first,   
            InputIterator last,  
            OutputIterator1 dest1,   
            OutputIterator2 dest2,   
            Predicate pred  
        );  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指示在一个范围中开始检查条件的位置。  
  
 `last`  
 一种输入迭代器，指示范围的结束位置。  
  
 `dest1`  
 一种输出迭代器，用于复制针对使用 `_Pred` 测试的条件返回 true 的元素。  
  
 `dest2`  
 一种输出迭代器，用于复制针对使用 `_Pred` 测试的条件返回 false 的元素。  
  
 `_Pred`  
 要测试的条件。 由定义要测试条件的用户定义谓词函数对象提供。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="remarks"></a>备注  
 模板函数将复制的每个元素`X`中`[first,last)`到`*dest1++`如果`_Pred(X)`为 true，或者提供至`*dest2++`如果不是。 它将返回 `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`。  
  
##  <a name="partition_point"></a>  partition_point  
 返回给定范围中不满足条件的第一个元素。 元素经过排序，满足条件的元素在不满足条件的元素之前。  
  
```  
template<class ForwardIterator, class Predicate>  
    ForwardIterator partition_point(  
        ForwardIterator first,   
        ForwardIterator last,  
        Predicate comp  
    );  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种 `ForwardIterator`，指示在一个范围内检查条件的开始位置。  
  
 `last`  
 一种 `ForwardIterator`，指示范围的结束位置。  
  
 `comp`  
 要测试的条件。 由用户定义的谓词函数对象提供，用于定义被搜索元素要满足的条件。 谓词采用一个参数并返回 `true` 或 `false`。  
  
### <a name="return-value"></a>返回值  
 返回 `ForwardIterator`，是指不满足由 `comp` 测试的条件的第一个元素，如果找不到，则返回 `last`。  
  
### <a name="remarks"></a>备注  
 模板函数查找第一个迭代器`it`中`[first, last)`为其`comp(*it)`是`false`。 序列必须按 `comp` 排序。  
  
##  <a name="pop_heap"></a>  pop_heap  
 移除从堆顶到范围中倒数第二个位置之间的最大元素，然后将剩余元素形成新堆。  
  
```  
template<class RandomAccessIterator>  
void pop_heap( RandomAccessIterator first, RandomAccessIterator last);  
  
template<class RandomAccessIterator, class BinaryPredicate>  
void pop_heap(RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种随机访问迭代器，用于寻址堆中第一个元素的位置。  
  
 `last`  
 一种随机访问迭代器，用于寻址堆中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="remarks"></a>备注  
 如果添加到堆中的元素大于该堆中已有的任何元素，则 `pop_heap` 算法是由 push_heap 算法执行的操作的反向操作，其中范围的倒数第二个元素添加到由范围中前面的元素组成的堆中。  
  
 堆有两个属性：  
  
-   第一个元素始终最大。  
  
-   可以在对数时间内添加或删除元素。  
  
 堆是实施优先级队列的理想方式，用于实施 C++ 标准库容器适配器 [priority_queue 类](../standard-library/priority-queue-class.md)。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 排除末尾新添加元素的范围必须是一个堆。  
  
 复杂性是对数，最多需要日志 (* 姓氏-名字 *) 比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_pop_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 1 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   // Make v1 a heap with default less than ordering  
   random_shuffle( v1.begin( ), v1.end( ) );  
   make_heap ( v1.begin( ), v1.end( ) );  
   cout << "The heaped version of vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Add an element to the back of the heap  
   v1.push_back( 10 );  
   push_heap( v1.begin( ), v1.end( ) );  
   cout << "The reheaped v1 with 10 added is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove the largest element from the heap  
   pop_heap( v1.begin( ), v1.end( ) );  
   cout << "The heap v1 with 10 removed is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl << endl;  
  
   // Make v1 a heap with greater-than ordering with a 0 element  
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );  
   v1.push_back( 0 );  
   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The 'greater than' reheaped v1 puts the smallest "  
        << "element first:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Application of pop_heap to remove the smallest element  
   pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The 'greater than' heaped v1 with the smallest element\n "  
        << "removed from the heap is: ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="prev_permutation"></a>  prev_permutation  
 重新排序范围中的元素，以便按字典顺序的前一个更大排列（如果有）替换原有排序，其中“前一个”的意义可通过二元谓词指定。  
  
```  
template<class BidirectionalIterator>  
   bool prev_permutation(  
      BidirectionalIterator first,   
      BidirectionalIterator last);
  
template<class BidirectionalIterator, class BinaryPredicate>  
   bool prev_permutation(  
      BidirectionalIterator first,   
      BidirectionalIterator last,  
      BinaryPredicate comp);
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，指向要重新排序的范围内第一个元素的位置。  
  
 `last`  
 一种双向迭代器，指向要重新排序的范围内最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数，并且在满足时返回 `true`，未满足时返回 `false`。  
  
### <a name="return-value"></a>返回值  
 如果按字典顺序前一个排列存在并且已替换范围的原始顺序，则返回 `true`；否则，返回 `false`。这种情况下，顺序转换为按字典顺序最大的排列。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 默认二元谓词是“小于”，并且范围中的元素必须是小于比较项，以确保正确定义前一个排列。  
  
 复杂性是线性的与最多 ( `last`  -   `first`) / 2 交换。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_prev_perm.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt {  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) {m_nVal =  
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const  
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {  
   osIn << "CInt( " << rhs.m_nVal << " )";  
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 ) {  
   if ( elem1 < 0 )  
      elem1 = - elem1;  
   if ( elem2 < 0 )  
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main() {  
   // Reordering the elements of type CInt in a deque  
   // using the prev_permutation algorithm  
   CInt c1 = 1, c2 = 5, c3 = 10;  
   bool deq1Result;  
   deque<CInt> deq1, deq2, deq3;  
   deque<CInt>::iterator d1_Iter;  
  
   deq1.push_back ( c1 );  
   deq1.push_back ( c2 );  
   deq1.push_back ( c3 );  
  
   cout << "The original deque of CInts is deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   deq1Result = prev_permutation ( deq1.begin ( ) , deq1.end ( ) );  
  
   if ( deq1Result )  
      cout << "The lexicographically previous permutation "  
           << "exists and has \nreplaced the original "  
           << "ordering of the sequence in deq1." << endl;  
   else  
      cout << "The lexicographically previous permutation doesn't "  
           << "exist\n and the lexicographically "  
           << "smallest permutation\n has replaced the "  
           << "original ordering of the sequence in deq1." << endl;  
  
   cout << "After one application of prev_permutation,\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl << endl;  
  
   // Permutating vector elements with binary function mod_lesser  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = -3 ; i <= 3 ; i++ )  
      v1.push_back( i );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
  
   cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= 5 ) {  
      prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
      cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;  
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )  
         cout << *Iter1  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
```Output  
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).  
The lexicographically previous permutation doesn't exist  
 and the lexicographically smallest permutation  
 has replaced the original ordering of the sequence in deq1.  
After one application of prev_permutation,  
 deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).  
  
Vector v1 is ( -3 -2 -1 0 1 2 3 ).  
After the first prev_permutation, vector v1 is:  
 v1 = ( -3 -2 0 3 2 1 -1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 3 -1 2 1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 3 -1 1 2 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 2 3 1 -1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 2 -1 3 1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 2 -1 1 3 ).  
```  
  
##  <a name="push_heap"></a>  push_heap  
 将范围末尾的元素添加到包括范围中前面元素的现有堆中。  
  
```  
template<class RandomAccessIterator>  
void push_heap( RandomAccessIterator first, RandomAccessIterator last );  
  
template<class RandomAccessIterator, class BinaryPredicate>  
void push_heap( RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种随机访问迭代器，用于寻址堆中第一个元素的位置。  
  
 `last`  
 一种随机访问迭代器，用于寻址要转换为堆的范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="remarks"></a>备注  
 元素必须先推送回现有堆的末尾，然后使用该算法将此元素添加到现有堆。  
  
 堆有两个属性：  
  
-   第一个元素始终最大。  
  
-   可以在对数时间内添加或删除元素。  
  
 堆是实施优先级队列的理想方式，用于实施 C++ 标准库容器适配器 [priority_queue 类](../standard-library/priority-queue-class.md)。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 排除末尾新添加元素的范围必须是一个堆。  
  
 复杂性是对数，最多需要日志 (*姓氏-名字*) 比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_push_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 1 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   random_shuffle( v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Make v1 a heap with default less than ordering  
   make_heap ( v1.begin( ), v1.end( ) );  
   cout << "The heaped version of vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Add an element to the heap  
   v1.push_back( 10 );  
   cout << "The heap v1 with 10 pushed back is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   push_heap( v1.begin( ), v1.end( ) );  
   cout << "The reheaped v1 with 10 added is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl << endl;  
  
   // Make v1 a heap with greater than ordering  
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The greater-than heaped version of v1 is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   v1.push_back(0);  
   cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The greater than reheaped v1 with 11 added is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="random_shuffle"></a>  random_shuffle  
 Std::random_shuffle() 函数已弃用，替换为[std:: shuffle](../standard-library/algorithm-functions.md#shuffle)。 有关代码示例和详细信息，请参阅[\<随机 >](../standard-library/random.md)和 Stackoverflow 文章[为什么是 std:: random_shuffle 弃用方法在 C + + 14？](http://go.microsoft.com/fwlink/?LinkId=397954)。  
  
##  <a name="remove"></a>  remove  
 从给定范围中消除指定值，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。  
  
```  
template<class ForwardIterator, class Type>  
 ForwardIterator remove(ForwardIterator first, ForwardIterator last, const Type& val);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 寻址要删除元素的范围中的第一个元素位置的转发迭代器。  
  
 `last`  
 寻址要删除元素的范围中的最后一个元素的下一个位置的转发迭代器。  
  
 `val`  
 要从该范围删除的值。  
  
### <a name="return-value"></a>返回值  
 寻址修改范围中的新的末尾位置的转发迭代器，此位置即超出不包含指定值的残留序列的最后一个元素的下一个位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 未删除的元素顺序保持不变。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性的;有 ( `last`  -   `first`) 相等比较。  
  
 [list 类](../standard-library/list-class.md)具有更高效的成员函数 **remove** 的版本，它也会重新链接指针。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_remove.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements with a value of 7  
   new_end = remove ( v1.begin( ), v1.end( ), 7 );  
  
   cout << "Vector v1 with value 7 removed is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To change the sequence size, use erase  
   v1.erase (new_end, v1.end( ) );  
  
   cout << "Vector v1 resized with value 7 removed is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="remove_copy"></a>  remove_copy  
 将源范围中的元素复制到目标范围（不复制具有指定值的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。  
  
```  
template<class InputIterator, class OutputIterator, class Type>  
 OutputIterator remove_copy(InputIterator first, InputIterator last, OutputIterator result, const Type& val);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个输入迭代器，用于确定要删除元素的范围内第一个元素的位置。  
  
 `last`  
 一个输入迭代器，用于确定要删除元素的范围内最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，用于确定要删除元素的目标范围内第一个元素的位置。  
  
 `val`  
 要从该范围删除的值。  
  
### <a name="return-value"></a>返回值  
 一个向前迭代器，用于确定目标范围中的新的末尾位置，此位置即不包含指定值的残留序列副本的最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的源范围和目标范围必须有效；所有指针必须可取消引用，并且在序列内，最后一个位置可从第一个位置通过递增到达。  
  
 目标范围中必须有足够的空间，以便包含删除具有指定值的元素之后将复制的残留元素。  
  
 未删除的元素顺序保持不变。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性的;有 ( `last`  -   `first`) 比较是否相等和最多赋 ( `last`  -   `first`) 分配。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_remove_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2(10);  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle (v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:     ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements with a value of 7  
   new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );  
  
   cout << "Vector v1 is left unchanged as ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="remove_copy_if"></a>  remove_copy_if  
 将源范围中的元素复制到目标范围（不复制满足谓词的元素），而不影响剩余元素的顺序，并返回新目标范围的末尾。  
  
```  
template<class InputIterator, class OutputIterator, class Predicate>  
OutputIterator remove_copy_if(InputIterator first, InputIterator Last, OutputIterator result, Predicate pred);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个输入迭代器，用于确定要删除元素的范围内第一个元素的位置。  
  
 `last`  
 一个输入迭代器，用于确定要删除元素的范围内最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，用于确定要删除元素的目标范围内第一个元素的位置。  
  
 `_Pred`  
 必须满足的一元谓词是要替换的元素值。  
  
### <a name="return-value"></a>返回值  
 一个向前迭代器，用于确定目标范围中的新的末尾位置，此位置即不包含满足谓词的元素的残留序列的最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的源范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 目标范围中必须有足够的空间，以便包含删除具有指定值的元素之后将复制的残留元素。  
  
 未删除的元素顺序保持不变。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性︰ 有 ( `last`  -   `first`) 比较是否相等和最多赋 ( `last`  -   `first`) 分配。  
  
 有关这些函数行为方式的信息，请参阅[检查迭代器](../standard-library/checked-iterators.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_remove_copy_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2(10);  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:      ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements with a value greater than 6  
   new_end = remove_copy_if ( v1.begin( ), v1.end( ),   
      v2.begin( ), greater6 );  
  
   cout << "After the appliation of remove_copy_if to v1,\n "  
        << "vector v1 is left unchanged as ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is a copy of v1 with values greater "  
        << "than 6 removed:\n ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="remove_if"></a>  remove_if  
 从给定范围中消除满足谓词的元素，而不影响剩余元素的顺序，并返回不包含指定值的新范围的末尾。  
  
```  
template<class ForwardIterator, class Predicate>  
 ForwardIterator remove_if(ForwardIterator first, ForwardIterator last, Predicate pred);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指向从其中删除元素的范围中第一个元素的位置。  
  
 `last`  
 一种输入迭代器，指向从其中删除元素的范围中最后一个元素之后下一个元素的位置。  
  
 `_Pred`  
 必须满足的一元谓词是要替换的元素值。  
  
### <a name="return-value"></a>返回值  
 寻址修改范围中的新的末尾位置的转发迭代器，此位置即超出不包含指定值的残留序列的最后一个元素的下一个位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 未删除的元素顺序保持不变。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性︰ 有 ( `last`  -   `first`) 相等比较。  
  
 List 具有更高效的成员函数 remove 的版本，它将会重新链接指针。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_remove_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements satisfying predicate greater6  
   new_end = remove_if (v1.begin( ), v1.end( ), greater6 );  
  
   cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To change the sequence size, use erase  
   v1.erase (new_end, v1.end( ) );  
  
   cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace"></a>  replace  
 检查范围中的每个元素，并替换与指定值匹配的元素。  
  
```  
template<class ForwardIterator, class Type>  
void replace(ForwardIterator first, ForwardIterator last, const Type& _OldVal, const Type& _NewVal);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指向要从其中替换元素的范围中第一个元素的位置。  
  
 `last`  
 一种输入迭代器，指向要从其中替换元素的范围中最后一个元素之后下一个元素的位置。  
  
 `_OldVal`  
 要替换的元素的旧值。  
  
 `_NewVal`  
 要赋给具有旧值的元素的新值。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 未替换的元素的顺序保持不变。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性的;有 ( `last`  -   `first`) 比较是否相等和最多赋 ( `last`  -   `first`) 次新值。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_replace.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle (v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements with a value of 7 with a value of 700  
   replace (v1.begin( ), v1.end( ), 7 , 700);  
  
   cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace_copy"></a>  replace_copy  
 检查源范围中的每个元素，并替换与指定值匹配的元素，同时将结果复制到新的目标范围。  
  
```  
 template<class InputIterator, class OutputIterator, class Type>  
 OutputIterator replace_copy(   
     InputIterator first,  
     InputIterator last,  
     OutputIterator result,  
     const Type& _OldVal,  
     const Type& _NewVal);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个输入迭代器，指向要替换元素的范围中的第一个元素的位置。  
  
 `last`  
 一个输入迭代器，指向要替换元素的范围中最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，指向要将序列已更改的元素复制到的目标范围中的第一个元素。  
  
 `_OldVal`  
 要替换的元素的旧值。  
  
 `_NewVal`  
 要赋给具有旧值的元素的新值。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，指向要将序列已更改的元素复制到的目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的源范围和目标范围不能重叠，并且必须有效；所有指针必须可取消引用，并且在序列内，最后一个位置可从第一个位置通过递增到达。  
  
 未替换的元素的顺序保持不变。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性︰ 有 ( `last`  -   `first`) 比较是否相等和最多赋 ( `last`  -   `first`) 次新值。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_replace_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   list <int> L1 (15);  
   vector <int>::iterator Iter1;  
   list <int>::iterator L_Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
  
   int iii;  
   for ( iii = 0 ; iii <= 15 ; iii++ )  
      v1.push_back( 1 );  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements in one part of a vector with a value of 7  
   // with a value of 70 and copy into another part of the vector  
   replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);  
  
   cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements in a vector with a value of 70  
   // with a value of 1 and copy into a list  
   replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);  
  
   cout << "The list copy L1 of v1 with the value 0 replacing "  
        << "that of 7 is:\n ( " ;  
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )  
      cout << *L_Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace_copy_if"></a>  replace_copy_if  
 检查源范围中的每个元素，并替换满足指定谓词的元素，同时将结果复制到新的目标范围。  
  
```  
template<class InputIterator, class OutputIterator, class Predicate, class Type>  
OutputIterator replace_copy_if(  
    InputIterator first,  
    InputIterator last,  
    OutputIterator result,  
    Predicate pred,  
    const Type& val);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个输入迭代器，指向要替换元素的范围中的第一个元素的位置。  
  
 `last`  
 一个输入迭代器，指向要替换元素的范围中最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，指向要将元素复制到的目标范围内第一个元素的位置。  
  
 `_Pred`  
 必须满足的一元谓词是要替换的元素值。  
  
 `val`  
 要赋给其旧值满足谓词的元素的新值。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，指向要将序列已更改的元素复制到的目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的源范围和目标范围不能重叠，并且必须有效；所有指针必须可取消引用，并且在序列内，最后一个位置可从第一个位置通过递增到达。  
  
 未替换的元素的顺序保持不变。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性的;有 ( `last`  -   `first`) 比较是否相等和最多赋 ( `last`  -   `first`) 次新值。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_replace_copy_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   list <int> L1 (13);  
   vector <int>::iterator Iter1;  
   list <int>::iterator L_Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
  
   int iii;  
   for ( iii = 0 ; iii <= 13 ; iii++ )  
      v1.push_back( 1 );  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements with a value of 7 in the 1st half of a vector  
   // with a value of 70 and copy it into the 2nd half of the vector  
   replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,  
      greater6 , 70);  
  
   cout << "The vector v1 with values of 70 replacing those greater"  
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements in a vector with a value of 70  
   // with a value of 1 and copy into a list  
   replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),  
      greater6 , -1 );  
  
   cout << "A list copy of vector v1 with the value -1\n replacing "  
        << "those greater than 6 is:\n ( " ;  
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )  
      cout << *L_Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace_if"></a>  replace_if  
 检查范围中的每个元素，并替换满足指定谓词的元素。  
  
```  
template<class ForwardIterator, class Predicate, class Type>  
void replace_if(ForwardIterator first, ForwardIterator last, Predicate pred, const Type& val);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种输入迭代器，指向要从其中替换元素的范围中第一个元素的位置。  
  
 `last`  
 一个迭代器，指向要替换元素的范围中最后一个元素之后下一个元素的位置。  
  
 `_Pred`  
 必须满足的一元谓词是要替换的元素值。  
  
 `val`  
 要赋给其旧值满足谓词的元素的新值。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 未替换的元素的顺序保持不变。  
  
 算法 `replace_if` 是算法 **replace** 的泛化，允许指定任何谓词，而非等于一个指定常量值。  
  
 用于确定元素之间相等性的 `operator==` 必须在其操作数之间施加等效关系。  
  
 复杂性是线性︰ 有 ( `last`  -   `first`) 比较是否相等和最多赋 ( `last`  -   `first`) 次新值。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_replace_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements satisfying the predicate greater6  
   // with a value of 70  
   replace_if ( v1.begin( ), v1.end( ), greater6 , 70);  
  
   cout << "The vector v1 with a value 70 replacing those\n "  
        << "elements satisfying the greater6 predicate is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="reverse"></a>  reverse  
 反转范围中元素的顺序。  
  
```  
template<class BidirectionalIterator>  
 void reverse(BidirectionalIterator first, BidirectionalIterator last);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，指向元素要进行重排的范围中第一个元素的位置。  
  
 `last`  
 一个双向迭代器，指向元素要进行重排的范围中最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的源范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_reverse.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Reverse the elements in the vector   
   reverse (v1.begin( ), v1.end( ) );  
  
   cout << "The modified vector v1 with values reversed is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 0 1 2 3 4 5 6 7 8 9 ).  
The modified vector v1 with values reversed is:  
 ( 9 8 7 6 5 4 3 2 1 0 ).  
```  
  
##  <a name="reverse_copy"></a>  reverse_copy  
 反转源范围中元素的顺序，同时将这些元素复制到目标范围  
  
```  
template<class BidirectionalIterator, class OutputIterator>  
OutputIterator reverse_copy(   
    BidirectionalIterator  first,  
    BidirectionalIterator Last,  
    OutputIterator  result);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个双向迭代器，指向元素进行置换的源范围中第一个元素的位置。  
  
 `last`  
 一个双向迭代器，指向元素进行置换的源范围中最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，指向要将元素复制到的目标范围内第一个元素的位置。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，指向要将序列已更改的元素复制到的目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的源范围和目标范围必须有效；所有指针必须可取消引用，并且在序列内，最后一个位置可从第一个位置通过递增到达。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_reverse_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2( 10 );  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Reverse the elements in the vector   
   reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );  
  
   cout << "The copy v2 of the reversed vector v1 is:\n ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   cout << "The original vector v1 remains unmodified as:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="rotate"></a>  rotate  
 交换两个相邻范围中的元素。  
  
```  
template<class ForwardIterator>  
 void rotate(ForwardIterator first, ForwardIterator middle, ForwardIterator last);  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个向前迭代器，用于确定要轮换的范围内第一个元素的位置。  
  
 `middle`  
 一个向前迭代器，用于在范围内定义边界，从而确定范围内其元素将与第一部分中的元素进行交换的第二部分中第一个元素的位置。  
  
`Last`  
 一个向前迭代器，用于确定要轮换的范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针必须可取消引用，并且在序列内，最后一个位置可从第一个位置通过递增到达。  
  
 复杂性是线性的最多 ( `last`  -   `first`) 交换。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_rotate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   deque <int> d1;  
   vector <int>::iterator v1Iter1;  
   deque<int>::iterator d1Iter1;  
  
   int i;  
   for ( i = -3 ; i <= 5 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii =0 ; ii <= 5 ; ii++ )  
   {  
      d1.push_back( ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1  << " ";  
   cout << ")." << endl;  
  
   rotate ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) );  
   cout << "After rotating, vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1  << " ";  
   cout << ")." << endl;  
  
   cout << "The original deque d1 is ( " ;  
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
      cout << *d1Iter1  << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= d1.end ( ) - d1.begin ( ) ) {  
      rotate ( d1.begin ( ) , d1.begin ( ) + 1 , d1.end ( ) );  
      cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;  
      for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
         cout << *d1Iter1  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
```Output  
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).  
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).  
The original deque d1 is ( 0 1 2 3 4 5 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 1 2 3 4 5 0 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 2 3 4 5 0 1 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 3 4 5 0 1 2 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 4 5 0 1 2 3 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 5 0 1 2 3 4 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 0 1 2 3 4 5 ).  
```  
  
##  <a name="rotate_copy"></a>  rotate_copy  
 交换源范围中两个相邻范围内的元素，并将结果复制到目标范围。  
  
```  
template<class ForwardIterator, class OutputIterator>  
OutputIterator rotate_copy(  
    ForwardIterator first,  
    ForwardIterator middle,  
    ForwardIterator last,  
    OutputIterator result );  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个向前迭代器，用于确定要轮换的范围内第一个元素的位置。  
  
 `middle`  
 一个向前迭代器，用于在范围内定义边界，从而确定范围内其元素将与第一部分中的元素进行交换的第二部分中第一个元素的位置。  
  
 _ `Last`  
 一个向前迭代器，用于确定要轮换的范围内最后一个元素之后下一个元素的位置。  
  
 `result`  
 一种输出迭代器，用于定址目标范围内第一个元素的位置。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，用于确定目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针必须可取消引用，并且在序列内，最后一个位置可从第一个位置通过递增到达。  
  
 复杂性是线性的最多 ( `last`  -   `first`) 交换。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_rotate_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1 , v2 ( 9 );  
   deque <int> d1 , d2 ( 6 );  
   vector <int>::iterator v1Iter , v2Iter;  
   deque<int>::iterator d1Iter , d2Iter;  
  
   int i;  
   for ( i = -3 ; i <= 5 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii =0 ; ii <= 5 ; ii++ )  
      d1.push_back( ii );  
  
   cout << "Vector v1 is ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )  
      cout << *v1Iter  << " ";  
   cout << ")." << endl;  
  
   rotate_copy ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) , v2.begin ( ) );  
   cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )  
      cout << *v1Iter  << " ";  
   cout << ")." << endl;  
  
   cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;  
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )  
      cout << *v2Iter  << " ";  
   cout << ")." << endl;  
  
   cout << "The original deque d1 is ( " ;  
   for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )  
      cout << *d1Iter  << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= d1.end ( ) - d1.begin ( ) )  
   {  
      rotate_copy ( d1.begin ( ) , d1.begin ( ) + iii , d1.end ( ) , d2.begin ( ) );  
      cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;  
      for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )  
         cout << *d2Iter  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
##  <a name="search"></a>  search  
 在目标范围中搜索其元素与给定序列中的元素相等或在二元谓词指定的意义上等效于给定序列中的元素的序列的第一个匹配项。  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
   ForwardIterator1 search(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      ForwardIterator2 first2,   
      ForwardIterator2 last2);
  
template<class ForwardIterator1, class ForwardIterator2, class Predicate>  
   ForwardIterator1 search(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      ForwardIterator2 first2,   
      ForwardIterator2 last2  
      Predicate comp);
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `last1`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的前向迭代器。  
  
  `first2`  
 用于确定要匹配范围中的第一个元素的位置的前向迭代器。  
  
 `last2`  
 用于确定要匹配范围中的最后元素之后的位置的前向迭代器。  
  
 `comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 用于确定第一个子序列的第一个元素的位置的前向迭代器，这个子序列与指定序列匹配或在二元谓词所指定的某个条件下等效。  
  
### <a name="remarks"></a>备注  
 `operator==` 用于确定元素与指定值之间的匹配必须在其操作数之间施加等效关系。  
  
 引用的范围必须是有效的；所有指针必须是可解除引用的，并且在每个序列内，最后一个位置可从第一个位置通过递增到达。  
  
 平均复杂性与搜索范围的大小呈线性关系，并且最坏情况下复杂性与要搜索序列的大小也呈线性关系。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_search.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice (int elem1, int elem2 )  
{  
   return 2 * elem1 == elem2;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   int ii;  
   for ( ii = 4 ; ii <= 5 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 2 ; iii <= 4 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Searching v1 for first match to L1 under identity  
   vector <int>::iterator result1;  
   result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is at least one match of L1 in v1"  
           << "\n and the first one begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for a match to L1 under the binary predicate twice  
   vector <int>::iterator result2;  
   result2 = search  (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a sequence of elements in v1 that "  
           << "are equivalent\n to those in v2 under the binary "  
           << "predicate twice\n and the first one begins at position "  
           << result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )  
List L1 = ( 20 25 )  
Vector v2 = ( 20 30 40 )  
There is at least one match of L1 in v1  
 and the first one begins at position 4.  
There is a sequence of elements in v1 that are equivalent  
 to those in v2 under the binary predicate twice  
 and the first one begins at position 2.  
```  
  
##  <a name="search_n"></a>  search_n  
 在范围中搜索具有特定值或按二元谓词的指定与此值相关的指定数量的元素。  
  
```  
template<class ForwardIterator1, class Diff2, class Type>  
   ForwardIterator1 search_n(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      Diff2 count,   
      const Type& val);
  
template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>  
   ForwardIterator1 search_n(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      Diff2 count,   
      const Type& val,  
      BinaryPredicate comp);
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 用于确定要搜索范围中第一个元素的位置的前向迭代器。  
  
 `last1`  
 用于确定要搜索范围中最后元素之后下一个元素的位置的前向迭代器。  
  
 `count`  
 要搜索的子序列的大小。  
  
 `val`  
 要搜索的序列中元素的值。  
  
 `comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 用于确定第一个子序列的第一个元素的位置的前向迭代器，这个子序列与指定序列匹配或在二元谓词所指定的某个条件下等效。  
  
### <a name="remarks"></a>备注  
 `operator==` 用于确定元素与指定值之间的匹配必须在其操作数之间施加等效关系。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 复杂性与搜索的大小呈线性关系。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_search_n.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is 1/2 of the first  
bool one_half ( int elem1, int elem2 )  
{  
   return elem1 == 2 * elem2;  
}  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   for ( i = 0 ; i <= 2 ; i++ )  
   {  
      v1.push_back( 5  );  
   }  
  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   for ( i = 0 ; i <= 2 ; i++ )  
   {  
      v1.push_back( 10  );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Searching v1 for first match to (5 5 5) under identity  
   vector <int>::iterator result1;  
   result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match for a sequence ( 5 5 5 ) in v1."  
           << endl;  
   else  
      cout << "There is at least one match of a sequence ( 5 5 5 )"  
           << "\n in v1 and the first one begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for first match to (5 5 5) under one_half  
   vector <int>::iterator result2;  
   result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match for a sequence ( 5 5 5 ) in v1"  
           << " under the equivalence predicate one_half." << endl;  
   else  
      cout << "There is a match of a sequence ( 5 5 5 ) "  
           << "under the equivalence\n predicate one_half "  
           << "in v1 and the first one begins at "  
           << "position "<< result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )  
There is at least one match of a sequence ( 5 5 5 )  
 in v1 and the first one begins at position 6.  
There is a match of a sequence ( 5 5 5 ) under the equivalence  
 predicate one_half in v1 and the first one begins at position 15.  
```  
  
##  <a name="set_difference"></a>  set_difference  
 将属于一个排序的源范围、但不属于另一排序的源范围的所有元素相并到一个排序的目标范围，其中排序条件可通过二元谓词指定。  
  
```  
 template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_difference(  
     InputIterator1  first1,  
     InputIterator1  last1,  
     InputIterator2  first2,  
     InputIterator2  last2,  
     OutputIterator  result  );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_difference(  
    InputIterator1  first1,  
    InputIterator1  last1,  
    InputIterator2  first2,  
    InputIterator2  last2,  
    OutputIterator  result,  
    BinaryPredicate  comp  );  
  
```  
  
### <a name="parameters"></a>参数  
 `first1`  
 一个输入迭代器，用于寻址要相并且排序为一个范围（表示两个源范围的差异）的两个已排序源范围中第一个源范围内第一个元素的位置。  
  
 `last1`  
 一个输入迭代器，用于寻址要相并且排序为一个范围（表示两个源范围的差异）的两个已排序源范围中第一个源范围内最后一个元素之后下一个元素的位置。  
  
 `first2`  
 一个输入迭代器，用于寻址要相并且排序为一个范围（表示两个源范围的差异）的两个连续已排序源范围中第二个源范围内第一个元素的位置。  
  
 `last2`  
 一个输入迭代器，用于寻址要相并且排序为一个范围（表示两个源范围的差异）的两个连续已排序源范围中第二个源范围内最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，用于寻址要将两个源范围相并为一个已排序范围（表示两个源范围的差异）的目标范围内第一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，用于寻址表示两个源范围的差异的已排序目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 目标范围不能与任一源范围重叠，并且应当足够大，以便包含第一个源范围。  
  
 必须按照 `set_difference` 算法对合并范围排序时要使用的相同顺序对已排序源范围分别进行排列，作为应用该算法的前置条件。  
  
 该操作保持不变，因为每个范围内元素的相对顺序均保留在目标范围中。 merge 算法不会修改源范围。  
  
 输入迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 当两个源范围中有相等的元素时，在目标范围中，第一个范围中的元素优先于第二个源范围中的元素。 如果源范围包含某个元素的重复项，以便使第一个源范围中的重复项多于第二个源范围中的重复项，则目标范围将包含这些元素在第一个源范围中出现的次数比其在第二个源范围中出现的次数多出的次数。  
  
 算法的复杂性是线性的最多 2 \* (( *last1-first1*)-( *last2-first2*))-1 比较对于非空源范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_set_diff.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 )  
{  
   if (elem1 < 0)   
      elem1 = - elem1;  
   if (elem2 < 0)   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less-than ordering  
   int i;  
   for ( i = -1 ; i <= 4 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-3 ; ii <= 0 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference in asscending  
   // order with the default binary predicate less <int> ( )  
   Result1 = set_difference ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Set_difference of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference in descending  
   // order specify binary predicate greater<int>( )  
   Result2 = set_difference ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Set_difference of source ranges with binary"  
        << "predicate greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference applying a user  
   // defined binary predicate mod_lesser  
   Result3 = set_difference (  v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Set_difference of source ranges with binary "  
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_intersection"></a>  set_intersection  
 将属于两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。  
  
```  
 template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_intersection(   
      InputIterator1 first1,  
      InputIterator1 last1,  
      InputIterator2 first2,  
      InputIterator2 last2,  
      OutputIterator result );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_intersection(  
      InputIterator1 first1,  
      InputIterator1 last1,  
      InputIterator2 first2,  
      InputIterator2 last2,  
      OutputIterator result,  
      BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的交集）的两个已排序源范围中第一个源范围内第一个元素的位置。  
  
 `last1`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的交集）的两个已排序源范围中第一个源范围内最后一个元素之后下一个元素的位置。  
  
  `first2`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的交集）的两个连续已排序源范围中第二个源范围内第一个元素的位置。  
  
 `last2`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的交集）的两个连续已排序源范围中第二个源范围内最后一个元素之后下一个元素的位置。  
  
 **_** *结果*  
 一个输出迭代器，用于确定要将两个源范围相并为一个已排序范围（表示两个源范围的交集）的目标范围内第一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，用于确定表示两个源范围的交集的已排序目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 目标范围不能与任一源范围重叠，并且应当足够大，以便包含目标范围。  
  
 必须按照 merge 算法对合并范围排序时要使用的相同顺序对已排序源范围分别进行排列，作为应用该算法的前置条件。  
  
 该操作保持不变，因为每个范围内元素的相对顺序均保留在目标范围中。 该算法不会修改源范围。  
  
 输入迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 当两个源范围中有相等的元素时，在目标范围中，第一个范围中的元素优先于第二个源范围中的元素。 如果源范围包含某个元素的重复项，目标范围将包含出现在源范围中的这些元素的最大数目。  
  
 算法的复杂性是线性的最多 2 \* (( *last1-first1*) + ( *last2-first2*))-1 比较对于非空源范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_set_intersection.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>   // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 ) {  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less than ordering  
   int i;  
   for ( i = -1 ; i <= 3 ; i++ )  
      v1a.push_back( i );  
  
   int ii;  
   for ( ii =-3 ; ii <= 1 ; ii++ )  
      v1b.push_back( ii );  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        << "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        << "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
           <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection in asscending order with the  
   // default binary predicate less <int> ( )  
   Result1 = set_intersection ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Intersection of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection in descending order, specify  
   // binary predicate greater<int>( )  
   Result2 = set_intersection ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Intersection of source ranges with binary predicate"  
        << " greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection applying a user-defined  
   // binary predicate mod_lesser  
   Result3 = set_intersection ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Intersection of source ranges with binary predicate "  
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_symmetric_difference"></a>  set_symmetric_difference  
 将属于一个而不是两个排序的源范围的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。  
  
```  
template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_symmetric_difference(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_symmetric_difference(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result,  
    BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的对称差异）的两个已排序源范围中第一个源范围内第一个元素的位置。  
  
 `last1`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的对称差异）的两个已排序源范围中第一个源范围内最后一个元素之后下一个元素的位置。  
  
  `first2`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的对称差异）的两个连续已排序源范围中第二个源范围内第一个元素的位置。  
  
 `last2`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的对称差异）的两个连续已排序源范围中第二个源范围内最后一个元素之后下一个元素的位置。  
  
 **_** *结果*  
 一个输出迭代器，用于确定要将两个源范围相并为一个已排序范围（表示两个源范围的对称差异）的目标范围内第一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，用于确定表示两个源范围的对称差异的已排序目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 目标范围不能与任一源范围重叠，并且应当足够大，以便包含目标范围。  
  
 必须按照 **merge** 算法对合并范围排序时要使用的相同顺序对已排序源范围分别进行排列，作为应用该算法的前置条件。  
  
 该操作保持不变，因为每个范围内元素的相对顺序均保留在目标范围中。 merge 算法不会修改源范围。  
  
 输入迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 当两个源范围中有相等的元素时，在目标范围中，第一个范围中的元素优先于第二个源范围中的元素。 如果源范围包含某个元素的重复项，则目标范围将包含这些元素在其中一个源范围中出现的次数比其在另一个源范围中出现的次数多出的次数的绝对值。  
  
 算法的复杂性是线性的最多 2 \* ((*last1-first1*)-(*last2-first2*))-1 比较对于非空源范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_set_sym_diff.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less-than ordering  
   int i;  
   for ( i = -1 ; i <= 4 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-3 ; ii <= 0 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference in ascending  
   // order with the default binary predicate less <int> ( )  
   Result1 = set_symmetric_difference ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Set_symmetric_difference of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference in descending  
   // order, specify binary predicate greater<int>( )  
   Result2 = set_symmetric_difference ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Set_symmetric_difference of source ranges with binary"  
        << "predicate greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference applying a user  
   // defined binary predicate mod_lesser  
   Result3 = set_symmetric_difference ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Set_symmetric_difference of source ranges with binary "  
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_union"></a>  set_union  
 将至少属于两个排序的源范围之一的所有元素相并为一个排序的目标范围，其中排序条件可通过二元谓词指定。  
  
```  
 template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_union(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result );   
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_union(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result,  
    BinaryPredicate comp );  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的并集）的两个已排序源范围中第一个源范围内第一个元素的位置。  
  
 `last1`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的并集）的两个已排序源范围中第一个源范围内最后一个元素之后下一个元素的位置。  
  
  `first2`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的并集）的两个连续已排序源范围中第二个源范围内第一个元素的位置。  
  
 `last2`  
 一个输入迭代器，用于确定要相并且排序为一个范围（表示两个源范围的并集）的两个连续已排序源范围中第二个源范围内最后一个元素之后下一个元素的位置。  
  
 **_** *结果*  
 一个输出迭代器，用于确定要将两个源范围相并为一个已排序范围（表示两个源范围的并集）的目标范围内第一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素大于另一个元素的理解。 二元谓词采用两个参数，并且应在第一个元素小于第二个元素时返回 **true** ；否则返回 **false** 。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，用于确定表示两个源范围的并集的已排序目标范围内最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有指针必须可取消引用，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 目标范围不能与任一源范围重叠，并且应当足够大，以便包含目标范围。  
  
 必须按照 **merge** 算法对合并范围排序时要使用的相同顺序对已排序源范围分别进行排列，作为应用该算法的前置条件。  
  
 该操作保持不变，因为每个范围内元素的相对顺序均保留在目标范围中。 **merge**算法不会修改源范围。  
  
 输入迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 当两个源范围中有相等的元素时，在目标范围中，第一个范围中的元素优先于第二个源范围中的元素。 如果源范围包含某个元素的重复项，目标范围将包含出现在源范围中的这些元素的最大数目。  
  
 算法的复杂性是线性的最多 2 \* (( *last1-first1*)-( *last2-first2*))-1 比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_set_union.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a, Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less than ordering  
   int i;  
   for ( i = -1 ; i <= 3 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-3 ; ii <= 1 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );  
   vector <int>::iterator Iter2a,  Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a union in ascending order with the default   
    // binary predicate less <int> ( )  
   Result1 = set_union ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Union of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a union in descending order, specify binary   
   // predicate greater<int>( )  
   Result2 = set_union (  v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Union of source ranges with binary predicate greater "  
        << "specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a union applying a user-defined  
   // binary predicate mod_lesser  
   Result3 = set_union ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Union of source ranges with binary predicate "  
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="shuffle"></a>  std::shuffle  
 通过使用随机数生成器重新排列给定范围中的元素。  
  
```  
template<class RandomAccessIterator, class UniformRandomNumberGenerator>  
void shuffle(RandomAccessIterator first,  
    RandomAccessIterator last,  
    UniformRandomNumberGenerator&& gen);  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 指向范围中要重新排序的第一个元素的迭代器（包含第一个元素）。 必须满足 `RandomAccessIterator` 和 `ValueSwappable` 的要求。  
  
 `last`  
 指向范围中要重新排序的最后一个元素的迭代器（不包含最后一个元素）。 必须满足 `RandomAccessIterator` 和 `ValueSwappable` 的要求。  
  
 `gen`  
 
          `shuffle()` 函数将用于运算的随机数生成器。 必须满足 `UniformRandomNumberGenerator` 的要求。  
  
### <a name="remarks"></a>备注  
 有关详细信息和使用 `shuffle()` 的代码示例，请参阅 [\<random>](../standard-library/random.md)。  
  
##  <a name="sort"></a>  sort  
 将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列。  
  
```  
template<class RandomAccessIterator>  
   void sort(  
      RandomAccessIterator first,   
      RandomAccessIterator last);
  
template<class RandomAccessIterator, class Predicate>  
   void sort(  
      RandomAccessIterator first,   
      RandomAccessIterator last,   
      Predicate comp);
  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。  
  
 `last`  
 一种随机访问迭代器，用于定址要排序的范围中最后元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 该二元谓词采用两个参数，并且，如果两个参数按顺序排序，将返回 `true`，否则将返回 `false`。 该比较器函数必须对序列中的元素对进行严格弱排序。 有关详细信息，请参阅[算法](../standard-library/algorithms.md)。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 元素是等效的，但是如果两者都不小于对方，则不一定要相等。 `sort` 算法不稳定，因此不保证保留等效元素的相对顺序。 算法 `stable_sort` 会保留此原始顺序。  
  
 排序复杂性的平均值是*O*( *N*日志*N*)，其中*N* =  *姓氏-名字*。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_sort.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater ( int elem1, int elem2 )  
{  
   return elem1 > elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 5 ; ii++ )  
   {  
      v1.push_back( 2 * ii + 1 );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order. specify binary predicate  
   sort( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "Resorted (greater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   sort( v1.begin( ), v1.end( ), UDgreater );  
   cout << "Resorted (UDgreater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )  
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )  
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )  
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )  
```  
  
##  <a name="sort_heap"></a>  sort_heap  
 将堆转换为排序的范围。  
  
```  
template<class RandomAccessIterator>  
   void sort_heap(  
      RandomAccessIterator first,   
      RandomAccessIterator last);
  
template<class RandomAccessIterator, class Predicate>  
   void sort_heap(  
      RandomAccessIterator first,   
      RandomAccessIterator last,  
      Predicate comp);  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种随机访问迭代器，用于寻址目标堆中第一个元素的位置。  
  
 `last`  
 一种随机访问迭代器，用于寻址目标堆中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="remarks"></a>备注  
 堆有两个属性：  
  
-   第一个元素始终最大。  
  
-   可以在对数时间内添加或删除元素。  
  
 应用此算法后，其应用到的范围将不再是一个堆。  
  
 这种排序算法不稳定，因为不一定保留等效元素的相对顺序。  
  
 堆是实施优先级队列的理想方式，用于实施 C++ 标准库容器适配器 [priority_queue 类](../standard-library/priority-queue-class.md)。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 复杂性是最多*N*日志*N*，其中*N* = (*姓氏-名字*)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_sort_heap.cpp  
// compile with: /EHsc  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <ostream>  
#include <string>  
#include <vector>  
using namespace std;  
  
void print(const string& s, const vector<int>& v) {  
    cout << s << ": ( ";  
  
    for (auto i = v.begin(); i != v.end(); ++i) {  
        cout << *i << " ";  
    }  
  
    cout << ")" << endl;  
}  
  
int main() {  
    vector<int> v;  
    for (int i = 1; i <= 9; ++i) {  
        v.push_back(i);  
    }  
    print("Initially", v);  
  
    random_shuffle(v.begin(), v.end());  
    print("After random_shuffle", v);  
  
    make_heap(v.begin(), v.end());  
    print("     After make_heap", v);  
  
    sort_heap(v.begin(), v.end());  
    print("     After sort_heap", v);  
  
    random_shuffle(v.begin(), v.end());  
    print("             After random_shuffle", v);  
  
    make_heap(v.begin(), v.end(), greater<int>());  
    print("After make_heap with greater<int>", v);  
  
    sort_heap(v.begin(), v.end(), greater<int>());  
    print("After sort_heap with greater<int>", v);  
}  
```  
  
##  <a name="stable_partition"></a>  stable_partition  
 将范围中的元素分为两个不相交的集，满足一元谓词的元素在不满足一元谓词的元素之前，并保留等效元素的相对顺序。  
  
```  
template<class BidirectionalIterator, class Predicate>  
BidirectionalIterator stable_partition(  
    BidirectionalIterator first,  
    BidirectionalIterator last,  
    Predicate pred );  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，用于寻址要分区的范围中第一个元素的位置。  
  
 `last`  
 一种双向迭代器，用于寻址要分区的范围中最后一个元素之后下一个元素的位置。  
  
 `_Pred`  
 用户定义的谓词函数对象，用于定义如果元素要分类时应满足的条件。 谓词采用一个参数并返回 **true** 或 **false**。  
  
### <a name="return-value"></a>返回值  
 一种双向迭代器，用于寻址范围中不满足谓词条件的第一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 元素 *a* 和 *b* 是等效的，但是如果 *Pr* ( *a*,  *b*) 和  *Pr* ( *b*,  *a*) 均为 false（其中 *Pr* 是指定参数的谓词），则不一定要相等。 **stable_ partition** 算法稳定，可保证保留等效元素的相对顺序。 算法 **partition** 不必保留此原始顺序。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_stable_partition.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater5 ( int value ) {  
   return value >5;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2, result;  
  
   int i;  
   for ( i = 0 ; i <= 10 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 4 ; ii++ )  
      v1.push_back( 5 );  
  
   random_shuffle(v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Partition the range with predicate greater10  
   result = stable_partition (v1.begin( ), v1.end( ), greater5 );  
   cout << "The partitioned set of elements in v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "The first element in v1 to fail to satisfy the"  
        << "\n predicate greater5 is: " << *result << "." << endl;  
}  
```  
  
##  <a name="stable_sort"></a>  stable_sort  
 将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列，并保留等效元素的相对顺序。  
  
```  
template<class BidirectionalIterator>  
 void stable_sort( BidirectionalIterator first, BidirectionalIterator last );  
  
template<class BidirectionalIterator, class BinaryPredicate>  
void stable_sort(   
    BidirectionalIterator first,  
    BidirectionalIterator last,   
    BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种双向迭代器，用于寻址要排序的范围中第一个元素的位置。  
  
 `last`  
 一种双向迭代器，用于寻址要排序的范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="remarks"></a>备注  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 元素是等效的，但是如果两者都不小于对方，则不一定要相等。 **sort** 算法是稳定的，可保证保留等效元素的相对顺序。  
  
 运行时间复杂性`stable_sort`取决于可用，内存量 （给定足够的内存） 的最佳大小写，但*O*( *N*日志*N*) 和最坏情况下是*O*( *N* (日志*N* ) 2)，其中*N* =  *姓氏的名字。* 通常情况下，**sort** 算法比 `stable_sort` 快得多。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_stable_sort.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater (int elem1, int elem2 )  
{  
   return elem1 > elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i  );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   stable_sort(v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order, specify binary predicate  
   stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "Resorted (greater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   stable_sort(v1.begin( ), v1.end( ), UDgreater );  
   cout << "Resorted (UDgreater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )  
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )  
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )  
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )  
```  
  
##  <a name="swap"></a>  swap  
 第一次重写交换两个对象的值。 第二次重写交换两个对象数组之间的值。  
  
```  
template<class Type>  
   void swap(  
      Type& left,   
      Type& right);  
template<class Type, size_t N>  
   void swap(  
      Type (& left)[N],  
      Type (& right)[N]);\r
  
```  
  
### <a name="parameters"></a>参数  
 `left`  
 对于第一次重写，为交换其内容的第一个对象。 对于第二次重写，为交换其内容的第一个对象数组。  
  
 `right`  
 对于第一次重写，为交换其内容的第二个对象。 对于第二次重写，为交换其内容的第二个对象数组。  
  
### <a name="remarks"></a>备注  
 第一次重载设计用于对各个对象进行操作。 第二次重载交换两个数组之间对象的内容。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_swap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2, result;  
  
   for ( int i = 0 ; i <= 10 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   for ( int ii = 0 ; ii <= 4 ; ii++ )  
   {  
      v2.push_back( 5 );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   swap( v1, v2 );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).  
Vector v2 is ( 5 5 5 5 5 ).  
Vector v1 is ( 5 5 5 5 5 ).  
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).  
```  
  
##  <a name="swap_ranges"></a>  swap_ranges  
 将一个范围中的元素与另一大小相等的范围中的元素交换。  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
ForwardIterator2 swap_ranges(   
   ForwardIterator1 first1,  
   ForwardIterator1 last1,  
   ForwardIterator2 first2 );  
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一种前向迭代器，指向其元素将要进行交换的第一个范围的第一个位置。  
  
 `last1`  
 一种前向迭代器，指向其元素将要进行交换的第一个范围的最后一个位置之后的位置。  
  
  `first2`  
 一种前向迭代器，指向其元素将要进行交换的第二个范围的第一个位置。  
  
### <a name="return-value"></a>返回值  
 一种前向迭代器，指向其元素将要进行交换的第二个范围的最后一个位置之后的位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须是有效的；所有指针必须是可解除引用的，并且在每个序列内，最后一个位置可从第一个位置通过递增到达。 第二个范围必须与第一个范围一样大。  
  
 复杂性是线性的`last1`  -   `first1`交换执行。 如果交换同一类型的容器中的元素，应使用该容器中的 `swap` 成员函数，因为该成员函数通常具有恒定的复杂性。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_swap_ranges.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1;  
   deque <int> d1;  
   vector <int>::iterator v1Iter1;  
   deque<int>::iterator d1Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii =4 ; ii <= 9 ; ii++ )  
   {  
      d1.push_back( 6 );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1  << " ";  
   cout << ")." << endl;  
  
   cout << "Deque d1 is  ( " ;  
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
      cout << *d1Iter1  << " ";  
   cout << ")." << endl;  
  
   swap_ranges ( v1.begin ( ) , v1.end ( ) , d1.begin ( ) );  
  
   cout << "After the swap_range, vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "After the swap_range deque d1 is   ( " ;  
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
      cout << *d1Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 0 1 2 3 4 5 ).  
Deque d1 is  ( 6 6 6 6 6 6 ).  
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).  
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).  
```  
  
##  <a name="transform"></a>  transform  
 将指定的函数对象应用于源范围中的每个元素或两个源范围中的元素对，并将函数对象的返回值复制到目标范围。  
  
```  
 template<class InputIterator, class OutputIterator, class UnaryFunction>  
 OutputIterator transform(  
    InputIterator first1,  
    InputIterator last1,  
    OutputIterator result,  
    UnaryFunction _Func );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>  
OutputIterator transform(   
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    OutputIterator result,  
    BinaryFunction _Func );  
  
```  
  
### <a name="parameters"></a>参数  
  `first1`  
 一种输入迭代器，用于寻址要操作的第一个源范围内第一个元素的位置。  
  
 `last1`  
 一种输入迭代器，用于寻址要操作的第一个源范围内最后一个元素之后下一个元素的位置。  
  
  `first2`  
 一种输入迭代器，用于定址所操作的第二个源范围内第一个元素的位置。  
  
 `result`  
 一种输出迭代器，用于定址目标范围内第一个元素的位置。  
  
 `_Func`  
 在应用到第一个源范围中每个元素的第一版算法中使用的用户定义一元函数对象，或者在按前向顺序成对应用到两个源范围的第二版算法中使用的用户定义 (UD) 二元函数对象。  
  
### <a name="return-value"></a>返回值  
 一种输出迭代器，用于寻址接收通过函数对象转换的输出元素的目标范围内最后元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的范围必须是有效的；所有指针必须是可解除引用的，并且在每个序列内，最后一个位置必须可从第一个位置通过递增到达。 目标范围必须足够大，以包含已转换的源范围。  
  
 如果`result`设置为等于`first1`算法的第一个版本中，然后在源和目标范围将是相同的并且将就地修改序列。 但是`result`可能不解决范围内的位置 [`first1` + 1， `last1`)。  
  
 复杂性是线性的最多 (`last1` -  `first1`) 比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_transform.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
// The function object multiplies an element by a Factor  
template <class Type>  
class MultValue  
{  
   private:  
      Type Factor;   // The value to multiply by  
   public:  
      // Constructor initializes the value to multiply by  
      MultValue ( const Type& val ) : Factor ( val ) {  
      }  
  
      // The function call for the element to be multiplied  
      Type operator ( ) ( Type& elem ) const   
      {  
         return elem * Factor;  
      }  
};  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2 ( 7 ), v3 ( 7 );  
   vector <int>::iterator Iter1, Iter2 , Iter3;  
  
   // Constructing vector v1  
   int i;  
   for ( i = -4 ; i <= 2 ; i++ )  
   {  
      v1.push_back(  i );  
   }  
  
   cout << "Original vector  v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Modifying the vector v1 in place  
   transform (v1.begin ( ) , v1.end ( ) , v1.begin ( ) , MultValue<int> ( 2 ) );  
   cout << "The elements of the vector v1 multiplied by 2 in place gives:"  
        << "\n v1mod = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Using transform to multiply each element by a factor of 5  
   transform ( v1.begin ( ) , v1.end ( ) , v2.begin ( ) , MultValue<int> ( 5 ) );  
  
   cout << "Multiplying the elements of the vector v1mod\n "  
        <<  "by the factor 5 & copying to v2 gives:\n v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // The second version of transform used to multiply the   
   // elements of the vectors v1mod & v2 pairwise  
   transform ( v1.begin ( ) , v1.end ( ) ,  v2.begin ( ) , v3.begin ( ) ,   
      multiplies <int> ( ) );  
  
   cout << "Multiplying elements of the vectors v1mod and v2 pairwise "  
        <<  "gives:\n v3 = ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).  
The elements of the vector v1 multiplied by 2 in place gives:  
 v1mod = ( -8 -6 -4 -2 0 2 4 ).  
Multiplying the elements of the vector v1mod  
 by the factor 5 & copying to v2 gives:  
 v2 = ( -40 -30 -20 -10 0 10 20 ).  
Multiplying elements of the vectors v1mod and v2 pairwise gives:  
 v3 = ( 320 180 80 20 0 20 80 ).  
```  
  
##  <a name="unique"></a>  unique  
 移除指定范围中彼此相邻的重复元素。  
  
```  
template<class ForwardIterator>  
   ForwardIterator unique(  
      ForwardIterator first,   
      ForwardIterator last);
  
template<class ForwardIterator, class Predicate>  
   ForwardIterator unique(  
      ForwardIterator first,   
      ForwardIterator last,  
      Predicate comp);
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一种前向迭代器，用于寻址要进行重复删除扫描的范围中第一个元素的位置。  
  
 `last`  
 一种前向迭代器，用于寻址要进行重复删除扫描的范围中最后一个元素之后下一个元素的位置。  
  
 `comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 一种前向迭代器，指向不包含连续重复项的已修改序列新末尾位置，用于寻址未删除的最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 这两种形式的算法都可删除连续一对相等元素的第二个副本。  
  
 该算法的操作是稳定的，因此未删除的元素的相对顺序不会发生更改。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。 **unique** 算法不会更改序列中的元素数，并且已修改序列末尾位置之外的元素可取消引用，但未指定。  
  
 复杂性是线性的需要 ( `last`  -   `first`)-1 比较。  
  
 List 提供了更高效的成员函数 "unique"，它可能会表现得更好。  
  
 不能在关联容器上使用这些算法。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_unique.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
  
// Return whether modulus of elem1 is equal to modulus of elem2  
bool mod_equal ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 == elem2;  
};  
  
int main( )  
{  
   vector <int> v1;  
   vector <int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,  
         v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( 5 );  
      v1.push_back( -5 );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
   {  
      v1.push_back( 4 );  
   }  
   v1.push_back( 7 );  
  
   cout << "Vector v1 is ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove consecutive duplicates  
   v1_NewEnd1 = unique ( v1.begin ( ) , v1.end ( ) );  
  
   cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove consecutive duplicates under the binary prediate mod_equals  
   v1_NewEnd2 = unique ( v1.begin ( ) , v1_NewEnd1 , mod_equal );  
  
   cout << "Removing adjacent duplicates from vector v1 under the\n "  
        << " binary predicate mod_equal gives\n ( " ;  
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )  
      cout << *v1_Iter2 << " ";  
   cout << ")." << endl;  
  
   // Remove elements if preceded by an element that was greater  
   v1_NewEnd3 = unique ( v1.begin ( ) , v1_NewEnd2, greater<int>( ) );  
  
   cout << "Removing adjacent elements satisfying the binary\n "  
        << " predicate mod_equal from vector v1 gives ( " ;  
   for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )  
      cout << *v1_Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).  
Removing adjacent duplicates from vector v1 gives  
 ( 5 -5 5 -5 5 -5 5 -5 4 7 ).  
Removing adjacent duplicates from vector v1 under the  
  binary predicate mod_equal gives  
 ( 5 4 7 ).  
Removing adjacent elements satisfying the binary  
  predicate mod_equal from vector v1 gives ( 5 7 ).  
```  
  
##  <a name="unique_copy"></a>  unique_copy  
 将源范围中的元素复制到目标范围，彼此相邻的重复元素除外。  
  
```  
 template<class InputIterator, class OutputIterator>  
 OutputIterator unique_copy( InputIterator first,  
    InputIterator last,  
    OutputIterator result );  
  
template<class InputIterator, class OutputIterator, class BinaryPredicate>  
OutputIterator unique_copy( InputIterator first,  
    InputIterator last,  
    OutputIterator result,  
    BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>参数  
  `first`  
 一个向前迭代器，用于寻址源范围中要复制的第一个元素的位置。  
  
 `last`  
 一个向前迭代器，用于寻址源范围中要复制的最后一个元素之后下一个元素的位置。  
  
 `result`  
 一个输出迭代器，用于寻址接收删除的连续副本的目标范围中第一个元素的位置。  
  
 `comp`  
 用于定义两个元素被视为等效时应满足的条件的用户定义谓词函数对象。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 一个输出迭代器，用于寻址接收删除的连续副本的目标范围中最后一个元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 这两种形式的算法都可删除连续一对相等元素的第二个副本。  
  
 该算法的操作是稳定的，因此未删除的元素的相对顺序不会发生更改。  
  
 引用的范围必须有效；所有指针都必须可以引用，并且在序列中，可通过递增从第一个位置到达最后一个位置。  
  
 复杂性是线性的需要 ( `last`  -   `first`) 比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_unique_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
  
// Return whether modulus of elem1 is equal to modulus of elem2  
bool mod_equal ( int elem1, int elem2 ) {  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 == elem2;  
};  
  
int main() {  
   vector <int> v1;  
   vector <int>::iterator v1_Iter1, v1_Iter2,  
         v1_NewEnd1, v1_NewEnd2;  
  
   int i;  
   for ( i = 0 ; i <= 1 ; i++ ) {  
      v1.push_back( 5 );  
      v1.push_back( -5 );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 2 ; ii++ )  
      v1.push_back( 4 );  
   v1.push_back( 7 );  
  
   int iii;  
   for ( iii = 0 ; iii <= 5 ; iii++ )  
      v1.push_back( 10 );  
  
   cout << "Vector v1 is\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   // Copy first half to second, removing consecutive duplicates  
   v1_NewEnd1 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 8, v1.begin ( ) + 8 );  
  
   cout << "Copying the first half of the vector to the second half\n "  
        << "while removing adjacent duplicates gives\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   int iv;  
   for ( iv = 0 ; iv <= 7 ; iv++ )  
      v1.push_back( 10 );  
  
   // Remove consecutive duplicates under the binary prediate mod_equals  
   v1_NewEnd2 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 14,   
      v1.begin ( ) + 14 , mod_equal );  
  
   cout << "Copying the first half of the vector to the second half\n "  
        << " removing adjacent duplicates under mod_equals gives\n ( " ;  
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )  
      cout << *v1_Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="upper_bound"></a>  upper_bound  
 在排序的范围中查找其值大于指定值的第一个元素的位置，其中排序条件可通过二元谓词指定。  
  
```  
template<class ForwardIterator, class Type>  
   ForwardIterator upper_bound(  
      ForwardIterator first,   
      ForwardIterator last,  
      const Type& value);
  
template<class ForwardIterator, class Type, class Predicate>  
   ForwardIterator upper_bound(  
      ForwardIterator first,   
      ForwardIterator last,  
      const Type& value,  
      Predicate comp);
  
```  
  
### <a name="parameters"></a>参数  
 `first`  
 要搜索的范围中第一个元素的位置。  
  
 `last`  
 要搜索的范围中最后一个元素之后下一个元素的位置。  
  
 `value`  
 返回排序范围中需要被迭代器寻址的元素值超越的值。  
  
 `comp`  
 用户定义的谓词函数对象，用于定义对一个元素小于另一个元素的理解。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。  
  
### <a name="return-value"></a>返回值  
 一种前向迭代器，指向其值大于指定值的第一个元素的位置。  
  
### <a name="remarks"></a>备注  
 引用的已排序源范围必须有效；所有迭代器必须可取消引用，并且在序列内，最后一个位置必须可从第一个位置通过递增到达。  
  
 已排序的范围是使用 `upper_bound` 的前置条件，其中排序标准与通过二元谓词指定的排序标准相同。  
  
 `upper_bound` 不会修改该范围。  
  
 前向迭代器的值类型需小于比较元素才能进行排序；因此，给定两个元素，可以确定这两个元素相等（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。  
  
 该算法的复杂性与随机访问迭代器是对数关系，而对于其他迭代器是线性关系，并且与步骤数成比例 ( `last - first`)。  
  
### <a name="example"></a>示例  
  
```cpp  
// alg_upper_bound.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser( int elem1, int elem2 )  
{  
    if ( elem1 < 0 )  
        elem1 = - elem1;  
    if ( elem2 < 0 )  
        elem2 = - elem2;  
    return elem1 < elem2;  
}  
  
int main( )  
{  
    using namespace std;  
  
    vector<int> v1;  
    // Constructing vector v1 with default less-than ordering  
    for ( auto i = -1 ; i <= 4 ; ++i )  
    {  
        v1.push_back(  i );  
    }  
  
    for ( auto ii =-3 ; ii <= 0 ; ++ii )  
    {  
        v1.push_back(  ii  );  
    }  
  
    cout << "Starting vector v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    sort(v1.begin(), v1.end());  
    cout << "Original vector v1 with range sorted by the\n "  
        << "binary predicate less than is v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vector v2 with range sorted by greater  
    vector<int> v2(v1);  
  
    sort(v2.begin(), v2.end(), greater<int>());  
  
    cout << "Original vector v2 with range sorted by the\n "  
        << "binary predicate greater is v2 = ( " ;  
    for (const auto &Iter : v2)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vectors v3 with range sorted by mod_lesser  
    vector<int> v3(v1);  
    sort(v3.begin(), v3.end(), mod_lesser);  
  
    cout << "Original vector v3 with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3 = ( " ;  
    for (const auto &Iter : v3)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Demonstrate upper_bound  
  
    vector<int>::iterator Result;  
  
    // upper_bound of 3 in v1 with default binary predicate less<int>()  
    Result = upper_bound(v1.begin(), v1.end(), 3);  
    cout << "The upper_bound in v1 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // upper_bound of 3 in v2 with the binary predicate greater<int>( )  
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());  
    cout << "The upper_bound in v2 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // upper_bound of 3 in v3 with the binary predicate  mod_lesser  
    Result = upper_bound(v3.begin(), v3.end(), 3,  mod_lesser);  
    cout << "The upper_bound in v3 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
}  
  
```  
## <a name="see-also"></a>另请参阅   
 [\<algorithm>](../standard-library/algorithm.md)
