---
title: queue (STL/CLR)
ms.date: 11/04/2016
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
ms.openlocfilehash: 2cf0467c2b4799c2009f866b7aa22be5e421f762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384696"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)

此模板类描述一个对象，用于控制变长序列的元素具有的先进先出访问。 使用中的容器适配器`queue`管理视为一个队列的基础容器。

在下面的说明`GValue`等同于*值*后者是 ref 类型，除非在此情况下是`Value^`。 同样，`GContainer`等同于*容器*后者是 ref 类型，除非在此情况下是`Container^`。

## <a name="syntax"></a>语法

```cpp
template<typename Value,
    typename Container>
    ref class queue
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>参数

*值*<br/>
受控序列中的元素的类型。

*Container*<br/>
基础容器的类型。

## <a name="requirements"></a>要求

**标头：** \<cliext/队列 >

**Namespace:** cliext

## <a name="declarations"></a>声明

|类型定义|描述|
|---------------------|-----------------|
|[queue::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|
|[queue::container_type (STL/CLR)](#container_type)|基础容器的类型。|
|[queue::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|
|[queue::generic_container (STL/CLR)](#generic_container)|容器适配器泛型接口的类型。|
|[queue::generic_value (STL/CLR)](#generic_value)|容器适配器的泛型接口的元素的类型。|
|[queue::reference (STL/CLR)](#reference)|元素的引用的类型。|
|[queue::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|
|[queue::value_type (STL/CLR)](#value_type)|元素的类型。|

|成员函数|描述|
|---------------------|-----------------|
|[queue::assign (STL/CLR)](#assign)|替换所有元素。|
|[queue::back (STL/CLR)](#back)|访问最后一个元素。|
|[queue::empty (STL/CLR)](#empty)|测试元素是否存在。|
|[queue::front (STL/CLR)](#front)|访问第一个元素。|
|[queue::get_container (STL/CLR)](#get_container)|访问基础容器。|
|[queue::pop (STL/CLR)](#pop)|删除第一个元素。|
|[queue::push (STL/CLR)](#push)|添加一个新的最后一个元素。|
|[queue::queue (STL/CLR)](#queue)|构造容器对象。|
|[queue::size (STL/CLR)](#size)|对元素数进行计数。|
|[queue::to_array (STL/CLR)](#to_array)|将受控的序列复制到新数组。|

|属性|描述|
|--------------|-----------------|
|[queue::back_item (STL/CLR)](#back_item)|访问最后一个元素。|
|[queue::front_item (STL/CLR)](#front_item)|访问第一个元素。|

|运算符|描述|
|--------------|-----------------|
|[queue::operator= (STL/CLR)](#op_as)|替换受控序列。|
|[operator!= (queue) (STL/CLR)](#op_neq)|确定是否`queue`对象不等于另一个`queue`对象。|
|[operator< (queue) (STL/CLR)](#op_lt)|确定是否`queue`对象是否小于另一个`queue`对象。|
|[operator<= (queue) (STL/CLR)](#op_lteq)|确定是否`queue`对象是否小于或等于另一个`queue`对象。|
|[operator== (queue) (STL/CLR)](#op_eq)|确定是否`queue`对象是否等于另一个`queue`对象。|
|[operator> (queue) (STL/CLR)](#op_gt)|确定是否`queue`对象是否大于另一个`queue`对象。|
|[operator>= (queue) (STL/CLR)](#op_gteq)|确定是否`queue`对象是否大于或等于另一个`queue`对象。|

## <a name="interfaces"></a>接口

|接口|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|重复的对象。|
|IQueue\<值中，容器 >|维护泛型容器适配器。|

## <a name="remarks"></a>备注

该对象分配并释放存储类型的基础容器，通过它控制的序列`Container`，用于存储`Value`元素并根据需要增长。 该对象将访问限制为只将推送的第一个元素并弹出的最后一个元素，实现的先进先出队列 （也称为 FIFO 队列或只需一个队列）。

## <a name="members"></a>成员

## <a name="assign"></a> queue::assign (STL/CLR)

替换所有元素。

### <a name="syntax"></a>语法

```cpp
void assign(queue<Value, Container>% right);
```

#### <a name="parameters"></a>参数

*right*<br/>
要插入的容器适配器。

### <a name="remarks"></a>备注

该成员函数分配`right.get_container()`到基础容器。 您可以使用它来更改队列的全部内容。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Myqueue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="back"></a> queue::back (STL/CLR)

访问最后一个元素。

### <a name="syntax"></a>语法

```cpp
reference back();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列，必须为非空的最后一个元素的引用。 用于访问的最后一个元素，当您知道它存在。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

// alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
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

```cpp
property value_type back_item;
```

### <a name="remarks"></a>备注

属性访问，必须为非空的受控序列的最后一个元素。 您可以使用它来读取或写入的最后一个元素，当您知道它存在。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

// alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
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

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>备注

此类型描述的元素的常量引用。

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
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="container_type"></a> queue::container_type (STL/CLR)

基础容器的类型。

### <a name="syntax"></a>语法

```cpp
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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="difference_type"></a> queue::difference_type (STL/CLR)

两个元素之间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>备注

此类型描述可能是负值元素计数。

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
        System::Console::Write("{0} ", elem);
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

```cpp
bool empty();
```

### <a name="remarks"></a>备注

对于空受控序列，该成员函数返回 true。 它等效于[queue:: size (STL/CLR)](../dotnet/queue-size-stl-clr.md)`() == 0`。 用于测试是否队列为空。

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
        System::Console::Write("{0} ", elem);
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

## <a name="front"></a> queue::front (STL/CLR)

访问第一个元素。

### <a name="syntax"></a>语法

```cpp
reference front();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列，必须为非空的第一个元素的引用。 用于访问第一个元素，当您知道它存在。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

// alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
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

```cpp
property value_type front_item;
```

### <a name="remarks"></a>备注

属性访问，必须为非空的受控序列的第一个元素。 您可以使用它来读取或写入的第一个元素，当您知道它存在。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

// alter last item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
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

```cpp
typedef Microsoft::VisualC::StlClr::IQueue<Value>
    generic_container;
```

### <a name="remarks"></a>备注

此类型描述此模板容器适配器类的泛型接口。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myqueue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
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

用于容器的泛型接口具有的元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>备注

此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。 (`GValue`可以是`value_type`或`value_type^`如果`value_type`是 ref 类型。)

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Myqueue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Myqueue::generic_value elem = gc1->front();

        System::Console::Write("{0} ", elem);
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

访问基础容器。

### <a name="syntax"></a>语法

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>备注

成员函数返回基础容器。 您可以使用它来跳过容器包装所规定的限制。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_as"></a> queue::operator= (STL/CLR)

替换受控序列。

### <a name="syntax"></a>语法

```cpp
queue <Value, Container>% operator=(queue <Value, Container>% right);
```

#### <a name="parameters"></a>参数

*right*<br/>
若要复制的容器适配器。

### <a name="remarks"></a>备注

成员运算符副本*右*对象，然后返回`*this`。 用于替换受控的序列中的受控序列的副本*右*。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="pop"></a> queue::pop (STL/CLR)

删除最后一个元素。

### <a name="syntax"></a>语法

```cpp
void pop();
```

### <a name="remarks"></a>备注

成员函数删除必须为非空的受控序列的最后一个元素。 您可以使用它来缩短队列在后一个元素。

### <a name="example"></a>示例

