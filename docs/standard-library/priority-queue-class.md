---
title: "priority_queue 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
dev_langs: C++
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 705ffaa38222d83fe02e20f20c47ee4c06f22294
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="priorityqueue-class"></a>priority_queue 类
一个模板容器适配器类，它提供功能的限制，限制一些基本容器类型顶端元素的访问权限，并且该类通常为最大类或具有最高优先级。 可以将新元素添加到 priority_queue，并且可以检查或删除 priority_queue 的顶级元素。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>  
class priority_queue  
```  
  
#### <a name="parameters"></a>参数  
 *类型*  
 要存储在 priority_queue 中的元素数据类型。  
  
 `Container`  
 用来实现 priority_queue 的基础容器的类型。  
  
 *Compare*  
 一种提供函数对象的类型，该函数对象将两个元素值作为排序键进行比较，以确定其在 priority_queue 中的相对顺序。 此参数是可选自变量，默认值为二元谓词 **less***\<***typename** *Container***::value_type***>*。  
  
## <a name="remarks"></a>备注  
 队列对象的第一个模板参数中规定的 **Type** 类的元素与 [value_type](#value_type) 同义，并且必须与第二个模板参数规定的基础容器类 **Container** 中的元素类型相匹配。 **Type** 必须是可赋值的，这样才能复制该类型的对象并为该类型的变量赋值。  
  
 Priority_queue 通过调用存储的 **Traits** 类的函数对象，对它控制的序列进行排序。 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  
  
 适用于 Priority_queue 的基础容器类包括 [deque 类](../standard-library/deque-class.md)和默认的 [vector 类](../standard-library/vector-class.md)，或任何支持 `front`、`push_back`、`pop_back` 的操作和随机访问迭代器的其他序列容器。 基础容器类封装在容器适配器中，容器适配器仅公开一组有限的序列容器成员函数为公共接口。  
  
 将元素添加到和移出 `priority_queue` 均存在对数复杂性。 访问 `priority_queue` 中的元素存在恒定的复杂性。  
  
 C++ 标准库定义了三种类型的容器适配器：stack、queue 和 priority_queue。 每种适配器都限制了一些基础容器类的功能，以便对标准数据结构提供精确控制的接口。  
  
-   [堆栈类](../standard-library/stack-class.md)支持后进先出 (LIFO) 数据结构。 可以在脑海中将其类比为一摞盘子。 元素（盘子）只能从堆栈顶部（基容器末尾的最后一个元素）插入、检查或删除。 限制仅访问顶部元素是使用堆栈类的原因。  
  
-   [queue 类](../standard-library/queue-class.md)支持先进先出 (FIFO) 数据结构。 可以在脑海中将其类比为排队等候银行柜员的人。 元素（人）可从行的后部添加，并且可以从行的前部删除。 行的前部和后部都可以插入。 以这种方式限制仅访问前部和后部元素是使用队列类的原因。  
  
-   Priority_queue 类将对其元素进行排序，以便最大的元素始终位于顶部位置。 它支持元素的插入以及顶部元素的检查和删除。 可以在脑海中将其类比为按年龄、身高或其他标准排队的人。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[priority_queue](#priority_queue)|构造一个 `priority_queue`，它是空的，或者是一定范围内的基容器对象或其他 `priority_queue` 的副本。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#container_type)|一种类型，它提供将由 `priority_queue` 采用的基容器。|  
|[size_type](#size_type)|可表示 `priority_queue` 中元素数量的无符号整数类型。|  
|[value_type](#value_type)|一种类型，它表示存储为 `priority_queue` 中元素的对象的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[empty](#empty)|测试 `priority_queue` 是否为空。|  
|[pop](#pop)|从顶部位置移除 `priority_queue` 的最大元素。|  
|[push](#push)|基于来自 operator< 的元素的优先级将元素添加到优先级队列。|  
|[size](#size)|返回 `priority_queue` 中的元素数量。|  
|[top](#top)|返回对 `priority_queue` 顶部的最大元素的常量引用。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<queue>  
  
 **命名空间：** std  
  
##  <a name="container_type"></a>priority_queue::container_type  
 一种类型，它提供将调整的基容器。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数 `Container` 的同义词。 C++ 标准库序列容器类 `deque` 和默认类 `vector` 满足用作 priority_queue 对象的基容器的要求。 也可能使用满足要求的用户定义的类型。  
  
 有关 `Container` 的详细信息，请参阅 [priority_queue 类](../standard-library/priority-queue-class.md)主题的备注部分。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `container_type` 的示例，请参阅 [priority_queue](#priority_queue) 的示例。  
  
##  <a name="empty"></a>priority_queue::empty  
 测试 priority_queue 是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 priority_queue 为空，则为 **true**；如果 priority_queue 不为空，则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// pqueue_empty.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue <int> q1, s2;  
  
   q1.push( 1 );  
  
   if ( q1.empty( ) )  
      cout << "The priority_queue q1 is empty." << endl;  
   else  
      cout << "The priority_queue q1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The priority_queue s2 is empty." << endl;  
   else  
      cout << "The priority_queue s2 is not empty." << endl;  
}  
```  
  
