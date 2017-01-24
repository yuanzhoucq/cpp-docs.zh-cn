---
title: "stack 类 | Microsoft Docs"
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
  - "std::stack"
  - "std.stack"
  - "stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "堆栈上，堆栈类"
  - "stack 类"
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# stack 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 用来实现堆栈的基础容器的类型。 默认值是类 `deque`*\< 类型>*。  
  
## <a name="remarks"></a>备注  
 类的元素 **类型** 中的第一个模板规定堆栈对象的参数的代名词 [value_type](#stack__value_type) 必须与基础容器类中的元素的类型相匹配 **容器** 规定的第二个模板参数。  **类型** 必须是可赋值，，，因此很可能将复制该类型的对象并将值分配给该类型的变量。  
  
 用于堆栈的适当基础容器类包括 [e q u e](../standard-library/deque-class.md), ，[list 类](../standard-library/list-class.md), ，和 [vector 类](../standard-library/vector-class.md), ，或任何其他支持的操作的序列容器 **回**, ，`push_back`, ，和 `pop_back`。 基础容器类封装在容器适配器中，容器适配器仅公开一组有限的序列容器成员函数为公共接口。  
  
 堆栈的对象相等性比较当且仅当类的元素 **类型** 可比较相等性，很少-比可比较当且仅当类的元素 **类型** 小于-比可比较。  
  
-   堆栈类支持后进先出 (LIFO) 数据结构。 可以在脑海中将其类比为一摞盘子。 元素（盘子）只能从堆栈顶部（基容器末尾的最后一个元素）插入、检查或删除。 限制仅访问顶部元素是使用堆栈类的原因。  
  
-    [Queue 类](../standard-library/queue-class.md) 支持先入先出 (FIFO) 的数据结构。 可以在脑海中将其类比为排队等候银行柜员的人。 元素（人）可从行的后部添加，并且可以从行的前部删除。 行的前部和后部都可以插入。 以这种方式限制仅访问前部和后部元素是使用队列类的原因。  
  
-    [Priority_queue 类](../standard-library/priority-queue-class.md) 其元素进行排序，以便最大的元素始终位于顶部的位置。 它支持元素的插入以及顶部元素的检查和删除。 可以在脑海中将其类比为按年龄、身高或其他标准排队的人。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[堆栈](#stack__stack)|构造一个空的或者是基容器对象副本的 `stack`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[container_type](#stack__container_type)|一种类型，它提供将由 `stack` 采用的基容器。|  
|[size_type](#stack__size_type)|可表示 `stack` 中元素数量的无符号整数类型。|  
|[value_type](#stack__value_type)|一种类型，它表示存储为 `stack` 中元素的对象的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[为空](#stack__empty)|测试 `stack` 是否为空。|  
|[pop](#stack__pop)|从 `stack` 的顶部删除元素。|  
|[推送](#stack__push)|将元素添加到 `stack` 顶部。|  
|[大小](#stack__size)|返回 `stack` 中的元素数量。|  
|[返回页首](#stack__top)|返回对 `stack` 顶部元素的引用。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 堆栈>  
  
 **命名空间：** std  
  
##  <a name="a-namestackcontainertypea-stackcontainertype"></a><a name="stack__container_type"></a>  stack:: container_type  
 提供基本的容器为满足一种。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数 `Container` 的同义词。 所有三个 STL 序列容器类 — vector 类、 list 类和默认类 deque — 满足的要求，用作堆栈对象的基础容器。 此外可能使用满足这些要求的用户定义的类型。  
  
 有关详细信息 `Container`, ，请参阅备注部分的 [stack 类](../standard-library/stack-class.md) 主题。  
  
### <a name="example"></a>示例  
  请参阅示例 [stack:: stack](#stack__stack) 以举例说明如何声明和使用 `container_type`。  
  
##  <a name="a-namestackemptya-stackempty"></a><a name="stack__empty"></a>  stack:: empty  
 如果某个叠是空的测试。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 **true** 如果堆栈为空，则为 **false** 如果堆栈为空。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namestackpopa-stackpop"></a><a name="stack__pop"></a>  stack:: pop  
 从堆栈的顶部移除的元素。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>备注  
 堆栈必须为非空要应用的成员函数。 堆栈的顶部是所占用的最新添加的元素的位置，并且是容器末尾处的最后一个元素。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namestackpusha-stackpush"></a><a name="stack__push"></a>  stack:: push  
 将元素添加到堆栈的顶端。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>参数  
 ` val`  
 添加到堆栈顶部的元素。  
  
### <a name="remarks"></a>备注  
 堆栈的顶部是所占用的最新添加的元素的位置，并且是容器末尾处的最后一个元素。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namestacksizea-stacksize"></a><a name="stack__size"></a>  stack:: size  
 返回对堆栈中的元素数。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 堆栈的当前长度。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namestacksizetypea-stacksizetype"></a><a name="stack__size_type"></a>  stack:: size_type  
 无符号的整数类型，可以表示在堆栈中的元素的数目。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为同义词 `size_type` 基适配的容器由堆栈。  
  
### <a name="example"></a>示例  
  请参阅示例 [大小](#stack__size) 以举例说明如何声明和使用 `size_type`。  
  
##  <a name="a-namestackstacka-stackstack"></a><a name="stack__stack"></a>  stack:: stack  
 构造空的或者是一份基本容器类的堆栈。  
  
```  
stack();

explicit stack(const container_type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 构造的堆栈的要成为副本的容器。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namestacktopa-stacktop"></a><a name="stack__top"></a>  stack:: top  
 返回对堆栈顶部的元素的引用。  
  
```  
reference top();

const_reference top() const;
```  
  
### <a name="return-value"></a>返回值  
 对堆栈顶部的容器中的最后一个元素的引用。  
  
### <a name="remarks"></a>备注  
 堆栈必须为非空要应用的成员函数。 堆栈的顶部是所占用的最新添加的元素的位置，并且是容器末尾处的最后一个元素。  
  
 如果返回值为 **顶部** 分配给 `const_reference`, ，堆栈对象不能修改。 如果返回值为 **顶部** 分配给 **引用**, ，可以修改堆栈对象。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namestackvaluetypea-stackvaluetype"></a><a name="stack__value_type"></a>  stack:: value_type  
 一种表示存储为元素在堆栈中的对象的类型的类型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>备注  
 类型为同义词 `value_type` 基适配的容器由堆栈。  
  
### <a name="example"></a>示例  
  
```  
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
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)

