---
title: adapter (STL/CLR)
ms.date: 06/15/2018
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
ms.openlocfilehash: bdaf5e0e8e4d9620e7a55dfff84f271f0059faf3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545689"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)

STL/CLR 标头 `<cliext/adapter>` 指定两个模板类（`collection_adapter` 和 `range_adapter`）和模板函数 `make_collection`。

## <a name="syntax"></a>语法

```cpp
#include <cliext/adapter>
```

## <a name="requirements"></a>要求

**标头：** \<cliext/adapter >

**命名空间：** cliext

## <a name="declarations"></a>声明

|类|说明|
|-----------|-----------------|
|[collection_adapter (STL/CLR)](#collection_adapter)|将基类库（BCL）集合作为范围进行包装。|
|[range_adapter (STL/CLR)](#range_adapter)|将范围包装为 BCL 集合。|

|函数|说明|
|--------------|-----------------|
|[make_collection (STL/CLR)](#make_collection)|使用迭代器对创建范围适配器。|

## <a name="members"></a>成员

## <a name="collection_adapter-stlclr"></a><a name="collection_adapter"></a>collection_adapter （STL/CLR）

包装 .NET 集合以用作 STL/CLR 容器。 `collection_adapter` 是一种模板类，用于描述简单的 STL/CLR 容器对象。 它包装基类库（BCL）接口，并返回用于操作受控序列的迭代器对。

### <a name="syntax"></a>语法

```cpp
template<typename Coll>
    ref class collection_adapter;

template<>
    ref class collection_adapter<
        System::Collections::ICollection>;
template<>
    ref class collection_adapter<
        System::Collections::IEnumerable>;
template<>
    ref class collection_adapter<
        System::Collections::IList>;
template<>
    ref class collection_adapter<
        System::Collections::IDictionary>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::ICollection<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IEnumerable<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IList<Value>>;
template<typename Key,
    typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IDictionary<Key, Value>>;
```

#### <a name="parameters"></a>parameters

*Coll*<br/>
包装的集合的类型。

### <a name="specializations"></a>专用化

|专用化|说明|
|--------------------|-----------------|
|IEnumerable|通过元素进行排序。|
|ICollection|维护一组元素。|
|IList|维护一组有序的元素。|
|IDictionary|维护一组 {key，value} 对。|
|IEnumerable\<值 >|通过类型化元素的序列。|
|ICollection\<值 >|维护一组类型化的元素。|
|IList\<值 >|维护一组有序的类型化元素。|
|IDictionary\<值 >|维护一组类型化 {key，value} 对。|

### <a name="members"></a>成员

|类型定义|说明|
|---------------------|-----------------|
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|
|[collection_adapter::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|
|[collection_adapter::key_type (STL/CLR)](#key_type)|字典键的类型。|
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|字典值的类型。|
|[collection_adapter::reference (STL/CLR)](#reference)|元素的引用的类型。|
|[collection_adapter::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|
|[collection_adapter::value_type (STL/CLR)](#value_type)|元素的类型。|

|成员函数|说明|
|---------------------|-----------------|
|[collection_adapter::base (STL/CLR)](#base)|指定包装的 BCL 接口。|
|[collection_adapter::begin (STL/CLR)](#begin)|指定受控序列的开头。|
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|构造适配器对象。|
|[collection_adapter::end (STL/CLR)](#end)|指定受控序列的末尾。|
|[collection_adapter::size (STL/CLR)](#size)|对元素数进行计数。|
|[collection_adapter::swap (STL/CLR)](#swap)|交换两个容器的内容。|

|操作员|说明|
|--------------|-----------------|
|[collection_adapter::operator= (STL/CLR)](#op_eq)|替换存储的 BCL 句柄。|

### <a name="remarks"></a>备注

使用此模板类可以将 BCL 容器作为 STL/CLR 容器进行操作。 `collection_adapter` 将句柄存储到 BCL 接口，而该接口又控制一系列元素。 `collection_adapter` 对象 `X` 返回一对输入迭代器 `X.begin()` 和用于按顺序访问元素的 `X.end()`。 某些专用化还允许编写 `X.size()` 来确定受控序列的长度。

## <a name="collection_adapterbase-stlclr"></a><a name="base"></a>collection_adapter：： base （STL/CLR）

指定包装的 BCL 接口。

### <a name="syntax"></a>语法

```cpp
Coll^ base();
```

### <a name="remarks"></a>备注

该成员函数将返回存储的 BCL 接口句柄。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_base.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);
    return (0);
    }
```

```Output
x x x x x x
base() same = True
```

## <a name="collection_adapterbegin-stlclr"></a><a name="begin"></a>collection_adapter：： begin （STL/CLR）

指定受控序列的开头。

### <a name="syntax"></a>语法

```cpp
iterator begin();
```

### <a name="remarks"></a>备注

成员函数返回一个输入迭代器，该迭代器指定受控序列的第一个元素，或刚超出空序列的末尾。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_begin.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mycoll::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
}
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="collection_adaptercollection_adapter-stlclr"></a><a name="collection_adapter_collection_adapter"></a>collection_adapter：： collection_adapter （STL/CLR）

构造适配器对象。

### <a name="syntax"></a>语法

```cpp
collection_adapter();
collection_adapter(collection_adapter<Coll>% right);
collection_adapter(collection_adapter<Coll>^ right);
collection_adapter(Coll^ collection);
```

#### <a name="parameters"></a>parameters

collection<br/>
要包装的 BCL 句柄。

right<br/>
要复制的对象。

### <a name="remarks"></a>备注

构造函数：

`collection_adapter();`

用 `nullptr`初始化存储句柄。

构造函数：

`collection_adapter(collection_adapter<Coll>% right);`

`()``right.`[collection_adapter：： base （STL/CLR）](../dotnet/collection-adapter-base-stl-clr.md)初始化存储的句柄。

构造函数：

`collection_adapter(collection_adapter<Coll>^ right);`

`()``right->`[collection_adapter：： base （STL/CLR）](../dotnet/collection-adapter-base-stl-clr.md)初始化存储的句柄。

构造函数：

`collection_adapter(Coll^ collection);`

用 `collection`初始化存储句柄。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');

    // construct an empty container
    Mycoll c1;
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);

    // construct with a handle
    Mycoll c2(%d6x);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mycoll c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mycoll c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
base() null = True
x x x x x x
x x x x x x
x x x x x x
```

## <a name="collection_adapterdifference_type-stlclr"></a><a name="difference_type"></a>collection_adapter：:d ifference_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>备注

类型描述有符号的元素计数。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_difference_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mycoll::difference_type diff = 0;
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
}
```

```Output
a b c
end()-begin() = 3
```

## <a name="collection_adapterend-stlclr"></a><a name="end"></a>collection_adapter：： end （STL/CLR）

指定受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
iterator end();
```

### <a name="remarks"></a>备注

成员函数返回一个输入迭代器，它指向刚超出受控序列末尾的位置。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_end.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapteriterator-stlclr"></a><a name="iterator"></a>collection_adapter：： iterator （STL/CLR）

受控序列的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>备注

该类型描述可用作受控序列输入迭代器的未指定类型 `T1` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_iterator.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapterkey_type-stlclr"></a><a name="key_type"></a>collection_adapter：： key_type （STL/CLR）

字典键的类型。

### <a name="syntax"></a>语法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `Key`的同义词，在 `IDictionary` 或 `IDictionary<Value>`专用化中;否则，不会定义它。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_key_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adaptermapped_type-stlclr"></a><a name="mapped_type"></a>collection_adapter：： mapped_type （STL/CLR）

字典值的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value mapped_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `Value`的同义词，在 `IDictionary` 或 `IDictionary<Value>`专用化中;否则，不会定义它。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_mapped_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adapteroperator-stlclr"></a><a name="op_eq"></a>collection_adapter：： operator = （STL/CLR）

替换存储的 BCL 句柄。

### <a name="syntax"></a>语法

```cpp
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>parameters

right<br/>
要复制的适配器。

### <a name="remarks"></a>备注

成员运算符*直接*复制到对象，然后返回 `*this`。 使用此方法可以将存储的 BCL 句柄替换为*右侧*存储的 bcl 控点的副本。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mycoll c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
a b c
```

## <a name="collection_adapterreference-stlclr"></a><a name="reference"></a>collection_adapter：： reference （STL/CLR）

元素的引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>备注

类型描述对元素的引用。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_reference.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
    {   // get a reference to an element
        Mycoll::reference ref = *it;
        System::Console::Write("{0} ", ref);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adaptersize-stlclr"></a><a name="size"></a>collection_adapter：： size （STL/CLR）

对元素数进行计数。

### <a name="syntax"></a>语法

```cpp
size_type size();
```

### <a name="remarks"></a>备注

成员函数将返回受控序列的长度。 未在 `IEnumerable` 或 `IEnumerable<Value>`的专用化中定义它。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_size.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adaptersize_type-stlclr"></a><a name="size_type"></a>collection_adapter：： size_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>备注

该类型描述了一个非负元素计数。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_size_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    Mycoll::size_type size = c1.size();
    System::Console::WriteLine("size() = {0}", size);
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adapterswap-stlclr"></a><a name="swap"></a>collection_adapter：： swap （STL/CLR）

交换两个容器的内容。

### <a name="syntax"></a>语法

```cpp
void swap(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>parameters

right<br/>
要与其交换内容的容器。

### <a name="remarks"></a>备注

该成员函数在 `*this` 和*权限*之间交换存储的 BCL 句柄。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="collection_adaptervalue_type-stlclr"></a><a name="value_type"></a>collection_adapter：： value_type （STL/CLR）

元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>备注

该类型是模板参数*值*（如果存在于特殊化中）的同义词;否则，它是 `System::Object^`的同义词。

### <a name="example"></a>示例

```cpp
// cliext_collection_adapter_value_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display contents "a b c" using value_type
    for (Mycoll::iterator it = c1.begin();
        it != c1.end(); ++it)
    {   // store element in value_type object
        Mycoll::value_type val = *it;

        System::Console::Write("{0} ", val);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="make_collection-stlclr"></a><a name="make_collection"></a>make_collection （STL/CLR）

从迭代器对中进行 `range_adapter`。

### <a name="syntax"></a>语法

```cpp
template<typename Iter>
    range_adapter<Iter> make_collection(Iter first, Iter last);
```

#### <a name="parameters"></a>parameters

*Iter*<br/>
已包装迭代器的类型。

*first*<br/>
要包装的第一个迭代器。

*last*<br/>
要包装的第二个迭代器。

### <a name="remarks"></a>备注

此模板函数返回 `gcnew range_adapter<Iter>(first, last)`。 用于从一对迭代器构造 `range_adapter<Iter>` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_make_collection.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in d1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Collections::ICollection^ p1 =
        cliext::make_collection(d1.begin(), d1.end());
    System::Console::WriteLine("Count = {0}", p1->Count);
    System::Console::WriteLine("IsSynchronized = {0}",
        p1->IsSynchronized);
    System::Console::WriteLine("SyncRoot not nullptr = {0}",
        p1->SyncRoot != nullptr);

    // copy the sequence
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);

    a1[0] = L'|';
    p1->CopyTo(a1, 1);
    a1[4] = L'|';
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
Count = 3
IsSynchronized = False
SyncRoot not nullptr = True
| a b c |
```

## <a name="range_adapter-stlclr"></a><a name="range_adapter"></a>range_adapter （STL/CLR）

一个模板类，用于包装用于实现多个基类库（BCL）接口的一对迭代器。 使用 range_adapter 来操作 STL/CLR 范围，就像它是 BCL 集合一样。

### <a name="syntax"></a>语法

```cpp
template<typename Iter>
    ref class range_adapter
        :   public
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<Value>,
        System::Collections::Generic::ICollection<Value>
    { ..... };
```

#### <a name="parameters"></a>parameters

*Iter*<br/>
与已包装的迭代器关联的类型。

### <a name="members"></a>成员

|成员函数|说明|
|---------------------|-----------------|
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|构造适配器对象。|

|操作员|说明|
|--------------|-----------------|
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|替换存储的迭代器对。|

### <a name="interfaces"></a>界面

|接口|说明|
|---------------|-----------------|
|<xref:System.Collections.IEnumerable>|循环访问集合中的元素。|
|<xref:System.Collections.ICollection>|维护一组元素。|
|<xref:System.Collections.Generic.IEnumerable%601>|循环访问集合中的类型化元素。|
|<xref:System.Collections.Generic.ICollection%601>|维护一组类型化的元素。|

### <a name="remarks"></a>备注

Range_adapter 存储一对迭代器，这两个迭代器进而分隔元素的序列。 对象实现四个 BCL 接口，它们使你能够按顺序循环访问元素。 使用此模板类可以操作 STL/CLR 范围，这与 BCL 容器非常类似。

## <a name="range_adapteroperator-stlclr"></a><a name="range_adapter_op_eq"></a>range_adapter：： operator = （STL/CLR）

替换存储的迭代器对。

### <a name="syntax"></a>语法

```cpp
range_adapter<Iter>% operator=(range_adapter<Iter>% right);
```

#### <a name="parameters"></a>parameters

right<br/>
要复制的适配器。

### <a name="remarks"></a>备注

成员运算符*直接*复制到对象，然后返回 `*this`。 使用此方法可以将存储的迭代器对替换为*右侧*存储的迭代器对的副本。

### <a name="example"></a>示例

```cpp
// cliext_range_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Myrange c1(d1.begin(), d1.end());

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myrange c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
a b c
```

## <a name="range_adapterrange_adapter-stlclr"></a><a name="range_adapter_range_adapter"></a>range_adapter：： range_adapter （STL/CLR）

构造适配器对象。

### <a name="syntax"></a>语法

```cpp
range_adapter();
range_adapter(range_adapter<Iter>% right);
range_adapter(range_adapter<Iter>^ right);
range_adapter(Iter first, Iter last);
```

#### <a name="parameters"></a>parameters

*first*<br/>
要包装的第一个迭代器。

*last*<br/>
要包装的第二个迭代器。

right<br/>
要复制的对象。

### <a name="remarks"></a>备注

构造函数：

`range_adapter();`

用默认的构造迭代器初始化存储的迭代器对。

构造函数：

`range_adapter(range_adapter<Iter>% right);`

通过复制*右侧*存储的对来初始化存储的迭代器对。

构造函数：

`range_adapter(range_adapter<Iter>^ right);`

通过复制存储在 `*right`中的对，初始化存储的迭代器对。

构造函数：

`range_adapter(Iter^ first, last);`

用*first*和*last*初始化存储的迭代器对。

### <a name="example"></a>示例

```cpp
// cliext_range_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // construct an empty adapter
    Myrange c1;

    // construct with an iterator pair
    Myrange c2(d1.begin(), d1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another adapter
    Myrange c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying an adapter handle
    Myrange c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
a b c
a b c
```
