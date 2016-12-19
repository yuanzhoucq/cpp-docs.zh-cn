---
title: "queue 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.queue"
  - "std::queue"
  - "queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "queue 类"
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# queue 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种模板容器适配器类的功能的限制类型提供的一些基础容器，限制对封面和封底元素的访问。 可以在后面添加或从前面，移除元素，并且元素可以检查任何一端的队列。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Type, class Container = deque <Type>>  
class queue  
```  
  
#### <a name="parameters"></a>参数  
 *类型*  
 要存储在队列中的元素数据类型  
  
 `Container`  
 用来实现队列的基础容器的类型。  
  
## <a name="remarks"></a>备注  
 类的元素 **类型** 规定中的第一个模板参数的队列对象是使用同义词 [value_type](#queue__value_type) 必须与基础容器类中的元素的类型相匹配 **容器** 规定的第二个模板参数。  **类型** 必须是可赋值，，，因此很可能将复制该类型的对象并将值分配给该类型的变量。  
  
 用于队列的适当基础容器类包括 [e q u e](../standard-library/deque-class.md) 和 [列表](../standard-library/list-class.md), ，或任何其他支持的操作的序列容器 `front`, ，**回**, ，`push_back`, ，和 `pop_front`。 基础容器类封装在容器适配器中，容器适配器仅公开一组有限的序列容器成员函数为公共接口。  
  
 队列的对象相等性比较当且仅当类的元素 **类型** 有相等比较，并且小于-比可比较当且仅当类的元素 **类型** 小于-比可比较。  
  
 有三种类型的定义的 STL 容器适配器︰ 堆栈、 队列和 priority_queue。 每个限制某些基础容器类，用于提供对标准数据结构的精确地控制的接口的功能。  
  
-    [Stack 类](../standard-library/stack-class.md) 支持后进先出 (LIFO) 数据结构。 可以在脑海中将其类比为一摞盘子。 元素（盘子）只能从堆栈顶部（基容器末尾的最后一个元素）插入、检查或删除。 限制仅访问顶部元素是使用堆栈类的原因。  
  
-   Queue 类支持的先入先出 (FIFO) 数据结构。 可以在脑海中将其类比为排队等候银行柜员的人。 元素（人）可从行的后部添加，并且可以从行的前部删除。 行的前部和后部都可以插入。 限制访问仅有正面和背面的元素以这种方式是使用 queue 类的原因。  
  
-    [Priority_queue 类](../standard-library/priority-queue-class.md) 其元素进行排序，以便最大的元素始终位于顶部的位置。 它支持元素的插入以及顶部元素的检查和删除。 可以在脑海中将其类比为按年龄、身高或其他标准排队的人。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[队列](#queue__queue)|构造一个空的或者是基容器对象副本的 `queue`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#queue__container_type)|提供要由改写的基容器的类型 `queue`。|  
|[size_type](#queue__size_type)|可表示 `queue` 中元素数量的无符号整数类型。|  
|[value_type](#queue__value_type)|一种类型，它表示存储为 `queue` 中元素的对象的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[返回](#queue__back)|返回的引用，到最后一个和最后一次添加元素的背面 `queue`。|  
|[为空](#queue__empty)|测试 `queue` 是否为空。|  
|[前端](#queue__front)|返回在前面的第一个元素的引用 `queue`。|  
|[pop](#queue__pop)|从前端中移除一个元素 `queue`。|  
|[推送](#queue__push)|将元素添加到背面 `queue`。|  
|[大小](#queue__size)|返回 `queue` 中的元素数量。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 队列>  
  
 **命名空间：** std  
  
##  <a name="a-namequeuebacka-queueback"></a><a name="queue__back"></a>  queue:: back  
 返回的引用，到最后一个和最后一次添加队列的后面的元素。  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>返回值  
 队列的最后一个元素。 如果队列为空，则返回值是不确定。  
  
### <a name="remarks"></a>备注  
 如果返回值为 **回** 分配给 `const_reference`, ，不能修改队列对象。 如果返回值为 **回** 分配给 **引用**, ，可以修改对队列对象。  
  
 在使用 _SECURE_SCL 1 编译时，如果试图访问空队列中的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>示例  
  
```  
// queue_back.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 11 );  
  
   int& i = q1.back( );  
   const int& ii = q1.front( );  
  
   cout << "The integer at the back of queue q1 is " << i   
        << "." << endl;  
   cout << "The integer at the front of queue q1 is " << ii   
        << "." << endl;  
}  
```  
  
##  <a name="a-namequeuecontainertypea-queuecontainertype"></a><a name="queue__container_type"></a>  queue:: container_type  
 提供基本的容器为满足一种。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数 `Container` 的同义词。 两个 STL 序列容器类 — 列表类，而且默认 e q u e 类 — 满足用作队列对象的基础容器的要求。 此外可能使用满足要求的用户定义的类型。  
  
 有关详细信息 `Container`, ，请参阅备注部分的 [queue 类](../standard-library/queue-class.md) 主题。  
  
### <a name="example"></a>示例  
  请参阅示例 [队列](#queue__queue) 以举例说明如何声明和使用 `container_type`。  
  
##  <a name="a-namequeueemptya-queueempty"></a><a name="queue__empty"></a>  queue:: empty  
 测试队列是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 **true** 队列是否为空，则为 **false** 队列是否为非空。  
  
### <a name="example"></a>示例  
  
```  
// queue_empty.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
  
   // Declares queues with default deque base container  
   queue <int> q1, q2;  
  
   q1.push( 1 );  
  
   if ( q1.empty( ) )  
      cout << "The queue q1 is empty." << endl;  
   else  
      cout << "The queue q1 is not empty." << endl;  
  
   if ( q2.empty( ) )  
      cout << "The queue q2 is empty." << endl;  
   else  
      cout << "The queue q2 is not empty." << endl;  
}  
```  
  
```Output  
The queue q1 is not empty.  
The queue q2 is empty.  
```  
  
##  <a name="a-namequeuefronta-queuefront"></a><a name="queue__front"></a>  queue:: front  
 返回位于队列开头的第一个元素的引用。  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>返回值  
 队列的第一个元素。 如果队列为空，则返回值是不确定。  
  
### <a name="remarks"></a>备注  
 如果返回值为 `front` 分配给 `const_reference`, ，不能修改队列对象。 如果返回值为 `front` 分配给 **引用**, ，可以修改对队列对象。  
  
 成员函数将返回 **引用** 受控序列的第一个元素，它不能是空。  
  
 在使用 _SECURE_SCL 1 编译时，如果试图访问空队列中的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>示例  
  
```  
// queue_front.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   int& ii = q1.back( );  
   int& iii = q1.front( );  
  
   cout << "The integer at the back of queue q1 is " << ii   
        << "." << endl;  
   cout << "The integer at the front of queue q1 is " << iii   
        << "." << endl;  
}  
```  
  
##  <a name="a-namequeuepopa-queuepop"></a><a name="queue__pop"></a>  queue:: pop  
 从队列开头移除的元素。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>备注  
 队列不能是空要应用的成员函数。 队列的顶部是所占用的最新添加的元素的位置，并且是容器末尾处的最后一个元素。  
  
### <a name="example"></a>示例  
  
```  
// queue_pop.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, s2;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   i = q1.front( );  
   cout << "The element at the front of the queue is "  
        << i << "." << endl;  
  
   q1.pop( );  
  
   i = q1.size( );  
   cout << "After a pop the queue length is "   
        << i << "." << endl;  
  
   i = q1. front ( );  
   cout << "After a pop, the element at the front of the queue is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 3.  
