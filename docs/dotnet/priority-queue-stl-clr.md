---
title: priority_queue (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: abfe2a740a51ffe8b2735942bc9387f0b13bb0d2
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079526"
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
此模板类描述控制不同的长度为排序的元素序列，具有有限访问权限的对象。 使用容器适配器`priority_queue`管理作为优先级队列的基础容器。  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。 同样，`GContainer`相同`Container`后者为 ref 类型，除非在这种情况下很`Container^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
### <a name="parameters"></a>参数  
 “值”  
 受控序列中的元素的类型。  
  
 容器  
 基础容器的类型。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  

## <a name="declarations"></a>声明  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[priority_queue::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|  
|[priority_queue::container_type (STL/CLR)](#container_type)|基础容器的类型。|  
|[priority_queue::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|  
|[priority_queue::generic_container (STL/CLR)](#generic_container)|容器适配器泛型接口的类型。|  
|[priority_queue::generic_value (STL/CLR)](#generic_value)|容器适配器的泛型接口的元素的类型。|  
|[priority_queue::reference (STL/CLR)](#reference)|元素的引用的类型。|  
|[priority_queue::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|  
|[priority_queue::value_compare (STL/CLR)](#value_compare)|用于两个元素的排序委托。|  
|[priority_queue::value_type (STL/CLR)](#value_type)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](#assign)|替换所有元素。|  
|[priority_queue::empty (STL/CLR)](#empty)|测试元素是否存在。|  
|[priority_queue::get_container (STL/CLR)](#get_container)|访问基础的容器。|  
|[priority_queue::pop (STL/CLR)](#pop)|移除 hghest 优先级的元素。|  
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|构造容器对象。|  
|[priority_queue::push (STL/CLR)](#push)|添加新元素。|  
|[priority_queue::size (STL/CLR)](#size)|对元素数进行计数。|  
|[priority_queue::top (STL/CLR)](#top)|访问优先级最高的元素。|  
|[priority_queue::to_array (STL/CLR)](#to_array)|受控的序列复制到新数组。|  
|[priority_queue::value_comp (STL/CLR)](#value_comp)|将复制两个元素的排序委托。|  
  
|属性|描述|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](#top_item)|访问优先级最高的元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](#op_as)|替换受控序列。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|IPriorityQueue\<值、 容器 >|维护泛型容器适配器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放它通过的基础的容器，类型的控制的序列的存储`Container`，存储`Value`元素和根据需要增长。 它会保留为堆，与的优先级最高的元素 （顶部元素） 轻松地访问和可移动排序的序列。 对象限制的访问权限将新元素推送和弹出只是优先级最高的元素，实现优先级队列。  
  
 该对象进行排序它通过调用类型的存储的委托对象控制的序列[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)。 在构造 priority_queue; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是比较`operator<(value_type, value_type)`。 通过调用成员函数来访问此存储的对象[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`。  
  
 此类委托对象必须对进行严格弱排序类型的值[priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)。 这意味着为任何两个键`X`和`Y`:  
  
 `value_comp()(X, Y)` 返回相同的布尔值导致每次调用。  
  
 如果`value_comp()(X, Y)`为 true，然后`value_comp()(Y, X)`必须是 false。  
  
 如果`value_comp()(X, Y)`为 true，然后`X`称为才能进行排序之前`Y`。  
  
 如果`!value_comp()(X, Y) && !value_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 任何元素`X`，之前`Y`受控序列中中,`key_comp()(Y, X)`为 false。 （对于默认委托对象，密钥永远不会减小值中。）  
  
 最高优先级元素，因此是任何其他元素之前不会对其进行排序的元素。  
  
 由于基础容器保留为堆排序的元素：  
  
 容器必须支持随机访问迭代器。  
  
 具有等效排序的元素可能按不同顺序弹出，不是它们已推送。 （排序不稳定。）  
  
 因此，适合基础容器包括[deque (STL/CLR)](../dotnet/deque-stl-clr.md)和[向量 (STL/CLR)](../dotnet/vector-stl-clr.md)。  
  
## <a name="members"></a>成员
  
## <a name="assign"></a> priority_queue::assign (STL/CLR)
替换所有元素。  
  
### <a name="syntax"></a>语法  
  
```  
void assign(priority_queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要插入的容器适配器。  
  
### <a name="remarks"></a>备注  
 成员函数将指派`right.get_container()`到基础的容器。 你可以使用它来更改队列的全部内容。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_assign.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mypriority_queue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
c a b  
```  

## <a name="const_reference"></a> priority_queue::const_reference (STL/CLR)
元素的常量引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的常量引用。  
  
### <a name="example"></a>示例  
  
```  
// cliext_priority_queue_const_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " c b a"   
    for (; !c1.empty(); c1.pop())   
        {   // get a const reference to an element   
        Mypriority_queue::const_reference cref = c1.top();   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="container_type"></a> priority_queue:: container_type (STL/CLR)
基础容器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Container value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Container` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_container_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mypriority_queue::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
```  

## <a name="difference_type"></a> priority_queue::difference_type (STL/CLR)
两个元素间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述可能负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_difference_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute negative difference   
    Mypriority_queue::difference_type diff = c1.size();   
    c1.push(L'd');   
    c1.push(L'e');   
    diff -= c1.size();   
    System::Console::WriteLine("pushing 2 = {0}", diff);   
  
// compute positive difference   
    diff = c1.size();   
    c1.pop();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("popping 3 = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
pushing 2 = -2  
popping 3 = 3  
```  

## <a name="empty"></a> priority_queue:: empty (STL/CLR)
测试元素是否存在。  
  
### <a name="syntax"></a>语法  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它相当于[priority_queue:: size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`。 用于测试是否 priority_queue 为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_empty.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.pop();   
    c1.pop();   
    c1.pop();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="generic_container"></a> priority_queue::generic_container (STL/CLR)
容器的泛型接口的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>  
    generic_container;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述此模板容器适配器类的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_generic_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
c a b  
d c b a  
e d b a c  
```  

## <a name="generic_value"></a> priority_queue::generic_value (STL/CLR)
使用容器的泛型接口具有的元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。 (`GValue`是`value_type`或`value_type^`如果`value_type`是 ref 类型。)  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_generic_value.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in priority order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Mypriority_queue::generic_value elem = gc1->top();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
c a b  
c b a  
```  

## <a name="get_container"></a> priority_queue::get_container (STL/CLR)
访问基础的容器。  
  
### <a name="syntax"></a>语法  
  
```  
container_type get_container();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回基础的容器。 你可以使用它来绕过容器包装施加的限制。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_get_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
```  

## <a name="op_as"></a> priority_queue::operator = (STL/CLR)
替换受控序列。  
  
### <a name="syntax"></a>语法  
  
```  
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的容器适配器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用它将受控序列替换为 `right` 中的受控序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_operator_as.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mypriority_queue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
c a b  
```  

## <a name="pop"></a> priority_queue:: pop (STL/CLR)
移除的最高 proirity 元素。  
  
### <a name="syntax"></a>语法  
  
```  
void pop();  
```  
  
### <a name="remarks"></a>备注  
 成员函数删除受控序列，必须为非空的优先级最高的元素。 你可以使用它将在后面的一个元素缩短队列。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_pop.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
b a  
```  

## <a name="priority_queue"></a> priority_queue:: priority_queue (STL/CLR)
构造容器适配器对象。  
  
### <a name="syntax"></a>语法  
  
```  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### <a name="parameters"></a>参数  
 上下文  
 用于复制的容器。  
  
 第一个  
 要插入的范围开始处。  
  
 last  
 要插入的范围的末尾。  
  
 pred  
 排序受控序列的谓词。  
  
 右  
 要插入的对象或范围。  
  
### <a name="remarks"></a>备注  
 构造函数：  
  
 `priority_queue();`  
  
 创建一个空的已包装的容器，使用默认的排序谓词。 用于指定空的初始受控的序列，使用默认的排序谓词。  
  
 构造函数：  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 创建一个已包装的容器，它是一份`right.get_container()`，与排序的谓词`right.value_comp()`。 用于指定是通过对队列对象控制的序列的副本的初始受控的序列`right`，具有相同排序的谓词。  
  
 构造函数：  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 创建一个已包装的容器，它是一份`right->get_container()`，与排序的谓词`right->value_comp()`。 用于指定是通过对队列对象控制的序列的副本的初始受控的序列`*right`，具有相同排序的谓词。  
  
 构造函数：  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 创建一个空的已包装的容器，与排序的谓词`pred`。 用于指定空的初始受控的序列，通过指定排序的谓词。  
  
 构造函数：  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 创建一个空的已包装的容器，与排序的谓词`pred`，然后将推送的所有元素`cont`使用它来通过指定的排序谓词指定的现有容器，从初始受控的序列。  
  
 构造函数：  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 与默认排序谓词，创建一个空的已包装的容器，然后将推送序列 [`first`， `last`)。 用于指定与指定的排序谓词的指定 eqeuence，从初始受控的序列。  
  
 构造函数：  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 创建一个空的已包装的容器，与排序的谓词`pred`，然后将推送序列 [`first`， `last`)。 用于指定与指定的排序谓词的指定 seqeuence，从初始受控的序列。  
  
 构造函数：  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 创建一个空的已包装的容器，与排序的谓词`pred`，然后将推送的所有元素`cont`plus 序列 [`first`， `last`)。 用于指定从现有容器和指定的 seqeuence，初始受控的序列与指定的排序谓词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 c a b  
size() = 0  
 a c b  
 a c b  
 c a b  
 a c b  
 a a b c c b  
 c a b  
 c a b  
 a c b  
```  
  
## <a name="push"></a> priority_queue:: push (STL/CLR)
添加新元素。  
  
### <a name="syntax"></a>语法  
  
```  
void push(value_type val);  
```  
  
### <a name="remarks"></a>备注  
 成员函数将插入具有值的元素`val`到受控的序列，并对受控的序列中维护的堆专业重新排序。 用于将另一个元素添加到队列。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
```  
  
## <a name="reference"></a> priority_queue::reference (STL/CLR)
元素的引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify top of priority_queue and redisplay   
    Mypriority_queue::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
x a b  
```  

## <a name="size"></a> priority_queue:: size (STL/CLR)
对元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定当前受控序列中的元素的数目。 如果你关注的只是序列是否具有非零大小，请参阅[priority_queue:: empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_size.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// pop an item and reinspect   
    c1.pop();   
    System::Console::WriteLine("size() = {0} after popping", c1.size());   
  
// add two elements and reinspect   
    c1.push(L'a');   
    c1.push(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
size() = 3 starting with 3  
size() = 2 after popping  
size() = 4 after adding 2  
```  

## <a name="size_type"></a> priority_queue:: size_type (STL/CLR)
两个元素之间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述非负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp 
// cliext_priority_queue_size_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mypriority_queue::size_type diff = c1.size();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("size difference = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
size difference = 2  
```  
  
## <a name="to_array"></a> priority_queue::to_array (STL/CLR)
受控的序列复制到新数组。  
  
### <a name="syntax"></a>语法  
  
```  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回包含受控的序列的数组。 用于获取受控序列中数组形式的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_to_array.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
d c b a  
c a b  
```  

## <a name="top"></a> priority_queue:: top (STL/CLR)
访问优先级最高的元素。  
  
### <a name="syntax"></a>语法  
  
```  
reference top();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的顶部 （最高优先级） 元素的引用。 用于访问优先级最高的元素中，当你知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_top.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  

## <a name="top_item"></a> priority_queue::top_item (STL/CLR)
访问优先级最高的元素。  
  
### <a name="syntax"></a>语法  
  
```  
property value_type back_item;  
```  
  
### <a name="remarks"></a>备注  
 属性访问受控序列，必须为非空的顶部 （最高优先级） 元素。 你可以使用它来读取或写入优先级最高的元素中，当你知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_top_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
top_item = c  
 x a b  
```  

## <a name="value_comp"></a> priority_queue::value_comp (STL/CLR)
将复制两个元素的排序委托。  
  
### <a name="syntax"></a>语法  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回使用受控的序列进行排序的排序委托。 用于比较两个值。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_value_comp.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    vcomp = c2.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="value_compare"></a> priority_queue::value_compare (STL/CLR)
两个值排序委托。  
  
### <a name="syntax"></a>语法  
  
```  
binary_delegate<value_type, value_type, int> value_compare;  
```  
  
### <a name="remarks"></a>备注  
 该类型是确定是否已在第二个之前排序的第一个参数的委托的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_value_compare.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    vcomp = c2.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="value_type"></a> priority_queue:: value_type (STL/CLR)
元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Value` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_priority_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mypriority_queue::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  