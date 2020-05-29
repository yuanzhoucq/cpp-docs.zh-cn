---
title: utility (STL/CLR)
ms.date: 11/04/2016
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
ms.openlocfilehash: 6d025230abcff42e367a231e616a13f0f8c684f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320299"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

包括用于定义模板类`<cliext/utility>``pair`的 STL/CLR 标头以及多个支持模板函数。

## <a name="syntax"></a>语法

```cpp
#include <utility>
```

## <a name="requirements"></a>要求

**标题**\<：cliext/实用程序>

**命名空间**：cliext

## <a name="declarations"></a>声明

|类|说明|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|包装一对元素。|

|操作员|说明|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|对相等的比较。|
|[运算符！* （对） （STL/CLR）](#op_neq)|对不相等的比较。|
|[运算符<（对）（STL/CLR）](#op_lt)|对小于比较。|
|[运算符\<= （对） （STL/CLR）](#op_lteq)|对小于或相等的比较。|
|[运算符>（对）（STL/CLR）](#op_gt)|对大于比较。|
|[运算符>= （对） （STL/CLR）](#op_gteq)|大于或等于比较的对。|

|函数|说明|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|从一对值制作一对。|

## <a name="members"></a>成员

## <a name="pair-stlclr"></a><a name="pair"></a>对（STL/CLR）

模板类描述环绕一对值的对象。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>参数

*Value1*<br/>
第一个包装值的类型。

*Value2*<br/>
第二个包装值的类型。

## <a name="members"></a>成员

|类型定义|说明|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|第一个包装值的类型。|
|[pair::second_type (STL/CLR)](#second_type)|第二个包装值的类型。|

|成员对象|说明|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|第一个存储值。|
|[pair::second (STL/CLR)](#second)|第二个存储值。|

|成员函数|说明|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|构造对对象。|
|[pair::swap (STL/CLR)](#swap)|交换两对的内容。|

|操作员|说明|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|替换存储的值对。|

## <a name="remarks"></a>备注

对象存储一对值。 使用此模板类将两个值合并到单个对象中。 此外，对象（`cliext::pair`此处描述）仅存储托管类型;因此，该对象（此处描述）仅存储托管类型。以存储一对非托管类型使用`std::pair`，在 中`<utility>`声明。

## <a name="pairfirst-stlclr"></a><a name="first"></a>对：第一（STL/CLR）

第一个包装值。

### <a name="syntax"></a>语法

```cpp
Value1 first;
```

### <a name="remarks"></a>备注

对象存储第一个包装值。

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

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>对：：first_type（STL/CLR）

第一个包装值的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>备注

类型是模板参数*Value1*的同义词。

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

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>对：：运算符*（STL/CLR）

替换存储的值对。

### <a name="syntax"></a>语法

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*对*<br/>
要复制的配对。

### <a name="remarks"></a>备注

成员运算符*将右侧*复制到对象，然后返回`*this`。 使用它将存储的值对替换为*右侧*存储的值对的副本。

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

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>对：:p航空（STL/CLR）

构造对对象。

### <a name="syntax"></a>语法

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>参数

*对*<br/>
要存储的对。

*val1*<br/>
要存储的第一个值。

*瓦尔2*<br/>
要存储的第二个值。

### <a name="remarks"></a>备注

构造函数：

`pair();`

使用默认构造值初始化存储的对。

构造函数：

`pair(pair<Value1, Value2>% right);`

初始化存储的对与`right.`[对：：第一（STL/CLR）](../dotnet/pair-first-stl-clr.md)和`right.`[对：秒（STL/CLR）。](../dotnet/pair-second-stl-clr.md)

`pair(pair<Value1, Value2>^ right);`

初始化存储的对与`right->`[对：：第一（STL/CLR）](../dotnet/pair-first-stl-clr.md)和`right>`[对：秒（STL/CLR）。](../dotnet/pair-second-stl-clr.md)

构造函数：

`pair(Value1 val1, Value2 val2);`

用*val1*和*val2*初始化存储的对。

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

## <a name="pairsecond-stlclr"></a><a name="second"></a>对：秒（STL/CLR）

第二个包装值。

### <a name="syntax"></a>语法

```cpp
Value2 second;
```

### <a name="remarks"></a>备注

对象存储第二个包装值。

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

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>对：：second_type（STL/CLR）

第二个包装值的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>备注

类型是模板参数*Value2*的同义词。

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

## <a name="pairswap-stlclr"></a><a name="swap"></a>对：交换（STL/CLR）

交换两对的内容。

### <a name="syntax"></a>语法

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*对*<br/>
配对以交换内容。

### <a name="remarks"></a>备注

成员函数交换*和*之间的`*this`存储的值对 。

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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair（STL/CLR）

从一`pair`对值制作 。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>参数

*Value1*<br/>
第一个包装值的类型。

*Value2*<br/>
第二个包装值的类型。

*第一*<br/>
要换行的第一个值。

*第二*<br/>
要换行的第二个值。

### <a name="remarks"></a>备注

此模板函数返回 `pair<Value1, Value2>(first, second)`。 使用它从一`pair<Value1, Value2>`对值构造对象。

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

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>运算符！* （对） （STL/CLR）

对不相等的比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左对。

*对*<br/>
要比较的右对。

### <a name="remarks"></a>备注

运算符函数返回`!(left == right)`。 使用它来测试当按元素比较两对时，*左的*排序是否与*右侧*相同。

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>运算符&lt;（对）（STL/CLR）

对小于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左对。

*对*<br/>
要比较的右对。

### <a name="remarks"></a>备注

运算符函数`left.first <``right.first || !(right.first <``left.first &&``left.second <`返回`right.second`。 使用它来测试当按元素比较两对时，*左是否*按*右前*排列。

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>运算符&lt;= （对） （STL/CLR）

对小于或相等的比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左对。

*对*<br/>
要比较的右对。

### <a name="remarks"></a>备注

运算符函数返回`!(right < left)`。 使用它来测试在按元素比较两对时，*是否*未*在右后右*排序。

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

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>运算符* （对） （STL/CLR）

对相等的比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左对。

*对*<br/>
要比较的右对。

### <a name="remarks"></a>备注

运算符`left.first ==``right.first &&``left.second ==``right.second`函数返回 。 使用它来测试当按元素比较两对时，*左的*排序是否与*右侧*相同。

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>运算符&gt;（对）（STL/CLR）

对大于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左对。

*对*<br/>
要比较的右对。

### <a name="remarks"></a>备注

运算符函数返回`right``<``left`。 使用它来测试在按元素比较两对时 *，左是否*按*右*顺序排列。

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>运算符&gt;= （对） （STL/CLR）

大于或等于比较的对。

### <a name="syntax"></a>语法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左对。

*对*<br/>
要比较的右对。

### <a name="remarks"></a>备注

运算符函数返回`!(left < right)`。 使用它来测试在按元素比较两*对之前是否*未对*左侧*进行排序。

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