```Output  
The priority_queue q1 is not empty.  
The priority_queue s2 is empty.  
```  
  
##  <a name="pop"></a>priority_queue::pop  
 从顶部位置移除 priority_queue 的最大元素。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>备注  
 Priority_queue 必须为非空以应用成员函数。 容器中的最大元素始终占据 priority_queue 的顶部。  
  
### <a name="example"></a>示例  
  
```cpp  
// pqueue_pop.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, s2;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   priority_queue <int>::size_type i, iii;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
  
   q1.pop( );  
  
   iii = q1.size( );  
   cout << "After a pop, the priority_queue length is "   
        << iii << "." << endl;  
  
   const int& iv = q1.top( );  
   cout << "After a pop, the element at the top of the "  
        << "priority_queue is " << iv << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
After a pop, the priority_queue length is 2.  
After a pop, the element at the top of the priority_queue is 20.  
```  
  
##  <a name="priority_queue"></a>priority_queue::priority_queue  
 构造一个空的 priority_queue，或是一定范围内基容器对象或其他 priority_queue 的副本。  
  
```  
priority_queue();

explicit priority_queue(const Traits&_comp);

priority_queue(const Traits&_comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp, const container_type& _Cont);
```  
  
### <a name="parameters"></a>参数  
 *_ comp*  
 **constTraits** 类型的比较函数用于对 priority_queue 中的元素进行排序，它默认为基容器的比较函数。  
  
 `_Cont`  
 要以构造的 priority_queue 为副本的基容器。  
  
 `right`  
 要以构造的集为副本的 priority_queue。  
  
 `first`  
 要复制的范围元素中的第一个元素的位置。  
  
 `last`  
 要复制的元素范围以外的第一个元素的位置。  
  
### <a name="remarks"></a>备注  
 前三个构造函数中的每个函数均指定空的初始 priority_queue，第二个函数还指定用于建立元素顺序的比较函数 (`comp`) 的类型，第三个函数明确指定要使用的 `container_type` (`_Cont`)。 关键字 **explicit** 取消某些种类的自动类型转换。  
  
 第四个构造函数指定 priority_queue `right` 副本。  
  
 最后三个构造函数复制范围 [* 首先上, 一次 *) 的某些容器和使用这些值来初始化不断增加的实现中指定的比较函数的类类型 priority_queue**特征**和`container_type`.  
  
### <a name="example"></a>示例  
  