The element at the front of the queue is 10.  
After a pop the queue length is 2.  
After a pop, the element at the front of the queue is 20.  
```  
  
##  <a name="a-namequeuepusha-queuepush"></a><a name="queue__push"></a>  queue:: push  
 将元素添加到队列后面。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>参数  
 `val`  
 添加到队列后面的元素。  
  
### <a name="remarks"></a>备注  
 队列的后面是占用的最新添加的元素的位置，并且是容器末尾处的最后一个元素。  
  
### <a name="example"></a>示例  
  
```  
// queue_push.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   i = q1.front( );  
   cout << "The element at the front of the queue is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 3.  
The element at the front of the queue is 10.  
```  
  
##  <a name="a-namequeuequeuea-queuequeue"></a><a name="queue__queue"></a>  queue:: queue  
 构造的队列为空的或者是基容器对象的副本。  
  
```  
queue();

explicit queue(const container_type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
  **Const** 构造的队列的要成为副本的容器。  
  
### <a name="remarks"></a>备注  
 队列的默认基容器是 e q u e。 您还可以指定列表作为基础容器，但不是能指定矢量，因为它缺少所需 `pop_front` 成员函数。  
  
### <a name="example"></a>示例  
  
```  
// queue_queue.cpp  
// compile with: /EHsc  
#include <queue>  
#include <vector>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queue with default deque base container  
   queue <char> q1;  
  
   // Explicitly declares a queue with deque base container  
   queue <char, deque<char> > q2;  
  
   // These lines don't cause an error, even though they  
   // declares a queue with a vector base container  
   queue <int, vector<int> > q3;  
   q3.push( 10 );  
   // but the following would cause an error because vector has   
   // no pop_front member function  
   // q3.pop( );  
  
   // Declares a queue with list base container  
   queue <int, list<int> > q4;  
  
   // The second member function copies elements from a container  
   list<int> li1;  
   li1.push_back( 1 );  
   li1.push_back( 2 );  
   queue <int, list<int> > q5( li1 );  
   cout << "The element at the front of queue q5 is "  
        << q5.front( ) << "." << endl;  
   cout << "The element at the back of queue q5 is "  
        << q5.back( ) << "." << endl;  
}  
```  
  
```Output  
The element at the front of queue q5 is 1.  
The element at the back of queue q5 is 2.  
```  
  
##  <a name="a-namequeuesizea-queuesize"></a><a name="queue__size"></a>  queue:: size  
 返回队列中的元素数。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 队列的当前长度。  
  
### <a name="example"></a>示例  
  
```  
// queue_size.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2;  
   queue <int>::size_type i;  
  
   q1.push( 1 );  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   q1.push( 2 );  
   i = q1.size( );  
   cout << "The queue length is now " << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 1.  
The queue length is now 2.  
```  
  
##  <a name="a-namequeuesizetypea-queuesizetype"></a><a name="queue__size_type"></a>  queue:: size_type  
 一种无符号的整数类型，可表示队列中的元素数量。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为同义词 `size_type` 基适配的容器由队列。  
  
### <a name="example"></a>示例  
  请参阅示例 [queue:: front](#queue__front) 以举例说明如何声明和使用 `size_type`。  
  
##  <a name="a-namequeuevaluetypea-queuevaluetype"></a><a name="queue__value_type"></a>  queue:: value_type  
 表示存储为队列中元素的对象的类型的类型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为同义词 `value_type` 基适配的容器由队列。  
  
### <a name="example"></a>示例  
  
```  
// queue_value_type.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
  
   // Declares queues with default deque base container  
   queue<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   queue<int> q1;  
   q1.push(AnInt);  
   cout << "The element at the front of the queue is "  
        << q1.front( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the front of the queue is 69.  
```  
  
## <a name="see-also"></a>另请参阅  
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)

