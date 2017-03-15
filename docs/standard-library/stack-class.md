---
title: "stack 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::stack
- std.stack
- stack
dev_langs:
- C++
helpviewer_keywords:
- stack, stack class
- stack class
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
caps.latest.revision: 22
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
ms.openlocfilehash: 81467a48b08fab628da94b217c2925010f3118fe
ms.lasthandoff: 02/24/2017

---
# <a name="stack-class"></a>stack 类
一种模板容器适配器类，它提供了功能的限制，限制对最近添加到某些基础容器类型的元素的访问。 当清楚仅在容器上执行堆栈操作很重要时，会使用堆栈类。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Type, class Container= deque <Type>>  
class stack  
```  
  
#### <a name="parameters"></a>参数  
 *类型*  
 要存储在堆栈中的元素数据类型。  
  
 `Container`  
 用来实现堆栈的基础容器的类型。 默认值为 `deque`*\<Type>* 类。  
  
## <a name="remarks"></a>备注  
 堆栈对象的第一个模板参数中规定的 **Type** 类的元素与 [value_type](#stack__value_type) 同义，并且必须与第二个模板参数规定的基础容器类 **Container** 中的元素类型相匹配。 **Type** 必须是可赋值的，这样才能复制该类型的对象并为该类型的变量赋值。  
  
 适合堆栈的基础容器类包括 [deque](../standard-library/deque-class.md)、[list class](../standard-library/list-class.md) 和 [vector class](../standard-library/vector-class.md) 或者支持 **back** 操作（`push_back` 和 `pop_back`）的任何其他序列容器。 基础容器类封装在容器适配器中，容器适配器仅公开一组有限的序列容器成员函数为公共接口。  
  
 当且仅当 **Type** 类的元素可进行相等比较时，堆栈对象才可进行相等比较，当且仅当 **Type** 类的元素可进行小于比较时，堆栈对象才可进行小于比较。  
  
-   堆栈类支持后进先出 (LIFO) 数据结构。 可以在脑海中将其类比为一摞盘子。 元素（盘子）只能从堆栈顶部（基容器末尾的最后一个元素）插入、检查或删除。 限制仅访问顶部元素是使用堆栈类的原因。  
  
-   [queue class](../standard-library/queue-class.md) 支持先进先出 (FIFO) 数据结构。 可以在脑海中将其类比为排队等候银行柜员的人。 元素（人）可从行的后部添加，并且可以从行的前部删除。 行的前部和后部都可以插入。 以这种方式限制仅访问前部和后部元素是使用队列类的原因。  
  
-   [priority_queue 类](../standard-library/priority-queue-class.md)将对其元素进行排序，以便最大的元素始终位于顶部位置。 它支持元素的插入以及顶部元素的检查和删除。 可以在脑海中将其类比为按年龄、身高或其他标准排队的人。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[stack](#stack__stack)|构造一个空的或者是基容器对象副本的 `stack`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#stack__container_type)|一种类型，它提供将由 `stack` 采用的基容器。|  
|[size_type](#stack__size_type)|可表示 `stack` 中元素数量的无符号整数类型。|  
|[value_type](#stack__value_type)|一种类型，它表示存储为 `stack` 中元素的对象的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[empty](#stack__empty)|测试 `stack` 是否为空。|  
|[pop](#stack__pop)|从 `stack` 的顶部删除元素。|  
|[push](#stack__push)|将元素添加到 `stack` 顶部。|  
|[size](#stack__size)|返回 `stack` 中的元素数量。|  
|[top](#stack__top)|返回对 `stack` 顶部元素的引用。|  
  
## <a name="requirements"></a>要求  
 **标头：** \<堆栈>  
  
 **命名空间：** std  
  
##  <a name="a-namestackcontainertypea--stackcontainertype"></a><a name="stack__container_type"></a>  stack::container_type  
 一种类型，它提供将调整的基容器。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Container` 的同义词。 三个 C++ 标准库序列容器类 - 矢量类、列表类和默认的类 deque - 满足用作堆栈对象的基容器的要求。 也可能使用满足要求的用户定义的类型。  
  
 有关 `Container` 的详细信息，请参阅 [stack 类](../standard-library/stack-class.md)主题的“备注”部分。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `container_type` 的示例，请参阅 [stack::stack](#stack__stack) 的示例。  
  
##  <a name="a-namestackemptya--stackempty"></a><a name="stack__empty"></a>  stack::empty  
 测试堆栈是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果堆栈为空，则为 **true**；如果堆栈不为空，则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// stack_empty.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack <int> s1, s2;  
  
   s1.push( 1 );  
  
   if ( s1.empty( ) )  
      cout << "The stack s1 is empty." << endl;  
   else  
      cout << "The stack s1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The stack s2 is empty." << endl;  
   else  
      cout << "The stack s2 is not empty." << endl;  
}  
```  
  
```Output  
The stack s1 is not empty.  
The stack s2 is empty.  
```  
  
##  <a name="a-namestackpopa--stackpop"></a><a name="stack__pop"></a>  stack::pop  
 从堆栈的顶部删除元素。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>备注  
 堆栈必须为非空才能应用成员函数。 堆栈顶部是最近添加的元素所占据的位置，并且是容器末尾处的最后一个元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// stack_pop.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
  
   s1.pop( );  
  
   i = s1.size( );  
   cout << "After a pop, the stack length is "   
        << i << "." << endl;  
  
   i = s1.top( );  
   cout << "After a pop, the element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
After a pop, the stack length is 2.  
After a pop, the element at the top of the stack is 20.  
```  
  
