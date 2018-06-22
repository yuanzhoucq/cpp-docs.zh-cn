---
title: 队列 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::queue::assign
- cliext::queue::back
- cliext::queue::back_item
- cliext::queue::const_reference
- cliext::queue::container_type
- cliext::queue::difference_type
- cliext::queue::empty
- cliext::queue::front
- cliext::queue::front_item
- cliext::queue::generic_container
- cliext::queue::generic_value
- cliext::queue::get_container
- cliext::queue::operator=
- cliext::queue::pop
- cliext::queue::push
- cliext::queue::queue
- cliext::queue::reference
- cliext::queue::size
- cliext::queue::size_type
- cliext::queue::to_array
- cliext::queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- push member [STL/CLR]
- queue member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b4d591d2abd7613777dec6ae668badd84fe31d0c
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305541"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
此模板类描述控制元素的长短序列，可先入先出访问的对象。 使用容器适配器`queue`来管理为队列的基础容器。  
  
 在下面，描述`GValue`相同`Value`后者为 ref 类型，除非在这种情况下很`Value^`。 同样，`GContainer`相同`Container`后者为 ref 类型，除非在这种情况下很`Container^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 “值”  
 受控序列中的元素的类型。  
  
 容器  
 基础容器的类型。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  

## <a name="declarations"></a>声明  
  
|类型定义|Description|  
|---------------------|-----------------|  
|[queue::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|  
|[queue::container_type (STL/CLR)](#container_type)|基础容器的类型。|  
|[queue::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|  
|[queue::generic_container (STL/CLR)](#generic_container)|容器适配器泛型接口的类型。|  
|[queue::generic_value (STL/CLR)](#generic_value)|容器适配器的泛型接口的元素的类型。|  
|[queue::reference (STL/CLR)](#reference)|元素的引用的类型。|  
|[queue::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|  
|[queue::value_type (STL/CLR)](#value_type)|元素的类型。|  
  
|成员函数|Description|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](#assign)|替换所有元素。|  
|[queue::back (STL/CLR)](#back)|访问最后一个元素。|  
|[queue::empty (STL/CLR)](#empty)|测试元素是否存在。|  
|[queue::front (STL/CLR)](#front)|访问第一个元素。|  
|[queue::get_container (STL/CLR)](#get_container)|访问基础的容器。|  
|[queue::pop (STL/CLR)](#pop)|移除的第一个元素。|  
|[queue::push (STL/CLR)](#push)|添加新的最后一个元素。|  
|[queue::queue (STL/CLR)](#queue)|构造容器对象。|  
|[queue::size (STL/CLR)](#size)|对元素数进行计数。|  
|[queue::to_array (STL/CLR)](#to_array)|受控的序列复制到新数组。|  
  
|属性|Description|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](#back_item)|访问最后一个元素。|  
|[queue::front_item (STL/CLR)](#front_item)|访问第一个元素。|  
  
|运算符|Description|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](#op_as)|替换受控序列。|  
|[operator!= (queue) (STL/CLR)](#op_neq)|确定如果`queue`对象是否不等于另一个`queue`对象。|  
|[operator< (queue) (STL/CLR)](#op_lt)|确定如果`queue`对象是否小于另一个`queue`对象。|  
|[operator<= (queue) (STL/CLR)](#op_lteq)|确定如果`queue`对象是否小于或等于另一个`queue`对象。|  
|[operator== (queue) (STL/CLR)](#op_eq)|确定如果`queue`对象是否等于另一个`queue`对象。|  
|[operator> (queue) (STL/CLR)](#op_gt)|确定如果`queue`对象是否大于另一个`queue`对象。|  
|[operator>= (queue) (STL/CLR)](#op_gteq)|确定如果`queue`对象是否大于或等于另一个`queue`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|IQueue\<值、 容器 >|维护泛型容器适配器。|  
  
### <a name="remarks"></a>备注  
 对象分配和释放它通过的基础的容器，类型的控制的序列的存储`Container`，存储`Value`元素和根据需要增长。 对象限制的访问权限只将推送的第一个元素并弹出的最后一个元素，实现第一个在先进先出队列 （也称为 FIFO 队列或只需队列）。  
  
## <a name="members"></a>成员

## <a name="assign"></a> queue::assign (STL/CLR)
替换所有元素。  
  
### <a name="syntax"></a>语法  
  
```  
void assign(queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要插入的容器适配器。  
  
### <a name="remarks"></a>备注  
 成员函数将指派`right.get_container()`到基础的容器。 你可以使用它来更改队列的全部内容。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_assign.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Myqueue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="back"></a> queue:: back (STL/CLR)
访问最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```  
reference back();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的最后一个元素的引用。 用于访问最后一个元素，当你知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_back.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  

## <a name="back_item"></a> queue::back_item (STL/CLR)
访问最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```  
property value_type back_item;  
```  
  
### <a name="remarks"></a>备注  
 属性访问受控序列，必须为非空的最后一个元素。 你可以使用它来读取或写入的最后一个元素，当你知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_back_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  

## <a name="const_reference"></a> queue::const_reference (STL/CLR)
元素的常量引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的常量引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_const_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for (; !c1.empty(); c1.pop())   
        {   // get a const reference to an element   
        Myqueue::const_reference cref = c1.front();   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="container_type"></a> queue:: container_type (STL/CLR)
基础容器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Container value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Container` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_container_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Myqueue::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="difference_type"></a> queue::difference_type (STL/CLR)
两个元素间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述可能负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_difference_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute negative difference   
    Myqueue::difference_type diff = c1.size();   
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
 a b c  
pushing 2 = -2  
popping 3 = 3  
```  

## <a name="empty"></a> queue:: empty (STL/CLR)
测试元素是否存在。  
  
### <a name="syntax"></a>语法  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它相当于[queue:: size (STL/CLR)](../dotnet/queue-size-stl-clr.md)`() == 0`。 用于测试是否队列为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_empty.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="front"></a> queue:: front (STL/CLR)
访问第一个元素。  
  
### <a name="syntax"></a>语法  
  
```  
reference front();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的第一个元素的引用。 用于访问第一个元素，当你知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_front.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  

## <a name="front_item"></a> queue::front_item (STL/CLR)
访问第一个元素。  
  
### <a name="syntax"></a>语法  
  
```  
property value_type front_item;  
```  
  
### <a name="remarks"></a>备注  
 属性访问必须为非空的受控序列的第一个元素。 你可以使用它来读取或写入的第一个元素，当你知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_front_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter last item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  

## <a name="generic_container"></a> queue::generic_container (STL/CLR)
容器适配器泛型接口的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Microsoft::VisualC::StlClr::IQueue<Value>  
    generic_container;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述此模板容器适配器类的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_generic_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myqueue::generic_container^ gc1 = %c1;   
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
a b c  
a b c  
a b c d  
a b c d e  
```  

## <a name="generic_value"></a> queue::generic_value (STL/CLR)
使用容器的泛型接口具有的元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。 (`GValue`是`value_type`或`value_type^`如果`value_type`是 ref 类型。)  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_generic_value.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Myqueue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Myqueue::generic_value elem = gc1->front();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  

## <a name="get_container"></a> queue::get_container (STL/CLR)
访问基础的容器。  
  
### <a name="syntax"></a>语法  
  
```  
container_type^ get_container();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回基础的容器。 你可以使用它来绕过容器包装施加的限制。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_get_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c  
```  

## <a name="op_as"></a> queue::operator = (STL/CLR)
替换受控序列。  
  
### <a name="syntax"></a>语法  
  
```  
queue <Value, Container>% operator=(queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的容器适配器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用它将受控序列替换为 `right` 中的受控序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_operator_as.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="pop"></a> queue:: pop (STL/CLR)
移除的最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```  
void pop();  
```  
  
### <a name="remarks"></a>备注  
 成员函数删除受控序列，必须为非空的最后一个元素。 你可以使用它将在后面的一个元素缩短队列。  
  
### <a name="example"></a>示例  
  
```  
// cliext_queue_pop.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c  
b c  
```  

## <a name="push"></a> queue:: push (STL/CLR)
添加新的最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```  
void push(value_type val);  
```  
  
### <a name="remarks"></a>备注  
 成员函数添加一个带有值元素`val`队列的末尾。 用于将元素追加到队列。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c  
```  

## <a name="queue"></a> queue:: queue (STL/CLR)
构造容器适配器对象。  
  
### <a name="syntax"></a>语法  
  
```  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的对象。  
  
 包装  
 要使用的已包装的容器。  
  
### <a name="remarks"></a>备注  
 构造函数：  
  
 `queue();`  
  
 创建一个空的已包装的容器。 用于指定空的初始受控的序列。  
  
 构造函数：  
  
 `queue(queue<Value, Container>% right);`  
  
 创建一个已包装的容器，它是一份`right.get_container()`。 用于指定是通过对队列对象控制的序列的副本的初始受控的序列`right`。  
  
 构造函数：  
  
 `queue(queue<Value, Container>^ right);`  
  
 创建一个已包装的容器，它是一份`right->get_container()`。 用于指定是通过对队列对象控制的序列的副本的初始受控的序列`*right`。  
  
 构造函数：  
  
 `explicit queue(container_type wrapped);`  
  
 使用现有容器`wrapped`作为已包装的容器。 你可以使用它来构造一个队列从现有容器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/list>   
  
typedef cliext::queue<wchar_t> Myqueue;   
typedef cliext::list<wchar_t> Mylist;   
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;   
int main()   
    {   
// construct an empty container   
    Myqueue c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Mylist v2(5, L'x');   
    Myqueue_list c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myqueue_list c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Myqueue_list c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  

## <a name="reference"></a> queue::reference (STL/CLR)
元素的引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify back of queue and redisplay   
    Myqueue::reference ref = c1.back();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b x  
```  

## <a name="size"></a> queue:: size (STL/CLR)
对元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定当前受控序列中的元素的数目。 如果你关注的只是序列是否具有非零大小，请参阅[queue:: empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_size.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
 a b c  
size() = 3 starting with 3  
size() = 2 after popping  
size() = 4 after adding 2  
```  

## <a name="size_type"></a> queue:: size_type (STL/CLR)
两个元素之间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述非负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_size_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myqueue::size_type diff = c1.size();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("size difference = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size difference = 2  
```  

## <a name="to_array"></a> queue::to_array (STL/CLR)
受控的序列复制到新数组。  
  
### <a name="syntax"></a>语法  
  
```  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回包含受控的序列的数组。 用于获取受控序列中数组形式的副本。  
  
### <a name="example"></a>示例  
  
```  
// cliext_queue_to_array.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
a b c d  
a b c  
```  

## <a name="value_type"></a> queue:: value_type (STL/CLR)
元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Value` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Myqueue::value_type val = c1.front();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="op_neq"></a> 运算符 ！ = （队列） (STL/CLR)
队列不等于比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator!=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(left == right)`。 用于测试是否`left`未进行排序相同`right`两个队列时由元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_operator_ne.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> 运算符&lt;（队列） (STL/CLR)
队列小于比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回 true 当对于最低的位置`i`为其`!(right[i] < left[i])`很还 true， `left[i] < right[i]`。 否则，它将返回`left->` [queue:: size (STL/CLR)](../dotnet/queue-size-stl-clr.md) `() <` `right->size()`用于测试是否`left`进行排序之前`right`两个队列时由元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_operator_lt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> 运算符&lt;= （队列） (STL/CLR)
队列小于或等于比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(right < left)`。 用于测试是否`left`未进行排序之后`right`两个队列时由元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_operator_le.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> 运算符 = = （队列） (STL/CLR)
队列相等比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator==(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数，则返回 true，才由控制序列`left`和`right`具有相同的长度和每个位置`i`， `left[i] ==` `right[i]`。 用于测试是否`left`进行排序相同`right`两个队列时由元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_operator_eq.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> 运算符&gt;（队列） (STL/CLR)
队列大于以下值比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator>(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`right` `<` `left`。 用于测试是否`left`进行排序之后`right`两个队列时由元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_operator_gt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> 运算符&gt;= （队列） (STL/CLR)
队列大于以下值或相等比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator>=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(left < right)`。 用于测试是否`left`未进行排序之前`right`两个队列时由元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_queue_operator_ge.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  