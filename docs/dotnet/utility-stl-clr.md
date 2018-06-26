---
title: 实用工具 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
dev_langs:
- C++
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fcc97e5037898b3a9c39a6c72ed21b2c19a4c777
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2018
ms.locfileid: "36306016"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)
包括 STL/CLR 标头`<cliext/utility>`定义模板类`pair`和几个支持模板函数。  
  
## <a name="syntax"></a>语法  
  
```  
#include <utility>  
```

## <a name="requirements"></a>要求  
 **标头：** \<cliext/实用工具 >  
  
 **Namespace:** cliext  
  
## <a name="declarations"></a>声明  
  
|类|Description|  
|-----------|-----------------|  
|[pair (STL/CLR)](#pair)|包装元素的对。|  
  
|运算符|Description|  
|--------------|-----------------|  
|[operator== (pair) (STL/CLR)](#op_eq)|对相等比较。|  
|[operator!= (pair) (STL/CLR)](#op_neq)|对不相等比较。|  
|[operator< (pair) (STL/CLR)](#op_lt)|对小于比较。|  
|[运算符\<= （对） (STL/CLR)](#op_lteq)|小于或等于配对比较。|  
|[operator> (pair) (STL/CLR)](#op_gt)|对大于比较。|  
|[operator>= (pair) (STL/CLR)](#op_gteq)|对大于或等于比较。|  
  
|函数|Description|  
|--------------|-----------------|  
|[make_pair (STL/CLR)](#make_pair)|请从一对值对。|  

## <a name="members"></a>成员

##<a name="pair"></a> 对 (STL/CLR)
此模板类描述一个包装成对的值的对象。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>参数  
 Value1  
 第一个已包装的值的类型。  
  
 Value2  
 第二个已包装的值的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|Description|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](#first_type)|第一个包装值类型。|  
|[pair::second_type (STL/CLR)](#second_type)|已包装的第二个值的类型。|  
  
|成员对象|Description|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](#first)|第一个存储的值。|  
|[pair::second (STL/CLR)](#second)|第二个存储的值。|  
  
|成员函数|Description|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](#pair_pair)|构造 pair 对象。|  
|[pair::swap (STL/CLR)](#swap)|交换两个对的内容。|  
  
|运算符|Description|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](#op_as)|替换存储的值对。|  
  
## <a name="remarks"></a>备注  
 此对象存储值的对。 你使用此模板类将两个值合并到单个对象。 此外，对象`cliext::pair`（此处所述） 存储仅托管类型; 若要存储的成对的非托管类型，请使用`std::pair`中声明`<utility>`。  


## <a name="first"></a> pair::first (STL/CLR)
第一个已包装的值。  
  
### <a name="syntax"></a>语法  
  
```  
Value1 first;  
```  
  
### <a name="remarks"></a>备注  
 此对象存储的已包装的第一个值。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_first.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="first_type"></a> pair::first_type (STL/CLR)
第一个包装值类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Value1 first_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Value1` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_first_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="op_as"></a> pair::operator = (STL/CLR)
替换存储的值对。  
  
### <a name="syntax"></a>语法  
  
```  
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的对。  
  
### <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用于使用存储对中值的副本替换存储的值对的`right`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_operator_as.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
// assign to a new pair   
    cliext::pair<wchar_t, int> c2;   
    c2 = c1;   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 3]  
```  

## <a name="pair_pair"></a> pair::pair (STL/CLR)
构造 pair 对象。  
  
### <a name="syntax"></a>语法  
  
```  
pair();  
pair(pair<Coll>% right);  
pair(pair<Coll>^ right);  
pair(Value1 val1, Value2 val2);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要存储对。  
  
 val1  
 要存储的第一个值。  
  
 val2  
 要存储的第二个值。  
  
### <a name="remarks"></a>备注  
 构造函数：  
  
 `pair();`  
  
 初始化使用默认构造值的存储的对。  
  
 构造函数：  
  
 `pair(pair<Value1, Value2>% right);`  
  
 初始化带的存储的对`right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)和`right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)。  
  
 `pair(pair<Value1, Value2>^ right);`  
  
 初始化带的存储的对`right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)和`right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)。  
  
 构造函数：  
  
 `pair(Value1 val1, Value2 val2);`  
  
 初始化与带的存储的对`val1`和`val2`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_construct.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
// construct an empty container   
    cliext::pair<wchar_t, int> c1;   
    System::Console::WriteLine("[{0}, {1}]",   
        c1.first == L'\0' ? "\\0" : "??", c1.second);   
  
// construct with a pair of values   
    cliext::pair<wchar_t, int> c2(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
// construct by copying another pair   
    cliext::pair<wchar_t, int> c3(c2);   
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);   
  
// construct by copying a pair handle   
    cliext::pair<wchar_t, int> c4(%c3);   
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);   
  
    return (0);   
    }  
  
```  
  
```Output  
[\0, 0]  
[x, 3]  
[x, 3]  
[x, 3]  
```  

## <a name="second"></a> pair::second (STL/CLR)
第二个包装值。  
  
### <a name="syntax"></a>语法  
  
```  
Value2 second;  
```  
  
### <a name="remarks"></a>备注  
 此对象存储的已包装的第二个值。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_second.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="second_type"></a> pair::second_type (STL/CLR)
已包装的第二个值的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Value2 second_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Value2` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_second_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```    

## <a name="swap"></a> pair::swap (STL/CLR)
交换两个对的内容。  
  
### <a name="syntax"></a>语法  
  
```  
void swap(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 对要与其交换内容。  
  
### <a name="remarks"></a>备注  
 成员函数交换之间的值的存储的对`*this`和`right`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_swap.cpp   
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

## <a name="make_pair"></a> make_pair (STL/CLR)
请`pair`从一对值。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>参数  
 `Value1`  
 第一个包装值类型。  
  
 `Value2`  
 已包装的第二个值的类型。  
  
 `first`  
 要包装的第一个值。  
  
 `second`  
 要包装的第二个值。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `pair<Value1, Value2>(first, second)`。 使用它来构造`pair<Value1, Value2>`从一对值的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[y, 4]  
```  

## <a name="op_neq"></a> 运算符 ！ = （对） (STL/CLR)
对不相等比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator!=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左的对。  
  
 右  
 要比较的右对。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(left == right)`。 用于测试是否`left`未进行排序相同`right`时的两个对是元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp
// cliext_pair_operator_ne.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] != [x 3] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[x 3] != [x 4] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] != [x 3] is False  
[x 3] != [x 4] is True  
```  
  
## <a name="op_lt"></a> 运算符&lt;（对） (STL/CLR)
对小于比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左的对。  
  
 右  
 要比较的右对。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`。 用于测试是否`left`进行排序之前`right`时的两个对是元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_operator_lt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] < [x 3] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[x 3] < [x 4] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] < [x 3] is False  
[x 3] < [x 4] is True  
```  

## <a name="op_lteq"></a> 运算符&lt;= （对） (STL/CLR)
小于或等于配对比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左的对。  
  
 右  
 要比较的右对。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(right < left)`。 用于测试是否`left`未进行排序之后`right`时的两个对是元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_operator_le.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] <= [x 3] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] <= [x 3] is True  
[x 4] <= [x 3] is False  
```  
  
## <a name="op_eq"></a> 运算符 = = （对） (STL/CLR)
对相等比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator==(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左的对。  
  
 右  
 要比较的右对。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`left.first ==` `right.first &&` `left.second ==` `right.second`。 用于测试是否`left`进行排序相同`right`时的两个对是元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_operator_eq.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] == [x 3] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[x 3] == [x 4] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] == [x 3] is True  
[x 3] == [x 4] is False  
```  

## <a name="op_gt"></a> 运算符&gt;（对） (STL/CLR)
对大于比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左的对。  
  
 右  
 要比较的右对。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`right` `<` `left`。 用于测试是否`left`进行排序之后`right`时的两个对是元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_operator_gt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] > [x 3] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[x 4] > [x 3] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] > [x 3] is False  
[x 4] > [x 3] is True  
```  

## <a name="op_gteq"></a> 运算符&gt;= （对） (STL/CLR)
对大于或等于比较。  
  
### <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左的对。  
  
 右  
 要比较的右对。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(left < right)`。 用于测试是否`left`未进行排序之前`right`时的两个对是元素的比较的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_pair_operator_ge.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] >= [x 3] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] >= [x 3] is True  
[x 3] >= [x 4] is False  
```  
