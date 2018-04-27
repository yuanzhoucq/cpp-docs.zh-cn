---
title: queue 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
dev_langs:
- C++
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62d3a937d2141134255708d441b901c15a826f7a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="queue-class"></a>queue 类

一个模板容器适配器类，它提供功能的限制，限制对一些基本容器类型的前端和后端元素的访问权限。 可以在后端添加或从前端移除元素，并且可以在队列的任何一端检查元素。

## <a name="syntax"></a>语法

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>参数

*类型*要存储在队列中的元素数据类型

`Container` 用于实现队列的基础容器的类型。

## <a name="remarks"></a>备注

队列对象的第一个模板参数中规定的 **Type** 类的元素与 [value_type](#value_type) 同义，并且必须与第二个模板参数规定的基础容器类 **Container** 中的元素类型相匹配。 **Type** 必须是可赋值的，这样才能复制该类型的对象并为该类型的变量赋值。

适合队列的基础容器类包括 [deque](../standard-library/deque-class.md) 和 [list](../standard-library/list-class.md) 或者支持 `front`、**back**、`push_back` 和 `pop_front` 操作的任何其他序列容器。 基础容器类封装在容器适配器中，容器适配器仅公开一组有限的序列容器成员函数为公共接口。

当且仅当 **Type** 类的元素可进行相等比较时，queue 对象才可进行相等比较，当且仅当 **Type** 类的元素可进行小于比较时，queue 对象才可进行小于比较。

C++ 标准库定义了三种类型的容器适配器：stack、queue 和 priority_queue。 每种适配器都限制了一些基础容器类的功能，以便对标准数据结构提供精确控制的接口。

- [堆栈类](../standard-library/stack-class.md)支持后进先出 (LIFO) 数据结构。 可以在脑海中将其类比为一摞盘子。 元素（盘子）只能从堆栈顶部（基容器末尾的最后一个元素）插入、检查或删除。 限制仅访问顶部元素是使用堆栈类的原因。

- 队列类支持先进先出 (FIFO) 数据结构。 可以在脑海中将其类比为排队等候银行柜员的人。 元素（人）可从行的后部添加，并且可以从行的前部删除。 行的前部和后部都可以插入。 以这种方式限制仅访问前部和后部元素是使用队列类的原因。

- [priority_queue 类](../standard-library/priority-queue-class.md)将对其元素进行排序，以便最大的元素始终位于顶部位置。 它支持元素的插入以及顶部元素的检查和删除。 可以在脑海中将其类比为按年龄、身高或其他标准排队的人。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[queue](#queue)|构造一个空的或者是基容器对象副本的 `queue`。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[container_type](#container_type)|一种类型，它提供将由 `queue` 采用的基容器。|
|[size_type](#size_type)|可表示 `queue` 中元素数量的无符号整数类型。|
|[value_type](#value_type)|一种类型，它表示存储为 `queue` 中元素的对象的类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[back](#back)|返回对在 `queue` 后部最近添加的最后一个元素的引用。|
|[empty](#empty)|测试 `queue` 是否为空。|
|[front](#front)|返回对 `queue` 前部的第一个元素的引用。|
|[pop](#pop)|从 `queue` 前端移除一个元素。|
|[push](#push)|将元素添加到 `queue` 的后部。|
|[size](#size)|返回 `queue` 中的元素数量。|

## <a name="requirements"></a>要求

**标头：**\<queue>

**命名空间：** std

## <a name="back"></a>queue::back

返回对在队列后部最近添加的最后一个元素的引用。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>返回值

Queue 的最后一个元素。 如果队列为空，则未定义返回值。

### <a name="remarks"></a>备注

如果 **back** 的返回值赋给了 `const_reference`，则不能修改队列对象。 如果 **back** 的返回值赋给了 **reference**，则可以修改队列对象。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问空队列中的元素，则将发生运行时错误。  有关详细信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="container_type"></a>queue::container_type

一种类型，它提供将调整的基容器。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `Container` 的同义词。 两个 C++ 标准库序列容器类 - list 类和默认的 deque 类 - 满足用作队列对象的基容器的要求。 也可能使用满足要求的用户定义的类型。

有关 `Container` 的详细信息，请参阅 [queue 类](../standard-library/queue-class.md)主题的备注部分。

### <a name="example"></a>示例

有关如何声明和使用 `container_type` 的示例，请参阅 [queue](#queue) 的示例。

## <a name="empty"></a>queue::empty

测试队列是否为空。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果队列为空，则为 **true**；如果队列不为空，则为 **false**。

### <a name="example"></a>示例

```cpp
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

## <a name="front"></a>queue::front

返回对队列前部的第一个元素的引用。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>返回值

Queue 的第一个元素。 如果队列为空，则未定义返回值。

### <a name="remarks"></a>备注

如果将 `front` 的返回值分配给 `const_reference`，则无法修改队列对象。 如果 `front` 的返回值赋给了 **reference**，则可以修改队列对象。

成员函数返回对受控序列的第一个元素的**引用**，该元素必须为非空。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问空队列中的元素，则将发生运行时错误。  有关详细信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="pop"></a>queue::pop

从队列的前部移除元素。

```cpp
void pop();
```

### <a name="remarks"></a>备注

队列不能为空，以便应用成员函数。 队列的顶部是最近添加的元素所占据的位置，并且是容器末尾处的最后一个元素。

### <a name="example"></a>示例

```cpp
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

## <a name="push"></a>queue::push

将元素添加到队列的后部。

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>参数

`val` 添加到队列的背面的元素。

### <a name="remarks"></a>备注

队列的后部是最近添加的元素所占据的位置，并且是容器末尾处的最后一个元素。

### <a name="example"></a>示例

```cpp
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

## <a name="queue"></a>queue::queue

构造一个空的或者是基容器对象副本的队列。

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>参数

`right` **Const**构造的队列是为复制其中的容器。

### <a name="remarks"></a>备注

队列的默认基容器是 deque。 还可以指定列表作为基容器，但不能指定矢量，因为它缺少所需的 `pop_front` 成员函数。

### <a name="example"></a>示例

```cpp
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

## <a name="size"></a>queue::size

返回队列中的元素数目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

Queue 的当前长度。

### <a name="example"></a>示例

```cpp
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

## <a name="size_type"></a>queue::size_type

一种无符号整数类型，此类型可表示队列中的元素数量。

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>备注

该类型是由队列调整的基容器的 `size_type` 的同义词。

### <a name="example"></a>示例

有关如何声明和使用 `size_type` 的示例，请参阅 [queue::front](#front) 的示例。

## <a name="value_type"></a>queue::value_type

一种类型，它表示存储为队列中元素的对象的类型。

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>备注

该类型是由队列调整的基容器的 `value_type` 的同义词。

### <a name="example"></a>示例

```cpp
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

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
