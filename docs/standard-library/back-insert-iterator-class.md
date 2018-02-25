---
title: "back_insert_iterator 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7646b26c1651ccf93fcc3bcb6828ae402ea5ca07
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="backinsertiterator-class"></a>back_insert_iterator 类
描述满足输出迭代器需求的迭代器适配器。 它将元素插入到序列后端而非覆盖序列，因此它提供的语义不同于 C++ 序列容器的迭代器所提供的覆盖语义。 `back_insert_iterator` 类针对容器类型进行模板化。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Container>  
class back_insert_iterator;  
```  
  
#### <a name="parameters"></a>参数  
 `Container`  
 要通过 `back_insert_iterator` 将元素插入后端的容器的类型。  
  
## <a name="remarks"></a>备注  
 此容器必须满足末尾插入序列的要求，可以从中在分期常量时间内将元素插入序列末尾。 [deque 类](../standard-library/deque-class.md)、[list 类](../standard-library/list-class.md) 和 [vector 类](../standard-library/vector-class.md)定义的 C++ 标准库序列容器，提供需要的 `push_back` 成员函数并满足这些需求。 在这三个容器和字符串中，可以对其中每一个进行适配以便与 `back_insert_iterator` 一起使用。 `back_insert_iterator` 必须使用其容器进行初始化。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[back_insert_iterator](#back_insert_iterator)|构造在容器的最后一个元素后插入元素的 `back_insert_iterator`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#container_type)|为 `back_insert_iterator` 提供容器的类型。|  
|[reference](#reference)|为 `back_insert_iterator` 提供引用的类型。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator*](#op_star)|取消引用运算符，用于实现末尾插入的输出迭代器表达式 * `i` = `x`。|  
|[operator++](#op_add_add)|将 `back_insert_iterator` 递增到下一个可用来存储值的位置。|  
|[operator=](#op_eq)|赋值运算符，用于实现末尾插入的输出迭代器表达式 *`i` = `x`。|  
  
## <a name="requirements"></a>惠?  
 **标头**：\<iterator>  
  
 **命名空间：** std  
  
##  <a name="back_insert_iterator"></a>  back_insert_iterator::back_insert_iterator  
 构造在容器的最后一个元素后插入元素的 `back_insert_iterator`。  
  
```   
explicit back_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>参数  
 `_Cont`  
 `back_insert_iterator` 要向其中插入元素的容器。  
  
### <a name="return-value"></a>返回值  
 针对参数容器的 `back_insert_iterator`。  
  
### <a name="example"></a>示例  
  
```cpp  
// back_insert_iterator_back_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Insertions with member function  
   back_inserter ( vec ) = 40;  
   back_inserter ( vec ) = 50;  
  
   // Alternatively, insertions can be done with template function  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 600;  
   backiter++;  
 *backiter = 700;  
  
   cout << "After the insertions, the vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 1 2 3 ).  
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).  
```  
  
##  <a name="container_type"></a>  back_insert_iterator::container_type  
 为 `back_insert_iterator` 提供容器的类型。  
  
```   
typedef Container  
container_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **Container** 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// back_insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back (  i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The original vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> >::container_type vec1 = vec;  
   back_inserter ( vec1 ) = 40;  
  
   cout << "After the insertion, the vector is: ( ";  
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector vec is: ( 1 2 3 ).  
After the insertion, the vector is: ( 1 2 3 40 ).  
```  
  
##  <a name="op_star"></a>  back_insert_iterator::operator*  
 用于实现输出迭代器表达式 \* *i* = *x* 的取消引用运算符。  
  
```  
back_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>返回值  
 对插入到容器末尾的元素的引用。  
  
### <a name="remarks"></a>备注  
 用于实现输出迭代器表达式 **\*Iter** = **value**。 如果 **Iter** 是对序列中元素进行寻址的迭代器，则 **\*Iter** = **value** 会替换该元素的值，且不会改变此序列中元素的总数。  
  
### <a name="example"></a>示例  
  
```cpp  
// back_insert_iterator_back_insert.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 10;  
   backiter++;      // Increment to the next element  
 *backiter = 20;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 ).  
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).  
```  
  
##  <a name="op_add_add"></a>  back_insert_iterator::operator++  
 将 `back_insert_iterator` 递增到下一个可用来存储值的位置。  
  
```  
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>返回值  
 `back_insert_iterator`，它寻址下一个可用来存储值的位置。  
  
### <a name="remarks"></a>备注  
 前递增和后递增运算符将返回相同的结果。  
  
### <a name="example"></a>示例  
  
```cpp  
// back_insert_iterator_op_incre.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 3 ; ++i )    
   {  
      vec.push_back ( 10 * i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 30;  
   backiter++;      // Increment to the next element  
 *backiter = 40;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 10 20 ).  
After the insertions, the vector vec becomes: ( 10 20 30 40 ).  
```  
  
##  <a name="op_eq"></a>  back_insert_iterator::operator=  
 将值追加或放回到容器的末尾。  
  
```  
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>参数  
 `val`  
 要插入到容器中的值。  
  
### <a name="return-value"></a>返回值  
 对插入到容器末尾的最后一个元素的引用。  
  
### <a name="remarks"></a>备注  
 第一个成员运算符会对 `Container.push_back( val)` 求值，  
  
 然后返回 `*this`。 第二个成员运算符会求值  
  
 `container->push_back((typename Container::value_type&&)val)`,  
  
 然后返回 `*this`。  
  
### <a name="example"></a>示例  
  
```cpp  
// back_insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 10;  
   backiter++;      // Increment to the next element  
 *backiter = 20;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="reference"></a>  back_insert_iterator::reference  
 为 `back_insert_iterator` 提供引用的类型。  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述对关联容器控制的序列元素的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// back_insert_iterator_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> >::reference   
        RefLast = *(vec.end ( ) - 1 );  
   cout << "The last element in the vector vec is: "   
        << RefLast << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 ).  
The last element in the vector vec is: 3.  
```  
  
## <a name="see-also"></a>请参阅  
 [\<iterator>](../standard-library/iterator.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)

