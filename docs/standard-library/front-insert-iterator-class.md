---
title: "front_insert_iterator 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/std::front_insert_iterator
- front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- front_insert_iterator class
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 6468f372324cb6f62b5b09524cfbf5386b1502c6
ms.lasthandoff: 02/24/2017

---
# <a name="frontinsertiterator-class"></a>front_insert_iterator 类
描述满足输出迭代器需求的迭代器适配器。 它将元素插入到序列前端而非覆盖序列，因此它提供的语义不同于 C++ 序列容器的迭代器所提供的覆盖语义。 `front_insert_iterator` 类针对容器类型进行模板化。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Container>  
class front_insert_iterator;  
```  
  
#### <a name="parameters"></a>参数  
 `Container`  
 要通过 `front_insert_iterator` 将元素插入前端的容器的类型。  
  
## <a name="remarks"></a>备注  
 此容器必须满足前端插入序列的需求，可以从中在分期常量时间内将元素插入序列开头。 [deque 类](../standard-library/deque-class.md) 和 [list 类](../standard-library/list-class.md) 定义的 C++ 标准库序列容器提供需要的 `push_front` 成员函数并满足这些需求。 相反，[vector 类](../standard-library/vector-class.md)定义的序列容器不满足这些需求，无法进行适配化以便与 `front_insert_iterator` 一起使用。 `front_insert_iterator` 必须使用其容器进行初始化。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[front_insert_iterator](#front_insert_iterator__front_insert_iterator)|创建一个可以在指定容器对象前端插入元素的迭代器。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#front_insert_iterator__container_type)|表示要从中执行前端插入的容器的类型。|  
|[reference](#front_insert_iterator__reference)|一种类型，此类型提供对关联容器所控制序列中的元素的引用。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator*](#front_insert_iterator__operator_star)|取消引用用于实现前端插入的输出迭代器表达式 * `i` = `x` 的运算符。|  
|[operator++](#front_insert_iterator__operator_add_add)|将 `front_insert_iterator` 递增到下一个可用来存储值的位置。|  
|[operator=](#front_insert_iterator__operator_eq)|赋值运算符，用于实现前端插入的输出迭代器表达式 * `i` = `x`。|  
  
## <a name="requirements"></a>要求  
 **标头**：\<iterator>  
  
 **命名空间：** std  
  
##  <a name="front_insert_iterator__container_type"></a>  front_insert_iterator::container_type  
 表示要从中执行前端插入的容器的类型。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **Container** 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// front_insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> >::container_type L2 = L1;  
   front_inserter ( L2 ) = 20;  
   front_inserter ( L2 ) = 10;  
   front_inserter ( L2 ) = 40;  
  
   list <int>::iterator vIter;  
   cout << "The list L2 is: ( ";  
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L2 is: ( 40 10 20 ).  
*\  
```  
  
##  <a name="front_insert_iterator__front_insert_iterator"></a>  front_insert_iterator::front_insert_iterator  
 创建一个可以在指定容器对象前端插入元素的迭代器。  
  
```  
explicit front_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>参数  
 `_Cont`  
 `front_insert_iterator` 要将元素插入到其中的容器对象。  
  
### <a name="return-value"></a>返回值  
 参数容器对象的 `front_insert_iterator`。  
  
### <a name="example"></a>示例  
  
```cpp  
// front_insert_iterator_front_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = -1 ; i < 9 ; ++i )    
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   // Using the member function to insert an element  
   front_inserter ( L ) = 20;  
  
   // Alternatively, one may use the template function  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="front_insert_iterator__operator_star"></a>  front_insert_iterator::operator*  
 取消引用返回其所寻址元素的插入迭代器。  
  
```  
front_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>返回值  
 此成员函数返回已寻址元素的值。  
  
### <a name="remarks"></a>备注  
 用于实现输出迭代器表达式 **\*Iter** = **value**。 如果 **Iter** 是对序列中元素进行寻址的迭代器，则 **\*Iter** = **value** 会替换该元素的值，且不会改变此序列中元素的总数。  
  
### <a name="example"></a>示例  
  
```cpp  
// front_insert_iterator_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for ( i = -1 ; i < 9 ; ++i )   
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 20;  
  
   // Alternatively, you may use  
   front_inserter ( L ) = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="front_insert_iterator__operator_add_add"></a>  front_insert_iterator::operator++  
 将 `back_insert_iterator` 递增到下一个可用来存储值的位置。  
  
```  
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>返回值  
 `front_insert_iterator`，它寻址下一个可用来存储值的位置。  
  
### <a name="remarks"></a>备注  
 前递增和后递增运算符将返回相同的结果。  
  
### <a name="example"></a>示例  
  
```cpp  
// front_insert_iterator_op_incre.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="front_insert_iterator__operator_eq"></a>  front_insert_iterator::operator=  
 将值追加（推送）到容器开头。  
  
```  
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>参数  
 `val`  
 要赋给容器的值。  
  
### <a name="return-value"></a>返回值  
 对插入到容器开头的最后一个元素的引用。  
  
### <a name="remarks"></a>备注  
 第一个成员运算符会对 `container.push_front( val)` 求值，然后返回 `*this`。  
  
 第二个成员运算符会求值  
  
 `container->push_front((typename Container::value_type&&) val)`,  
  
 然后返回 `*this`。  
  
### <a name="example"></a>示例  
  
```cpp  
// front_insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="front_insert_iterator__reference"></a>  front_insert_iterator::reference  
 一种类型，此类型提供对关联容器所控制序列中的元素的引用。  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// front_insert_iterator_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L;  
   front_insert_iterator<list<int> > fiivIter( L );  
 *fiivIter = 10;  
 *fiivIter = 20;  
 *fiivIter = 30;  
  
   list<int>::iterator LIter;  
   cout << "The list L is: ( ";  
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)  
      cout << *LIter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator<list<int> >::reference   
        RefFirst = *(L.begin ( ));  
   cout << "The first element in the list L is: "   
        << RefFirst << "." << endl;  
}  
\* Output:   
The list L is: ( 30 20 10 ).  
The first element in the list L is: 30.  
*\  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<iterator>](../standard-library/iterator.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


