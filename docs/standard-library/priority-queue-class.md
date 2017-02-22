---
title: "priority_queue 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.priority_queue"
  - "priority_queue"
  - "std::priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "priority_queue 类"
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# priority_queue 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种模板容器适配器类，它提供的功能限制对某些基础的容器类型，这始终是最大值或最高优先级的顶级元素的访问限制。 可以将新元素添加到 priority_queue 并且可以检查 priority_queue 的顶级元素，或将其删除。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>  
class priority_queue  
```  
  
#### <a name="parameters"></a>参数  
 *类型*  
 要存储在 priority_queue 中的元素数据类型。  
  
 `Container`  
 用于实现 priority_queue 基础容器的类型。  
  
 *比较*  
 提供可比较两个元素值作为排序键以确定其在 priority_queue 相对顺序的函数对象的类型。 此参数为可选和二元谓词 **较少***\<***typename** *容器***:: value_type***>* 是默认值。  
  
## <a name="remarks"></a>备注  
 类的元素 **类型** 规定中的第一个模板参数的队列对象是使用同义词 [value_type](#priority_queue__value_type) 必须与基础容器类中的元素的类型相匹配 **容器** 规定的第二个模板参数。  **类型** 必须是可赋值，，，因此很可能将复制该类型的对象并将值分配给该类型的变量。  
  
 Priority_queue 它通过调用的存储的函数对象的类控制的序列进行排序 **特征**。 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  
  
 Priority_queue 基础的适当容器类包括 [deque 类](../standard-library/deque-class.md) 和默认 [vector 类](../standard-library/vector-class.md) 或任何其他支持的操作的序列容器 `front`, ，`push_back`, ，和 `pop_back` 和随机访问迭代器。 基础容器类封装在容器适配器中，容器适配器仅公开一组有限的序列容器成员函数为公共接口。  
  
 将元素添加到和移除元素从 `priority_queue` 都具有对数复杂性。 访问中的元素 `priority_queue` 具有恒定的复杂性。  
  
 有三种类型的定义的 STL 容器适配器︰ 堆栈、 队列和 priority_queue。 每个限制某些基础容器类，用于提供对标准数据结构的精确地控制的接口的功能。  
  
-    [Stack 类](../standard-library/stack-class.md) 支持后进先出 (LIFO) 数据结构。 可以在脑海中将其类比为一摞盘子。 元素（盘子）只能从堆栈顶部（基容器末尾的最后一个元素）插入、检查或删除。 限制仅访问顶部元素是使用堆栈类的原因。  
  
-    [Queue 类](../standard-library/queue-class.md) 支持先入先出 (FIFO) 的数据结构。 可以在脑海中将其类比为排队等候银行柜员的人。 元素（人）可从行的后部添加，并且可以从行的前部删除。 行的前部和后部都可以插入。 限制访问仅有正面和背面的元素以这种方式是使用 queue 类的原因。  
  
-   Priority_queue 类其元素进行排序，以便最大的元素始终位于顶部的位置。 它支持元素的插入以及顶部元素的检查和删除。 可以在脑海中将其类比为按年龄、身高或其他标准排队的人。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[priority_queue](#priority_queue__priority_queue)|构造 `priority_queue` ，它是空，或者是一份范围基容器对象或其他 `priority_queue`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#priority_queue__container_type)|一种类型，它提供将由 `priority_queue` 采用的基容器。|  
|[size_type](#priority_queue__size_type)|可表示 `priority_queue` 中元素数量的无符号整数类型。|  
|[value_type](#priority_queue__value_type)|一种类型，它表示存储为 `priority_queue` 中元素的对象的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[为空](#priority_queue__empty)|测试 `priority_queue` 是否为空。|  
|[pop](#priority_queue__pop)|移除的最大元素 `priority_queue` 从顶部的位置。|  
|[推送](#priority_queue__push)|基于优先级的运算符中的元素的优先级队列中添加一个元素 <。|  
|[大小](#priority_queue__size)|返回 `priority_queue` 中的元素数量。|  
|[返回页首](#priority_queue__top)|返回的在顶部的最大元素的常量的引用 `priority_queue`。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 队列>  
  
 **命名空间：** std  
  
##  <a name="a-namepriorityqueuecontainertypea-priorityqueuecontainertype"></a><a name="priority_queue__container_type"></a>  priority_queue:: container_type  
 提供为满足的基础容器的类型。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数 `Container` 的同义词。 STL 序列容器类 deque 和默认类向量满足的要求，以用作 priority_queue 对象的基础容器。 此外可能使用满足要求的用户定义的类型。  
  
 有关详细信息 `Container`, ，请参阅备注部分的 [priority_queue 类](../standard-library/priority-queue-class.md) 主题。  
  
### <a name="example"></a>示例  
  请参阅示例 [priority_queue](#priority_queue__priority_queue) 以举例说明如何声明和使用 `container_type`。  
  
##  <a name="a-namepriorityqueueemptya-priorityqueueempty"></a><a name="priority_queue__empty"></a>  priority_queue:: empty  
 测试 priority_queue 是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 **true** priority_queue 是否为空; **false** 如果 priority_queue 为非空。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namepriorityqueuepopa-priorityqueuepop"></a><a name="priority_queue__pop"></a>  priority_queue:: pop  
 从顶部的位置中删除 priority_queue 的最大元素。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>备注  
 Priority_queue 必须为非空以应用成员函数。 在容器中的最大元素始终占用 priority_queue 的顶部。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namepriorityqueuepriorityqueuea-priorityqueuepriorityqueue"></a><a name="priority_queue__priority_queue"></a>  priority_queue:: priority_queue  
 构造空的或者是一份范围基容器对象或另一个 priority_queue priority_queue。  
  
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
 类型的比较函数 **constTraits** 使用的元素进行排序 priority_queue，默认值进行比较的基础容器函数中。  
  
 `_Cont`  
 基容器构造的 priority_queue 的要成为副本。  
  
 ` right`  
 Priority_queue 构造的集的要成为副本。  
  
 ` first`  
 要复制的范围元素中的第一个元素的位置。  
  
 ` last`  
 要复制的元素范围以外的第一个元素的位置。  
  
### <a name="remarks"></a>备注  
 每个前三个构造函数指定空的初始 priority_queue，第二个还指定类型的比较函数 ( ` comp`) 用于在建立的元素和第三个显式指定的顺序 `container_type` ( `_Cont`) 使用。 关键字 **显式** 取消某些种类的自动类型转换。  
  
 第四个构造函数指定一份 priority_queue ` right`。  
  
 最后三个构造函数复制范围 [ * first、 last*) 的某个容器，并使用值来初始化与提高在指定的类型的比较函数的类中实现 priority_queue **特征** 和 `container_type`。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namepriorityqueuepusha-priorityqueuepush"></a><a name="priority_queue__push"></a>  priority_queue:: push  
 基于优先级的运算符中的元素的优先级队列中添加一个元素 <。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>参数  
 ` val`  
 Priority_queue 页首添加的元素。  
  
### <a name="remarks"></a>备注  
 Priority_queue 的顶部是所占用的最大元素的容器中的位置。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namepriorityqueuesizea-priorityqueuesize"></a><a name="priority_queue__size"></a>  priority_queue:: size  
 Priority_queue 中返回元素的数。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 Priority_queue 当前长度。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namepriorityqueuesizetypea-priorityqueuesizetype"></a><a name="priority_queue__size_type"></a>  priority_queue:: size_type  
 无符号的整数类型，可以表示 priority_queue 中的元素数。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为同义词 `size_type` 由 priority_queue 改写，以便在基础容器。  
  
### <a name="example"></a>示例  
  请参阅示例 [大小](#priority_queue__size) 以举例说明如何声明和使用 `size_type`。  
  
##  <a name="a-namepriorityqueuetopa-priorityqueuetop"></a><a name="priority_queue__top"></a>  priority_queue:: top  
 返回对 priority_queue 顶部的最大元素的常量引用。  
  
```  
const_reference top() const;
```  
  
### <a name="return-value"></a>返回值  
 对由确定的最大元素的引用 **特征** 函数、 priority_queue 对象。  
  
### <a name="remarks"></a>备注  
 Priority_queue 必须为非空以应用成员函数。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namepriorityqueuevaluetypea-priorityqueuevaluetype"></a><a name="priority_queue__value_type"></a>  priority_queue:: value_type  
 一种表示存储为 priority_queue 中元素的对象的类型的类型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为同义词 `value_type` 由 priority_queue 改写，以便在基础容器。  
  
### <a name="example"></a>示例  
  
```  
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
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)