```cpp
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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="push"></a> queue::push (STL/CLR)

添加一个新的最后一个元素。

### <a name="syntax"></a>语法

```cpp
void push(value_type val);
```

### <a name="remarks"></a>备注

成员函数将具有值的元素添加`val`队列的末尾。 用于将元素追加到队列。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="queue"></a> queue::queue (STL/CLR)

构造容器适配器对象。

### <a name="syntax"></a>语法

```cpp
queue();
queue(queue<Value, Container>% right);
queue(queue<Value, Container>^ right);
explicit queue(container_type% wrapped);
```

#### <a name="parameters"></a>参数

*right*<br/>
要复制的对象。

*wrapped*<br/>
若要使用的已包装的容器。

### <a name="remarks"></a>备注

构造函数：

`queue();`

创建一个空的已包装的容器。 用于指定空的初始受控的序列。

构造函数：

`queue(queue<Value, Container>% right);`

创建已包装的容器是一份`right.get_container()`。 用于指定是控制队列对象的序列的副本的初始受控的序列*右*。

构造函数：

`queue(queue<Value, Container>^ right);`

创建已包装的容器是一份`right->get_container()`。 用于指定是控制队列对象的序列的副本的初始受控的序列`*right`。

构造函数：

`explicit queue(container_type wrapped);`

使用现有容器*包装*作为已包装的容器。 使用它来构造一个队列从现有的容器。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myqueue_list c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Myqueue_list c4(%c2);
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
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

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>备注

此类型描述的元素的引用。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify back of queue and redisplay
    Myqueue::reference ref = c1.back();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
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

```cpp
size_type size();
```

### <a name="remarks"></a>备注

成员函数将返回受控序列的长度。 用于确定受控序列中当前元素的数目。 如果您关心的只是该序列是否具有非零大小，请参阅[queue:: empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)`()`。

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
        System::Console::Write("{0} ", elem);
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

## <a name="size_type"></a> queue::size_type (STL/CLR)

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>备注

此类型描述非负元素计数。

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
        System::Console::Write("{0} ", elem);
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

将受控的序列复制到新数组。

### <a name="syntax"></a>语法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>备注

成员函数返回一个数组，包含对受控的序列。 用于获取数组形式的受控序列的副本。

### <a name="example"></a>示例

```cpp
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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="value_type"></a> queue::value_type (STL/CLR)

元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>备注

该类型是模板参数的同义词*值*。

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

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a> operator!= (queue) (STL/CLR)

队列不相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value,
    typename Container>
    bool operator!=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(left == right)`。 使用它来测试是否*左*未排序相同*右*当两个队列都比较的元素的方式。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
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

## <a name="op_lt"></a> operator&lt; (queue) (STL/CLR)

队列小于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value,
    typename Container>
    bool operator<(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回 true 当对于最低的位置`i`为其`!(right[i] < left[i])`它是还 true 的`left[i] < right[i]`。 否则，它将返回`left->` [queue:: size (STL/CLR)](../dotnet/queue-size-stl-clr.md) `() <` `right->size()`使用它来测试是否*左*排序之前*右*当两个队列都是比较的元素的方式。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
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

## <a name="op_lteq"></a> operator&lt;= (queue) (STL/CLR)

队列小于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value,
    typename Container>
    bool operator<=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(right < left)`。 使用它来测试是否*左*未排序后*右*当两个队列都比较的元素的方式。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
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

## <a name="op_eq"></a> operator== (queue) (STL/CLR)

队列相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value,
    typename Container>
    bool operator==(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数才返回 true，序列由控制*左*并*右*具有相同的长度和每个位置`i`， `left[i] ==` `right[i]`。 使用它来测试是否*左*进行排序相同*右*当两个队列都比较的元素的方式。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
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

## <a name="op_gt"></a> operator&gt; (queue) (STL/CLR)

大于比较的队列。

### <a name="syntax"></a>语法

```cpp
template<typename Value,
    typename Container>
    bool operator>(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数将返回`right` `<` `left`。 使用它来测试是否*左*进行排序后*右*当两个队列都比较的元素的方式。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
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

## <a name="op_gteq"></a> operator&gt;= (queue) (STL/CLR)

队列大于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value,
    typename Container>
    bool operator>=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(left < right)`。 使用它来测试是否*左*未排序之前*右*当两个队列都比较的元素的方式。

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
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
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