##  <a name="a-namestackpusha--stackpush"></a><a name="stack__push"></a>  stack::push  
 在堆栈的末尾处添加一个元素。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>参数  
 ` val`  
 添加到堆栈顶部的元素。  
  
### <a name="remarks"></a>备注  
 堆栈顶部是最近添加的元素所占据的位置，并且是容器末尾处的最后一个元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// stack_push.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
```  
  
##  <a name="a-namestacksizea--stacksize"></a><a name="stack__size"></a>  stack::size  
 返回堆栈中元素数。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 堆栈的当前长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// stack_size.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
   stack <int>::size_type i;  
  
   s1.push( 1 );  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   s1.push( 2 );  
   i = s1.size( );  
   cout << "The stack length is now " << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 1.  
The stack length is now 2.  
```  
  
##  <a name="a-namestacksizetypea--stacksizetype"></a><a name="stack__size_type"></a>  stack::size_type  
 一种无符号整数类型，此类型可表示堆栈中的元素数。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为堆栈采用的基容器的 `size_type` 的同义词。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `size_type` 的示例，请参阅 [size](#stack__size) 的示例。  
  
##  <a name="a-namestackstacka--stackstack"></a><a name="stack__stack"></a>  stack::stack  
 构造一个空的堆栈或者是基容器类副本的堆栈。  
  
```  
stack();

explicit stack(const container_type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 所构造堆栈要成为其副本的矢量。  
  
### <a name="example"></a>示例  
  
```cpp  
// stack_stack.cpp  
// compile with: /EHsc  
#include <stack>  
#include <vector>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares stack with default deque base container  
   stack <char> dsc1;  
  
   //Explicitly declares a stack with deque base container  
   stack <char, deque<char> > dsc2;  
  
   // Declares a stack with vector base containers  
   stack <int, vector<int> > vsi1;  
  
   // Declares a stack with list base container  
   stack <int, list<int> > lsi;  
  
   // The second member function copies elements from a container  
   vector<int> v1;  
   v1.push_back( 1 );  
   stack <int, vector<int> > vsi2( v1 );  
   cout << "The element at the top of stack vsi2 is "  
        << vsi2.top( ) << "." << endl;  
}  
```  
  
```Output  
The element at the top of stack vsi2 is 1.  
```  
  
##  <a name="a-namestacktopa--stacktop"></a><a name="stack__top"></a>  stack::top  
 返回对堆栈顶部元素的引用。  
  
```  
reference top();

const_reference top() const;
```  
  
### <a name="return-value"></a>返回值  
 对堆栈顶部容器中的最后一个元素的引用。  
  
### <a name="remarks"></a>备注  
 堆栈必须为非空才能应用成员函数。 堆栈顶部是最近添加的元素所占据的位置，并且是容器末尾处的最后一个元素。  
  
 如果 **top** 的返回值赋给了 `const_reference`，则不能修改堆栈对象。 如果 **top** 的返回值赋给了 **reference**，则不能修改堆栈对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// stack_top.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 1 );  
   s1.push( 2 );  
  
   int& i = s1.top( );  
   const int& ii = s1.top( );  
  
   cout << "The top integer of the stack s1 is "  
        << i << "." << endl;  
   i--;  
   cout << "The next integer down is "<< ii << "." << endl;  
}  
```  
  
```Output  
The top integer of the stack s1 is 2.  
The next integer down is 1.  
```  
  
##  <a name="a-namestackvaluetypea--stackvaluetype"></a><a name="stack__value_type"></a>  stack::value_type  
 一种类型，它表示存储为堆栈中元素的对象类型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为堆栈采用的基容器的 `value_type` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// stack_value_type.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   stack<int> s1;  
   s1.push( AnInt );  
   cout << "The element at the top of the stack is "  
        << s1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the stack is 69.  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


