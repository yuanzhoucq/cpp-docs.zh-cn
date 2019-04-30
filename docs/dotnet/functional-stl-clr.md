---
title: functional (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
ms.openlocfilehash: f4a99ea972c6d2ea9b9721664cc75dec257fd7b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393748"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

包含 STL/CLR 标头`<cliext/functional>`来定义多个模板类和相关的模板委托和函数。

## <a name="syntax"></a>语法

```
#include <functional>
```

## <a name="requirements"></a>要求

**标头：** \<cliext/功能 >

**Namespace:** cliext

## <a name="declarations"></a>声明

|委托|描述|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|两个参数的委托。|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|返回两个参数委托**void**。|
|[unary_delegate (STL/CLR)](#unary_delegate)|单参数委托。|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|返回的单参数委托**void**。|

|类|描述|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|要求反的两个参数函子的仿函数。|
|[binder1st (STL/CLR)](#binder1st)|若要将第一个参数绑定到两个参数函子的仿函数。|
|[binder2nd (STL/CLR)](#binder2nd)|若要将第二个参数绑定到两个参数函子的仿函数。|
|[divides (STL/CLR)](#divides)|除仿函数。|
|[equal_to (STL/CLR)](#equal_to)|相等比较函子。|
|[greater (STL/CLR)](#greater)|大于比较函子。|
|[greater_equal (STL/CLR)](#greater_equal)|大于或等于比较函子。|
|[less (STL/CLR)](#less)|小于比较函子。|
|[less_equal (STL/CLR)](#less_equal)|小于或等于比较函子。|
|[logical_and (STL/CLR)](#logical_and)|逻辑 AND 仿函数。|
|[logical_not (STL/CLR)](#logical_not)|逻辑不仿函数。|
|[logical_or (STL/CLR)](#logical_or)|逻辑 OR 仿函数。|
|[minus (STL/CLR)](#minus)|减去仿函数。|
|[modulus (STL/CLR)](#modulus)|取模仿函数。|
|[multiplies (STL/CLR)](#multiplies)|Multiply 仿函数。|
|[negate (STL/CLR)](#negate)|若要返回其参数求反的仿函数。|
|[not_equal_to (STL/CLR)](#not_equal_to)|不等于比较函子。|
|[plus (STL/CLR)](#plus)|添加仿函数。|
|[unary_negate (STL/CLR)](#unary_negate)|要求反的单参数函子的仿函数。|

|函数|描述|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|生成自变量和函子 binder1st。|
|[bind2nd (STL/CLR)](#bind2nd)|生成自变量和函子 binder2nd。|
|[not1 (STL/CLR)](#not1)|生成伪函数 unary_negate。|
|[not2 (STL/CLR)](#not2)|生成伪函数 binary_negate。|

## <a name="members"></a>成员

## <a name="binary_delegate"></a> binary_delegate (STL/CLR)

Genereic 类描述双参数委托。 使用它指定在其参数和返回类型的方面的委托。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>参数

*Arg1*<br/>
第一个参数的类型。

*Arg2*<br/>
第二个参数的类型。

*结果*<br/>
返回类型。

### <a name="remarks"></a>备注

Genereic 委托描述两个参数函数。

请注意，对于：

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

类型`Fun1`和`Fun2`是同义词，而为：

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

它们不是相同的类型。

### <a name="example"></a>示例

```cpp
// cliext_binary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

bool key_compare(wchar_t left, wchar_t right)
    {
    return (left < right);
    }

typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="binary_delegate_noreturn"></a> binary_delegate_noreturn (STL/CLR)

Genereic 类将描述返回的两个参数委托**void**。 使用它指定根据其参数的委托。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>参数

*Arg1*<br/>
第一个参数的类型。

*Arg2*<br/>
第二个参数的类型。

### <a name="remarks"></a>备注

Genereic 委托介绍返回的两个参数函数**void**。

请注意，对于：

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

类型`Fun1`和`Fun2`是同义词，而为：

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

它们不是相同的类型。

### <a name="example"></a>示例

```cpp
// cliext_binary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void key_compare(wchar_t left, wchar_t right)
    {
    System::Console::WriteLine("compare({0}, {1}) = {2}",
        left, right, left < right);
    }

typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    kcomp(L'a', L'a');
    kcomp(L'a', L'b');
    kcomp(L'b', L'a');
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(a, a) = False
compare(a, b) = True
compare(b, a) = False
```

## <a name="binary_negate"></a> binary_negate (STL/CLR)

此模板类描述某个函数，调用时，返回的逻辑不其存储的两个参数函子。 使用它指定根据其存储的函子的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    ref class binary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    explicit binary_negate(Fun% functor);
    binary_negate(binary_negate<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*Fun*<br/>
存储函子的类型。

## <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|
|stored_function_type|函子的类型。|

|成员|描述|
|------------|-----------------|
|binary_negate|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type^()|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述存储其他两个参数函子的两个参数仿函数。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回逻辑的存储函子的不调用具有两个参数。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_binary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="bind1st"></a> bind1st (STL/CLR)

生成`binder1st`自变量和函数。

### <a name="syntax"></a>语法

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>模板参数

*arg*<br/>
自变量类型。

*Fun*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*functor*<br/>
要包装仿函数。

*left*<br/>
要包装的第一个参数。

### <a name="remarks"></a>备注

模板函数返回[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`。 您将其用作中调用的第二个参数的单参数伪函数包装两个参数函子和其第一个参数的简便方法。

### <a name="example"></a>示例

```cpp
// cliext_bind1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="bind2nd"></a> bind2nd (STL/CLR)

生成`binder2nd`自变量和函数。

### <a name="syntax"></a>语法

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>模板参数

*arg*<br/>
自变量类型。

*Fun*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*functor*<br/>
要包装仿函数。

*right*<br/>
要包装的第二个参数。

### <a name="remarks"></a>备注

模板函数返回[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`。 您将其用作中与第一个参数调用某个单参数函数包装两个参数函子和第二个参数的简便方法。

### <a name="example"></a>示例

```cpp
// cliext_bind2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="binder1st"></a> binder1st (STL/CLR)

此模板类描述单参数仿函数，调用时，返回其存储的第一个参数而提供的第二个参数调用其存储两个参数仿函数。 使用它指定根据其存储的函子的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    ref class binder1st
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        second_argument_type, result_type>
        delegate_type;

    binder1st(Fun% functor, first_argument_type left);
    binder1st(binder1st<Arg>% right);

    result_type operator()(second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*Fun*<br/>
存储函子的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|
|stored_function_type|函子的类型。|

|成员|描述|
|------------|-----------------|
|binder1st|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type^()|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述存储两个参数函子和第一个参数的单参数仿函数。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回调用存储的第一个参数而提供的第二个参数的存储函子的结果。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_binder1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="binder2nd"></a> binder2nd (STL/CLR)

此模板类描述单参数仿函数，调用时，返回使用提供的第一个自变量和其存储的第二个参数调用其存储两个参数仿函数。 使用它指定根据其存储的函子的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    ref class binder2nd
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        first_argument_type, result_type>
        delegate_type;

    binder2nd(Fun% functor, second_argument_type left);
    binder2nd(binder2nd<Arg>% right);

    result_type operator()(first_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*Fun*<br/>
存储函子的类型。

## <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|
|stored_function_type|函子的类型。|

|成员|描述|
|------------|-----------------|
|binder2nd|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type^()|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述单参数仿函数，存储的两个参数伪函数和第二个参数。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回调用提供的第一个参数而存储的第二个参数的存储函子的结果。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_binder2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="divides"></a> divides (STL/CLR)

此模板类描述某个函数，调用时，返回第一个参数除以第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class divides
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    divides();
    divides(divides<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|divides|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type^()|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回第一个参数除以第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_divides.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::divides<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 3
```

## <a name="equal_to"></a> equal_to (STL/CLR)

此模板类描述某个函数，调用时，返回 true，仅当第一个参数等于第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    equal_to();
    equal_to(equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|equal_to|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type^()|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅第一个参数是否等于第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="greater"></a> 更高版本 (STL/CLR)

此模板类描述某个函数，调用时，返回 true，仅当第一个参数大于第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class greater
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater();
    greater(greater<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|greater|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅第一个参数是否大于第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_greater.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
1 0
```

## <a name="greater_equal"></a> greater_equal (STL/CLR)

此模板类描述某个函数，调用时，返回 true 仅第一个参数是否大于或等于第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class greater_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater_equal();
    greater_equal(greater_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|greater_equal|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅第一个参数是否大于或等于第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_greater_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="less"></a> 更少的 (STL/CLR)

此模板类描述某个函数，调用时，返回 true，仅当第一个参数小于第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class less
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less();
    less(less<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|less|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅第一个参数是否小于第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_less.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="less_equal"></a> less_equal (STL/CLR)

此模板类描述某个函数，调用时，返回 true 仅第一个参数是否小于或等于第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class less_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less_equal();
    less_equal(less_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|less_equal|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅第一个参数是否小于或等于第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_less_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
0 1
```

## <a name="logical_and"></a> logical_and (STL/CLR)

此模板类描述某个函数，调用时，返回 true，仅当第一个参数和第二个测试为 true。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class logical_and
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_and();
    logical_and(logical_and<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|logical_and|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅当第一个参数和第二个测试为 true。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_logical_and.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 1 0" and " 1 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_and<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
3 0
1 0
```

## <a name="logical_not"></a> logical_not (STL/CLR)

此模板类描述某个函数，调用时，返回 true，仅当任一参数测试为 false。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class logical_not
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    logical_not();
    logical_not(logical_not<Arg> %right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|argument_type|伪函数自变量的类型。|
|delegate_type|泛型委托的类型。|
|result_type|伪函数结果的类型。|

|成员|描述|
|------------|-----------------|
|logical_not|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述单参数仿函数。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅其参数如果测试为 false。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_logical_not.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::logical_not<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
0 1
```

## <a name="logical_or"></a> logical_or (STL/CLR)

此模板类描述某个函数，调用时，返回 true，仅当第一个参数或第二个测试为 true。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class logical_or
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_or();
    logical_or(logical_or<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|logical_or|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅当 true 的第一个参数或作为第二个测试。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_logical_or.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(0);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 2 0" and " 0 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_or<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
0 0
1 0
```

## <a name="minus"></a> 减 (STL/CLR)

此模板类描述某个函数，调用时，返回第一个参数减去第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class minus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    minus();
    minus(minus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|minus|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回第一个参数减去第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_minus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::minus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 2
```

## <a name="modulus"></a> modulus (STL/CLR)

此模板类描述某个函数，调用时，返回第二个模的第一个参数。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class modulus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    modulus();
    modulus(modulus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|modulus|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回第二个模的第一个参数。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_modulus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(2);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 2" and " 3 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::modulus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 2
3 1
1 0
```

## <a name="multiplies"></a> 相乘 (STL/CLR)

此模板类描述某个函数，调用时，返回第二个时间的第一个参数。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class multiplies
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    multiplies();
    multiplies(multiplies<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|multiplies|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回第二个时间的第一个参数。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_multiplies.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::multiplies<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
8 3
```

## <a name="negate"></a> negate (STL/CLR)

此模板类描述某个函数，调用时，返回其参数求反。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class negate
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    negate();
    negate(negate<Arg>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|argument_type|伪函数自变量的类型。|
|delegate_type|泛型委托的类型。|
|result_type|伪函数结果的类型。|

|成员|描述|
|------------|-----------------|
|negate|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述单参数仿函数。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回其参数求反。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(-3);
    Myvector c3(2, 0);

// display initial contents " 4 -3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::negate<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 -3
-4 3
```

## <a name="not_equal_to"></a> not_equal_to (STL/CLR)

此模板类描述某个函数，调用时，返回 true，仅当第一个参数不等于第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class not_equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    not_equal_to();
    not_equal_to(not_equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|not_equal_to|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回 true 仅第一个参数是否不等于第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_not_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="not1"></a> not1 (STL/CLR)

生成`unary_negate`函子的。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>模板参数

*Fun*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*functor*<br/>
要包装仿函数。

### <a name="remarks"></a>备注

模板函数返回[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`。 您将其用作方便地将某个单参数函数包装在仿函数，提供其逻辑非。

### <a name="example"></a>示例

```cpp
// cliext_not1.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```

## <a name="not2"></a> not2 (STL/CLR)

生成`binary_negate`函子的。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>模板参数

*Fun*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*functor*<br/>
要包装仿函数。

### <a name="remarks"></a>备注

模板函数返回[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`。 您将其用作中提供其逻辑非运算的伪函数包装两个参数函子的简便方法。

### <a name="example"></a>示例

```cpp
// cliext_not2.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="plus"></a> plus (STL/CLR)

此模板类描述某个函数，调用时，返回的第一个参数加上第二个。 使用它指定根据其自变量类型的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Arg>
    ref class plus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    plus();
    plus(plus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*arg*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子的第一个参数的类型。|
|result_type|伪函数结果的类型。|
|second_argument_type|函子的第二个参数的类型。|

|成员|描述|
|------------|-----------------|
|plus|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|运算符 delegate_type ^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述了两个参数函子。 它定义了成员运算符`operator()`以便作为函数调用时对象，它返回第一个参数加上第二个。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_plus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::plus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
6 4
```

## <a name="unary_delegate"></a> unary_delegate (STL/CLR)

Genereic 类描述单参数委托。 使用它指定在其参数和返回类型的方面的委托。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>参数

*arg*<br/>
自变量类型。

*结果*<br/>
返回类型。

### <a name="remarks"></a>备注

Genereic 委托描述单参数函数。

请注意，对于：

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

类型`Fun1`和`Fun2`是同义词，而为：

`delegate int Fun1(int);`

`delegate int Fun2(int);`

它们不是相同的类型。

### <a name="example"></a>示例

```cpp
// cliext_unary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

int hash_val(wchar_t val)
    {
    return ((val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate<wchar_t, int> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 5
hash(L'b') = 22
```

## <a name="unary_delegate_noreturn"></a> unary_delegate_noreturn (STL/CLR)

Genereic 类将描述返回的单参数委托**void**。 使用它指定根据其自变量类型的委托。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>参数

*arg*<br/>
自变量类型。

### <a name="remarks"></a>备注

Genereic 委托介绍返回的单参数函数**void**。

请注意，对于：

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

类型`Fun1`和`Fun2`是同义词，而为：

`delegate void Fun1(int);`

`delegate void Fun2(int);`

它们不是相同的类型。

### <a name="example"></a>示例

```cpp
// cliext_unary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void hash_val(wchar_t val)
    {
    System::Console::WriteLine("hash({0}) = {1}",
       val, (val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    myhash(L'a');
    myhash(L'b');
    return (0);
    }
```

```Output
hash(a) = 5
hash(b) = 22
```

## <a name="unary_negate"></a> unary_negate (STL/CLR)

此模板类描述某个函数，调用时，返回的逻辑不其存储的单参数函子。 使用它指定根据其存储的函子的函数对象。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    ref class unary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::argument_type argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    unary_negate(Fun% functor);
    unary_negate(unary_negate<Fun>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>参数

*Fun*<br/>
存储函子的类型。

### <a name="member-functions"></a>成员函数

|类型定义|描述|
|---------------------|-----------------|
|argument_type|伪函数自变量的类型。|
|delegate_type|泛型委托的类型。|
|result_type|伪函数结果的类型。|

|成员|描述|
|------------|-----------------|
|unary_negate|构造函子。|

|运算符|描述|
|--------------|-----------------|
|operator()|计算所需的函数。|
|delegate_type^|将强制转换为委托的仿函数。|

### <a name="remarks"></a>备注

此模板类描述存储另一个单参数函子的一个参数仿函数。 它定义了成员运算符`operator()`以便作为函数调用时对象，它将返回逻辑的存储函子的不使用参数调用。

你还可以传递该对象用作函数参数的类型是`delegate_type^`，适当地将其转换。

### <a name="example"></a>示例

```cpp
// cliext_unary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```