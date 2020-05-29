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
ms.openlocfilehash: 2d06a92fea9a702633216e3244879687b66f97d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208723"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

包含 STL/CLR 标头 `<cliext/functional>` 来定义多个模板类以及相关的模板委托和函数。

## <a name="syntax"></a>语法

```
#include <functional>
```

## <a name="requirements"></a>要求

**标头：** \<cliext/功能 >

**命名空间：** cliext

## <a name="declarations"></a>声明

|委托|说明|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|双参数委托。|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|返回**void**的双参数委托。|
|[unary_delegate (STL/CLR)](#unary_delegate)|单参数委托。|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|返回**void**的单参数委托。|

|类|说明|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|函子对双参数函子进行反运算。|
|[binder1st (STL/CLR)](#binder1st)|函子用于将第一个参数绑定到两个参数函子。|
|[binder2nd (STL/CLR)](#binder2nd)|函子用于将第二个参数绑定到两个参数函子。|
|[divides (STL/CLR)](#divides)|除函子。|
|[equal_to (STL/CLR)](#equal_to)|相等比较函子。|
|[greater (STL/CLR)](#greater)|比较函子。|
|[greater_equal (STL/CLR)](#greater_equal)|大于或等于比较函子。|
|[less (STL/CLR)](#less)|比较函子比较。|
|[less_equal (STL/CLR)](#less_equal)|比较函子。|
|[logical_and (STL/CLR)](#logical_and)|Logical 和函子。|
|[logical_not (STL/CLR)](#logical_not)|逻辑非函子。|
|[logical_or (STL/CLR)](#logical_or)|逻辑或函子。|
|[minus (STL/CLR)](#minus)|减去函子。|
|[modulus (STL/CLR)](#modulus)|取模函子。|
|[multiplies (STL/CLR)](#multiplies)|将函子相乘。|
|[negate (STL/CLR)](#negate)|函子返回其反参数。|
|[not_equal_to (STL/CLR)](#not_equal_to)|不等于比较函子。|
|[plus (STL/CLR)](#plus)|添加函子。|
|[unary_negate (STL/CLR)](#unary_negate)|函子对单参数函子进行反运算。|

|函数|说明|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|为参数和函子生成 binder1st。|
|[bind2nd (STL/CLR)](#bind2nd)|为参数和函子生成 binder2nd。|
|[not1 (STL/CLR)](#not1)|生成函子的 unary_negate。|
|[not2 (STL/CLR)](#not2)|生成函子的 binary_negate。|

## <a name="members"></a>成员

## <a name="binary_delegate-stlclr"></a><a name="binary_delegate"></a>binary_delegate （STL/CLR）

Genereic 类描述了一个双参数委托。 使用它可以指定委托的参数和返回类型。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>parameters

*Arg1*<br/>
第一个参数的类型。

*Arg2*<br/>
第二个参数的类型。

*结果*<br/>
返回类型。

### <a name="remarks"></a>备注

Genereic 委托描述了一个双参数函数。

请注意，对于：

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

`Fun1` 和 `Fun2` 类型是同义词，而对于：

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

它们的类型不同。

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

## <a name="binary_delegate_noreturn-stlclr"></a><a name="binary_delegate_noreturn"></a>binary_delegate_noreturn （STL/CLR）

Genereic 类描述返回**void**的两参数委托。 使用它以参数的形式指定委托。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>parameters

*Arg1*<br/>
第一个参数的类型。

*Arg2*<br/>
第二个参数的类型。

### <a name="remarks"></a>备注

Genereic 委托介绍了返回**void**的两参数函数。

请注意，对于：

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

`Fun1` 和 `Fun2` 类型是同义词，而对于：

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

它们的类型不同。

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

## <a name="binary_negate-stlclr"></a><a name="binary_negate"></a>binary_negate （STL/CLR）

此模板类描述了一个函子，该模板在调用时返回其存储的双参数函子的逻辑。 使用它以存储的函子指定函数对象。

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

#### <a name="parameters"></a>parameters

*趣味*<br/>
存储的函子的类型。

## <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|
|stored_function_type|函子的类型。|

|成员|说明|
|------------|-----------------|
|binary_negate|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type ^ （）|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子，用于存储另一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它返回使用两个参数调用的存储的函子的逻辑。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="bind1st-stlclr"></a><a name="bind1st"></a>bind1st （STL/CLR）

生成参数和函子的 `binder1st`。

### <a name="syntax"></a>语法

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>模板参数

*与我们联系*<br/>
自变量类型。

*趣味*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*函子*<br/>
要包装的函子。

*left*<br/>
要换行的第一个参数。

### <a name="remarks"></a>备注

此模板函数返回[binder1st （STL/CLR）](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`。 使用该方法可以方便地将两个参数的函子和其第一个参数包装在一个参数函子中，后者使用第二个参数调用它。

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

## <a name="bind2nd-stlclr"></a><a name="bind2nd"></a>bind2nd （STL/CLR）

生成参数和函子的 `binder2nd`。

### <a name="syntax"></a>语法

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>模板参数

*与我们联系*<br/>
自变量类型。

*趣味*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*函子*<br/>
要包装的函子。

right<br/>
要换行的第二个参数。

### <a name="remarks"></a>备注

此模板函数返回[binder2nd （STL/CLR）](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`。 使用该方法可以方便地将两个参数的函子和它的第二个参数封装在一个参数函子中，该参数使用第一个参数调用它。

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

## <a name="binder1st-stlclr"></a><a name="binder1st"></a>binder1st （STL/CLR）

此模板类描述了一个参数函子，在调用它时，它将返回其存储的双参数函子，并将其存储的第一个参数和提供的第二个参数一起调用。 使用它以存储的函子指定函数对象。

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

#### <a name="parameters"></a>parameters

*趣味*<br/>
存储的函子的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|
|stored_function_type|函子的类型。|

|成员|说明|
|------------|-----------------|
|binder1st|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type ^ （）|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个参数函子，用于存储两个参数函子和第一个参数。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它返回使用存储的第一个参数和提供的第二个参数调用存储的函子的结果。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="binder2nd-stlclr"></a><a name="binder2nd"></a>binder2nd （STL/CLR）

此模板类描述了一个参数函子，在调用它时，将返回其存储的双参数函子，该参数使用提供的第一个参数及其存储的第二个参数来调用。 使用它以存储的函子指定函数对象。

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

#### <a name="parameters"></a>parameters

*趣味*<br/>
存储的函子的类型。

## <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|
|stored_function_type|函子的类型。|

|成员|说明|
|------------|-----------------|
|binder2nd|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type ^ （）|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个参数函子，用于存储两个参数函子和第二个参数。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它返回使用提供的第一个参数和存储的第二个参数调用存储的函子的结果。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="divides-stlclr"></a><a name="divides"></a>相除（STL/CLR）

此模板类描述了一个函子，该模板在调用时返回第一个参数除以第二个参数。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|divides|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type ^ （）|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它将返回第一个自变量除以第二个参数。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="equal_to-stlclr"></a><a name="equal_to"></a>equal_to （STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数等于第二个参数时才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|equal_to|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|operator delegate_type ^ （）|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，仅当第一个参数等于第二个参数时，它才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="greater-stlclr"></a><a name="greater"></a>大于（STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数大于第二个参数时才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|greater|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，仅当第一个参数大于第二个参数时，它才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="greater_equal-stlclr"></a><a name="greater_equal"></a>greater_equal （STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数大于或等于第二个参数时，才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|greater_equal|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，仅当第一个参数大于或等于第二个参数时，它才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="less-stlclr"></a><a name="less"></a>小于（STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数小于第二个参数时才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|less|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，仅当第一个参数小于第二个参数时，它才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="less_equal-stlclr"></a><a name="less_equal"></a>less_equal （STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数小于或等于第二个参数时，才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|less_equal|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，仅当第一个参数小于或等于第二个参数时，它才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="logical_and-stlclr"></a><a name="logical_and"></a>logical_and （STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数和第二个测试都为 true 时，才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|logical_and|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，仅当第一个参数和第二个测试都为 true 时，它才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="logical_not-stlclr"></a><a name="logical_not"></a>logical_not （STL/CLR）

此模板类描述了一个函子，该方法在调用时仅在其参数测试为 false 时返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|argument_type|函子参数的类型。|
|delegate_type|泛型委托的类型。|
|result_type|函子结果的类型。|

|成员|说明|
|------------|-----------------|
|logical_not|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了单参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它仅在其参数测试为 false 时返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="logical_or-stlclr"></a><a name="logical_or"></a>logical_or （STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数或第二个测试为 true 时才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|logical_or|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，只有第一个参数或第二个测试为 true 时才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="minus-stlclr"></a><a name="minus"></a>减号（STL/CLR）

此模板类描述了一个函子，该模板在调用时返回第一个参数减去第二个参数。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|minus|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它将返回第一个参数减去第二个参数。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="modulus-stlclr"></a><a name="modulus"></a>取模（STL/CLR）

此模板类描述了一个函子，该模板在调用时返回第一个第一个参数取模。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|modulus|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它将返回第二个参数模数。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="multiplies-stlclr"></a><a name="multiplies"></a>乘法（STL/CLR）

此模板类描述了一个函子，该模板在调用时将返回第二个参数的第二个参数。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|multiplies|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它将返回第二个参数的时间。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="negate-stlclr"></a><a name="negate"></a>否定（STL/CLR）

此模板类描述了一个函子，该模板在调用时返回其反参数。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|argument_type|函子参数的类型。|
|delegate_type|泛型委托的类型。|
|result_type|函子结果的类型。|

|成员|说明|
|------------|-----------------|
|negate|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了单参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它将返回其自变量。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="not_equal_to-stlclr"></a><a name="not_equal_to"></a>not_equal_to （STL/CLR）

此模板类描述了一个函子，在调用后，仅当第一个参数不等于第二个参数时才返回 true。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|not_equal_to|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，仅当第一个参数不等于第二个参数时，它才返回 true。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="not1-stlclr"></a><a name="not1"></a>not1 （STL/CLR）

生成函子的 `unary_negate`。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>模板参数

*趣味*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*函子*<br/>
要包装的函子。

### <a name="remarks"></a>备注

模板函数返回[unary_negate （STL/CLR）](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`。 使用该方法可以方便地在传递其逻辑 NOT 的函子中包装单参数函子。

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

## <a name="not2-stlclr"></a><a name="not2"></a>not2 （STL/CLR）

生成函子的 `binary_negate`。

### <a name="syntax"></a>语法

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>模板参数

*趣味*<br/>
函子的类型。

#### <a name="function-parameters"></a>函数参数

*函子*<br/>
要包装的函子。

### <a name="remarks"></a>备注

模板函数返回[binary_negate （STL/CLR）](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`。 使用该方法可以方便地将两个参数函子在函子中，用于传递其逻辑。

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

## <a name="plus-stlclr"></a><a name="plus"></a>plus （STL/CLR）

此模板类描述了一个函子，该模板在调用时返回第一个参数加上第二个参数。 使用它以其参数类型指定函数对象。

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

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
参数和返回值的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|delegate_type|泛型委托的类型。|
|first_argument_type|函子第一个参数的类型。|
|result_type|函子结果的类型。|
|second_argument_type|函子第二个参数的类型。|

|成员|说明|
|------------|-----------------|
|加|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|操作员 delegate_type ^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个双参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它将返回第一个参数加上第二个参数。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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

## <a name="unary_delegate-stlclr"></a><a name="unary_delegate"></a>unary_delegate （STL/CLR）

Genereic 类描述了单参数委托。 使用它可以指定委托的参数和返回类型。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
自变量类型。

*结果*<br/>
返回类型。

### <a name="remarks"></a>备注

Genereic 委托说明了单参数函数。

请注意，对于：

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

`Fun1` 和 `Fun2` 类型是同义词，而对于：

`delegate int Fun1(int);`

`delegate int Fun2(int);`

它们的类型不同。

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

## <a name="unary_delegate_noreturn-stlclr"></a><a name="unary_delegate_noreturn"></a>unary_delegate_noreturn （STL/CLR）

Genereic 类描述返回**void**的单参数委托。 使用它以参数类型指定委托。

### <a name="syntax"></a>语法

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>parameters

*与我们联系*<br/>
自变量类型。

### <a name="remarks"></a>备注

Genereic 委托介绍了返回**void**的单参数函数。

请注意，对于：

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

`Fun1` 和 `Fun2` 类型是同义词，而对于：

`delegate void Fun1(int);`

`delegate void Fun2(int);`

它们的类型不同。

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

## <a name="unary_negate-stlclr"></a><a name="unary_negate"></a>unary_negate （STL/CLR）

此模板类描述了一个函子，该模板在调用时返回其存储的单参数函子的逻辑。 使用它以存储的函子指定函数对象。

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

#### <a name="parameters"></a>parameters

*趣味*<br/>
存储的函子的类型。

### <a name="member-functions"></a>成员函数

|类型定义|说明|
|---------------------|-----------------|
|argument_type|函子参数的类型。|
|delegate_type|泛型委托的类型。|
|result_type|函子结果的类型。|

|成员|说明|
|------------|-----------------|
|unary_negate|构造函子。|

|操作员|说明|
|--------------|-----------------|
|operator()|计算所需的函数。|
|delegate_type^|将函子转换为委托。|

### <a name="remarks"></a>备注

此模板类描述了一个参数函子，用于存储另一个参数函子。 它定义成员运算符 `operator()` 以便在将对象作为函数调用时，它返回使用参数调用的存储的函子的逻辑。

您还可以将该对象作为其类型 `delegate_type^` 的函数参数传递，并进行相应的转换。

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
