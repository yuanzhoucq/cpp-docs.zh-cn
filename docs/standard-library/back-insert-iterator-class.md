---
title: "back_insert_iterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator/std::back_insert_iterator"
  - "std::back_insert_iterator"
  - "back_insert_iterator"
  - "std.back_insert_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "back_insert_iterator 类"
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# back_insert_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 此容器必须满足末尾插入序列的要求，可以从中在分期常量时间内将元素插入序列末尾。 定义的 STL 序列容器 [deque 类](../standard-library/deque-class.md), ，[list 类](../standard-library/list-class.md) 和 [vector 类](../standard-library/vector-class.md) 提供需要 `push_back` 成员函数并满足这些要求。 在这三个容器和字符串中，可以对其中每一个进行适配以便与 `back_insert_iterator` 一起使用。 `back_insert_iterator` 必须使用其容器进行初始化。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[back_insert_iterator](#back_insert_iterator__back_insert_iterator)|构造在容器的最后一个元素后插入元素的 `back_insert_iterator`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#back_insert_iterator__container_type)|为 `back_insert_iterator` 提供容器的类型。|  
|[引用](#back_insert_iterator__reference)|为 `back_insert_iterator` 提供引用的类型。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 *](#back_insert_iterator__operator_star)|取消引用运算符，用于实现输出迭代器表达式 * `i` = `x` 末尾插入。|  
|[operator + +](#back_insert_iterator__operator_add_add)|将 `back_insert_iterator` 递增到下一个可用来存储值的位置。|  
|[运算符 =](#back_insert_iterator__operator_eq)|赋值运算符，用于实现输出迭代器表达式 * `i` = `x` 末尾插入。|  
  
## <a name="requirements"></a>要求  
 **标头**: \< 迭代器>  
  
 **命名空间：** std  
  
##  <a name="a-namebackinsertiteratorbackinsertiteratora-backinsertiteratorbackinsertiterator"></a><a name="back_insert_iterator__back_insert_iterator"></a>  back_insert_iterator:: back_insert_iterator  
 构造在容器的最后一个元素后插入元素的 `back_insert_iterator`。  
  
```  
 
explicit back_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>参数  
 `_Cont`  
 容器的 `back_insert_iterator` 是插入到的元素。  
  
### <a name="return-value"></a>返回值  
 一个 `back_insert_iterator` 参数容器。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namebackinsertiteratorcontainertypea-backinsertiteratorcontainertype"></a><a name="back_insert_iterator__container_type"></a>  back_insert_iterator:: container_type  
 为 `back_insert_iterator` 提供容器的类型。  
  
```  
 
typedef Container  
container_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **容器**。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namebackinsertiteratoroperatorstara-backinsertiteratoroperator"></a><a name="back_insert_iterator__operator_star"></a>  back_insert_iterator:: operator *  
 取消引用运算符，用于实现输出迭代器表达式 \* *我* = *x*。  
  
```  
back_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>返回值  
 对容器的后面插入元素的引用。  
  
### <a name="remarks"></a>备注  
 用于实现输出迭代器表达式 **\*Iter** = **值**。 如果 **Iter** 是一个迭代器，然后在序列中，元素的地址 **\*Iter** = **值** 用值替换该元素并不会更改序列中元素的总数。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namebackinsertiteratoroperatoraddadda-backinsertiteratoroperator"></a><a name="back_insert_iterator__operator_add_add"></a>  back_insert_iterator:: operator + +  
 将 `back_insert_iterator` 递增到下一个可用来存储值的位置。  
  
```  
back_insert_iterator<Container>& operator++();

back_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>返回值  
 一个 `back_insert_iterator` 寻址下一个值可能会存储到其中的位置。  
  
### <a name="remarks"></a>备注  
 Preincrementation 和 postincrementation 运算符将返回相同的结果。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namebackinsertiteratoroperatoreqa-backinsertiteratoroperator"></a><a name="back_insert_iterator__operator_eq"></a>  back_insert_iterator:: operator =  
 追加或推送到后端的容器上的值。  
  
```  
back_insert_iterator<Container>& operator=(typename Container::const_reference val);

    back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>参数  
 ` val`  
 要插入到容器的值。  
  
### <a name="return-value"></a>返回值  
 对容器的后面插入的最后一个元素的引用。  
  
### <a name="remarks"></a>备注  
 在第一个成员操作数的计算 `Container.push_back( val)`,，  
  
 然后返回 `*this`。 在第二个成员操作数的计算  
  
 `container->push_back((typename Container::value_type&&)val)`,  
  
 然后返回 `*this`。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namebackinsertiteratorreferencea-backinsertiteratorreference"></a><a name="back_insert_iterator__reference"></a>  back_insert_iterator:: reference  
 为 `back_insert_iterator` 提供引用的类型。  
  
```  
 
typedef typename Container::reference reference;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述对关联容器所控制的序列的元素的引用。  
  
### <a name="example"></a>示例  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [\< 迭代器>](../standard-library/iterator.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)

