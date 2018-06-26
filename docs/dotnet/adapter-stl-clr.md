---
title: 适配器 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 06/15/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 598159ff01fe1628a693085f84077d9adfcbbf49
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305535"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)
STL/CLR 标头`<cliext/adapter>`指定两个模板类 (`collection_adapter`和`range_adapter`)，该模板函数`make_collection`。  
  
## <a name="syntax"></a>语法  
  
```  
#include <cliext/adapter>  
```  

## <a name="requirements"></a>要求  
 **标头：** \<cliext/适配器 >  
  
 **Namespace:** cliext 
  
## <a name="members"></a>成员  
  
|类|Description|  
|-----------|-----------------|  
|[collection_adapter (STL/CLR)](#collection_adapter)|包装为一个范围的基类库 (BCL) 集合。|  
|[range_adapter (STL/CLR)](#range_adapter)|包装为 BCL 集合的范围。|  

|函数|Description|  
|--------------|-----------------|  
|[make_collection (STL/CLR)](#make_collection)|创建范围适配器使用的迭代器对。|   
  
## <a name="collection_adapter"></a> collection_adapter (STL/CLR)
包装.NET 集合以用作 STL/CLR 容器。 A`collection_adapter`是一种模板类描述一个简单的 STL/CLR 容器对象。 它包装一个基类库 (BCL) 接口，并返回用于处理受控的序列的迭代器对。  
  
### <a name="syntax"></a>语法  
  
```  
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
  
##### <a name="parameters"></a>参数  
 如果给定  
 已包装的集合的类型。  
  
### <a name="specializations"></a>专用化  
  
|专用化|Description|  
|--------------------|-----------------|  
|IEnumerable|通过元素的序列。|  
|ICollection|维护一的组元素。|  
|IList|维护元素的有序的组。|  
|IDictionary|维护一套 {键，值} 对。|  
|IEnumerable\<值 >|访问类型化元素的序列。|  
|ICollection\<值 >|维护一的组类型化的元素。|  
|IList\<值 >|维护类型化元素的有序的组。|  
|IDictionary\<值 >|维护一组的类型化 {键，值} 对。|  
  
### <a name="members"></a>成员  
  
|类型定义|Description|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|  
|[collection_adapter::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|  
|[collection_adapter::key_type (STL/CLR)](#key_type)|字典键的类型。|  
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|字典值的类型。|  
|[collection_adapter::reference (STL/CLR)](#reference)|元素的引用的类型。|  
|[collection_adapter::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|  
|[collection_adapter::value_type (STL/CLR)](#value_type)|元素的类型。|  
  
|成员函数|Description|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](#base)|指定的已包装的 BCL 接口。|  
|[collection_adapter::begin (STL/CLR)](#begin)|指定受控序列的开头。|  
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|将构造一个适配器对象。|  
|[collection_adapter::end (STL/CLR)](#end)|指定受控序列的末尾。|  
|[collection_adapter::size (STL/CLR)](#size)|对元素数进行计数。|  
|[collection_adapter::swap (STL/CLR)](#swap)|交换两个容器的内容。|  
  
|运算符|Description|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](#op_eq)|替换存储的 BCL 句柄。|  
  
### <a name="remarks"></a>备注  
 使用此模板类来操作作为 STL/CLR 容器的 BCL 容器。 `collection_adapter`存储 BCL 接口，这反过来控制序列的元素的句柄。 A`collection_adapter`对象`X`返回一对输入迭代器`X.begin()`和`X.end()`用于访问的元素顺序。 某些专用化还允许你编写`X.size()`以确定受控序列的长度。  

## <a name="base"></a> collection_adapter::base (STL/CLR)
指定的已包装的 BCL 接口。  
  
### <a name="syntax"></a>语法  
  
```  
Coll^ base();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回存储的 BCL 接口句柄。  
  
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
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
base() same = True  
```  

## <a name="begin"></a> collection_adapter::begin (STL/CLR)
指定受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回指定第一个元素的受控序列，或刚超出空序列末尾的输入迭代器。  
  
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
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
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

## <a name="collection_adapter_collection_adapter"></a> collection_adapter::collection_adapter (STL/CLR)
将构造一个适配器对象。  
  
### <a name="syntax"></a>语法  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>参数  
 集合  
 要包装的 BCL 句柄。  
  
 右  
 要复制的对象。  
  
### <a name="remarks"></a>备注  
 构造函数：  
  
 `collection_adapter();`  
  
 初始化与存储的句柄`nullptr`。  
  
 构造函数：  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 初始化与存储的句柄`right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`。  
  
 构造函数：  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 初始化与存储的句柄`right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`。  
  
 构造函数：  
  
 `collection_adapter(Coll^ collection);`  
  
 初始化存储与句柄与`collection`。  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
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

## <a name="difference_type"></a> collection_adapter::difference_type (STL/CLR)
两个元素间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述签名的元素计数。  
  
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
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
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

## <a name="end"></a> collection_adapter::end (STL/CLR)
指定受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回输入迭代器，它指向刚超出受控序列的末尾。  
  
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
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="iterator"></a> collection_adapter::iterator (STL/CLR)
受控序列的迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T1`，可用作受控序列的输入迭代器。  
  
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
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_type"></a> collection_adapter::key_type (STL/CLR)
字典键的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词`Key`，在专用化`IDictionary`或`IDictionary<Value>`; 否则为未定义。  
  
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
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> collection_adapter::mapped_type (STL/CLR)
字典值的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Value mapped_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词`Value`，在专用化`IDictionary`或`IDictionary<Value>`; 否则为未定义。  
  
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
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_eq"></a> collection_adapter::operator = (STL/CLR)
替换存储的 BCL 句柄。  
  
### <a name="syntax"></a>语法  
  
```  
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的适配器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用于将替换中的存储 BCL 句柄的副本存储的 BCL 句柄`right`。  
  
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
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mycoll c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="reference"></a> collection_adapter::reference (STL/CLR)
元素的引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的引用。  
  
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
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mycoll::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="size"></a> collection_adapter::size (STL/CLR)
对元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 中的专用化未定义`IEnumerable`或`IEnumerable<Value>`。  
  
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
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="size_type"></a> collection_adapter::size_type (STL/CLR)
两个元素之间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述非负元素计数。  
  
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
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
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

## <a name="swap"></a> collection_adapter::swap (STL/CLR)
交换两个容器的内容。  
  
### <a name="syntax"></a>语法  
  
```  
void swap(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要与其交换内容的容器。  
  
### <a name="remarks"></a>备注  
 成员函数交换之间的存储的 BCL 句柄`*this`和`right`。  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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

## <a name="value_type"></a> collection_adapter::value_type (STL/CLR)
元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词`Value`，如果存在专用化; 否则它是同义词`System::Object^`。  
  
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
  
// display contents " a b c" using value_type   
    for (Mycoll::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mycoll::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="make_collection"></a> make_collection (STL/CLR)
请`range_adapter`从迭代器对。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Iter>  
    range_adapter<Iter> make_collection(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>参数  
 `Iter`  
 已包装的迭代器的类型。  
  
 `first`  
 要包装的第一个迭代器。  
  
 `last`  
 要包装的第二个迭代器。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `gcnew range_adapter<Iter>(first, last)`。 使用它来构造`range_adapter<Iter>`从一对迭代器的对象。  
  
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
        System::Console::Write(" {0}", elem);   
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
        System::Console::Write(" {0}", elem);   
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

## <a name="range_adapter"></a> range_adapter (STL/CLR)
一种模板类，用于包装一对迭代器，用于实现多个基类库 (BCL) 接口。 Range_adapter 用于处理 STL/CLR 范围，就像它是 BCL 集合。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 Iter  
 与已包装的迭代器关联的类型。  
  
### <a name="members"></a>成员  
  
|成员函数|Description|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|将构造一个适配器对象。|  
  
|运算符|Description|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|替换存储的迭代器对。|  
  
### <a name="interfaces"></a>接口  
  
|接口|Description|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|循环访问集合中的元素。|  
|<xref:System.Collections.ICollection>|维护一的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|循环访问集合中的类型化元素...|  
|<xref:System.Collections.Generic.ICollection%601>|维护一的组类型化的元素。|  
  
### <a name="remarks"></a>备注  
 Range_adapter 存储一对迭代器，反过来分隔的元素序列。 该对象实现四个 BCL 接口，可以循环访问的元素顺序。 使用此模板类来操作非常类似 BCL 容器 STL/CLR 范围。  

## <a name="range_adapter_op_eq"></a> range_adapter::operator = (STL/CLR)
替换存储的迭代器对。  
  
### <a name="syntax"></a>语法  
  
```  
range_adapter<Iter>% operator=(range_adapter<Iter>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的适配器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用于使用存储的迭代器对在副本替换存储的迭代器对`right`。  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myrange c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="range_adapter_range_adapter"></a> range_adapter::range_adapter (STL/CLR)
将构造一个适配器对象。  
  
### <a name="syntax"></a>语法  
  
```  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要包装的第一个迭代器。  
  
 last  
 要包装的第二个迭代器。  
  
 右  
 要复制的对象。  
  
### <a name="remarks"></a>备注  
 构造函数：  
  
 `range_adapter();`  
  
 初始化使用默认构造迭代器的存储的迭代器对。  
  
 构造函数：  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 通过将复制的对存储在初始化存储的迭代器对`right`。  
  
 构造函数：  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 通过将复制的对存储在初始化存储的迭代器对`*right`。  
  
 构造函数：  
  
 `range_adapter(Iter^ first, last);`  
  
 初始化带的存储的迭代器对`first`和`last`。  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  