```cpp  
// pqueue_ctor.cpp  
// compile with: /EHsc  
#include <queue>  
#include <vector>  
#include <deque>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function declares priority_queue  
   // with a default vector base container  
   priority_queue <int> q1;  
   cout << "q1 = ( ";  
   while ( !q1.empty( ) )  
   {  
      cout << q1.top( ) << " ";  
      q1.pop( );  
   }  
   cout << ")" << endl;  
  
   // Explicitly declares a priority_queue with nondefault  
   // deque base container  
   priority_queue <int, deque <int> > q2;  
   q2.push( 5 );  
   q2.push( 15 );  
   q2.push( 10 );  
   cout << "q2 = ( ";  
   while ( !q2.empty( ) )  
   {  
      cout << q2.top( ) << " ";  
      q2.pop( );  
   }  
   cout << ")" << endl;  
  
   // This method of printing out the elements of a priority_queue  
   // removes the elements from the priority queue, leaving it empty  
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;  
  
   // The third member function declares a priority_queue   
   // with a vector base container and specifies that the comparison   
   // function greater is to be used for ordering elements  
   priority_queue <int, vector<int>, greater<int> > q3;  
   q3.push( 2 );  
   q3.push( 1 );  
   q3.push( 3 );  
   cout << "q3 = ( ";  
   while ( !q3.empty( ) )  
   {  
      cout << q3.top( ) << " ";  
      q3.pop( );  
   }  
   cout << ")" << endl;  
  
   // The fourth member function declares a priority_queue and  
   // initializes it with elements copied from another container:  
   // first, inserting elements into q1, then copying q1 elements into q4  
   q1.push( 100 );  
   q1.push( 200 );  
   priority_queue <int> q4( q1 );  
   cout << "q4 = ( ";     
   while ( !q4.empty( ) )  
   {  
      cout << q4.top( ) << " ";  
      q4.pop( );  
   }  
   cout << ")" << endl;  
  
   // Creates an auxiliary vector object v5 to be used to initialize q5  
   vector <int> v5;  
   vector <int>::iterator v5_Iter;  
   v5.push_back( 10 );  
   v5.push_back( 30 );  
   v5.push_back( 20 );  
   cout << "v5 = ( " ;  
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )  
      cout << *v5_Iter << " ";  
   cout << ")" << endl;  
  
   // The fifth member function declares and  
   // initializes a priority_queue q5 by copying the  
   // range v5[ first,  last) from vector v5  
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q5 = ( ";  
   while ( !q5.empty( ) )  
   {  
      cout << q5.top( ) << " ";  
      q5.pop( );  
   }  
   cout << ")" << endl;  
  
   // The sixth member function declares a priority_queue q6  
   // with a comparison function greater and initializes q6  
   // by copying the range v5[ first,  last) from vector v5  
   priority_queue <int, vector<int>, greater<int> >   
      q6( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q6 = ( ";  
   while ( !q6.empty( ) )  
   {  
      cout << q6.top( ) << " ";  
      q6.pop( );  
   }  
   cout << ")" << endl;  
}  
```  
  
##  <a name="push"></a>priority_queue::push  
 基于来自 operator< 的元素的优先级将元素添加到优先级队列。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>参数  
 `val`  
 添加到 priority_queue 顶部的元素。  
  
### <a name="remarks"></a>备注  
 Priority_queue 的顶部是容器中的最大元素占用的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// pqueue_push.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="size"></a>priority_queue::size  
 返回 priority_queue 中的元素数目。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 Priority_queue 的当前长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// pqueue_size.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, q2;  
   priority_queue <int>::size_type i;  
  
   q1.push( 1 );  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   q1.push( 2 );  
   i = q1.size( );  
   cout << "The priority_queue length is now " << i << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 1.  
The priority_queue length is now 2.  
```  
  
##  <a name="size_type"></a>priority_queue::size_type  
 一种无符号整数类型，此类型可表示 priority_queue 中的元素数量。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是由 priority_queue 调整的基容器的 `size_type` 的同义词。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例。  
  
##  <a name="top"></a>priority_queue::top  
 返回对 priority_queue 顶部的最大元素的常量引用。  
  
```  
const_reference top() const;
```  
  
### <a name="return-value"></a>返回值  
 对由 priority_queue 的对象**特征**函数确定的最大元素的引用。  
  
### <a name="remarks"></a>备注  
 Priority_queue 必须为非空以应用成员函数。  
  
### <a name="example"></a>示例  
  
```cpp  
// pqueue_top.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="value_type"></a>priority_queue::value_type  
 一种类型，它表示存储为 priority_queue 中元素的对象的类型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是由 priority_queue 调整的基容器的 `value_type` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// pqueue_value_type.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   priority_queue<int> q1;  
   q1.push( AnInt );  
   cout << "The element at the top of the priority_queue is "  
        << q1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the priority_queue is 69.  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)

