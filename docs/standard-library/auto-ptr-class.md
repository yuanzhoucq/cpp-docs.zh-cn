---
title: auto_ptr 类
ms.date: 11/04/2016
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
ms.openlocfilehash: 1f2c8cce234910fbf69a35c8f8ef2fb0fe2a41c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203867"
---
# <a name="auto_ptr-class"></a>auto_ptr 类

在资源周围包装智能指针，确保在块失去控制权时自动销毁该资源。

功能更强大的 `unique_ptr` 类可取代 `auto_ptr`。 有关详细信息，请参阅 [unique_ptr 类](../standard-library/unique-ptr-class.md)。

有关 `throw()` 和异常处理的详细信息，请参阅[异常规范（引发）](../cpp/exception-specifications-throw-cpp.md)。

## <a name="syntax"></a>语法

```cpp
class auto_ptr {
    typedef Type element_type;
    explicit auto_ptr(Type* ptr = 0) throw();
    auto_ptr(auto_ptr<Type>& right) throw()
        ;
    template <class Other>
    operator auto_ptr<Other>() throw();
    template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
    template <class Other>
    auto_ptr(auto_ptr<Other>& right);
    auto_ptr<Type>& operator=(auto_ptr<Type>& right);
    ~auto_ptr();
    Type& operator*() const throw();
    Type * operator->()const throw();
    Type *get() const throw();
    Type *release()throw();
    void reset(Type* ptr = 0);
};
```

### <a name="parameters"></a>参数

*然后*\
可从中获取现有资源的 `auto_ptr`。

*ptr*\
指定用于替换已存储指针的指针。

## <a name="remarks"></a>备注

类模板将一个名为的智能指针描述 `auto_ptr` 为分配的对象。 指针必须为 null 或指定所分配的对象 **`new`** 。 如果 `auto_ptr` 的存储值已分配给其他对象，则它将转移所有权。 （它在使用 null 指针进行传输后替换存储的值）。的析构函数将 `auto_ptr<Type>` 删除已分配的对象。 `auto_ptr<Type>` 可确保在块失去控制权时（甚至在已引发异常的情况下）自动删除已分配的对象。 不应构造两个拥有相同对象的 `auto_ptr<Type>` 对象。

可以将 `auto_ptr<Type>` 对象作为函数调用的参数按值传递。 `auto_ptr` 不能是任何标准库容器的元素。 你无法使用 C++ 标准库容器可靠地管理一系列 `auto_ptr<Type>` 对象。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[auto_ptr](#auto_ptr)|`auto_ptr` 类型的对象的构造函数。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[element_type](#element_type)|类型是模板参数 `Type` 的同义词。|

### <a name="functions"></a>函数

|||
|-|-|
|[get](#get)|该成员函数将返回存储的指针 `myptr`。|
|[拆卸](#release)|该成员将存储的指针 `myptr` 替换为 Null 指针，并返回以前存储的指针。|
|[reset](#reset)|此成员函数对表达式 `delete myptr` 进行求值，但仅在存储的指针值 `myptr` 因函数调用而更改时进行。 然后它将存储的指针替换为 *ptr*。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#op_eq)|一个赋值运算符，用于将所有权从一个 `auto_ptr` 对象转移到到其他对象。|
|[操作员](#op_star)|`auto_ptr` 类型的对象的取消引用运算符。|
|[operator->](#op_arrow)|允许成员访问的运算符。|
|[运算符 auto_ptr\<Other>](#op_auto_ptr_lt_other_gt)|将某种 `auto_ptr` 强制转换为另一种 `auto_ptr`。|
|[运算符 auto_ptr_ref\<Other>](#op_auto_ptr_ref_lt_other_gt)|将 `auto_ptr` 强制转换为 `auto_ptr_ref`。|

### <a name="auto_ptr"></a><a name="auto_ptr"></a>auto_ptr

`auto_ptr` 类型的对象的构造函数。

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

#### <a name="parameters"></a>参数

*ptr*\
指向 `auto_ptr` 封装的对象的指针。

*然后*\
由构造函数复制的 `auto_ptr` 对象。

#### <a name="remarks"></a>备注

第一个构造函数在中存储*ptr* `myptr` ，并将存储的指针存储到所分配的对象。 第二个构造函数通过存储*权限*来传输存储在*右侧*的指针的所有权。 [版本](#release) `myptr` 。

第三个构造函数的行为与第二个相同，只不过它会存储 `right` 。 `ref`. `release`在中 `myptr` ，其中 `ref` 是存储在中的引用 `right` 。

如果指向的指针 `Other` 可以隐式转换为指向的指针，则模板构造函数的行为与第二个构造函数的行为相同 `Type` 。

#### <a name="example"></a>示例

```cpp
// auto_ptr_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

void function ( auto_ptr<Int> &pi )
{
   ++( *pi );
   auto_ptr<Int> pi2( pi );
   ++( *pi2 );
   pi = pi2;
}

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   cout << pi->x << endl;
   function( pi );
   cout << pi->x << endl;
}
```

```Output
Constructing 00311AF8
5
7
Destructing 00311AF8
```

### <a name="element_type"></a><a name="element_type"></a>element_type

类型是模板参数 `Type` 的同义词。

```cpp
typedef Type element  _type;
```

### <a name="get"></a><a name="get"></a>获取

该成员函数将返回存储的指针 `myptr`。

```cpp
Type *get() const throw();
```

#### <a name="return-value"></a>返回值

存储的指针 `myptr` 。

#### <a name="example"></a>示例

```cpp
// auto_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      x = i;
      cout << "Constructing " << ( void* )this  << " Value: " << x << endl;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << " Value: " << x << endl;
   };

   int x;

};

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   pi.reset( new Int( 6 ) );
   Int* pi2 = pi.get ( );
   Int* pi3 = pi.release ( );
   if (pi2 == pi3)
      cout << "pi2 == pi3" << endl;
   delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="operator"></a><a name="op_eq"></a>operator =

一个赋值运算符，用于将所有权从一个 `auto_ptr` 对象转移到到其他对象。

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>参数

*然后*\
一个 `auto_ptr` 类型的对象。

#### <a name="return-value"></a>返回值

对类型为 `auto_ptr<Type>` 的对象的引用。

#### <a name="remarks"></a>备注

赋值将计算表达式的值 `delete myptr` ，但仅在存储的指针由于赋值而更改时才会 `myptr` 发生。 然后，它会通过存储*权限*来转移存储在*右侧*的指针的所有权。[版本](#release) `myptr` 。 函数返回__ \* this__。

#### <a name="example"></a>示例

有关使用成员运算符的示例，请参阅[auto_ptr](#auto_ptr)。

### <a name="operator"></a><a name="op_star"></a>操作员

`auto_ptr` 类型的对象的取消引用运算符。

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>返回值

对指针所拥有的类型的对象的引用 `Type` 。

#### <a name="remarks"></a>备注

间接运算符返回 `*`[get](#get)。 因此，存储的指针不能为空。

#### <a name="example"></a>示例

有关如何使用成员函数的示例，请参阅[auto_ptr](#auto_ptr)。

### <a name="operator-gt"></a><a name="op_arrow"></a>操作员&gt;

允许成员访问的运算符。

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>返回值

拥有的对象的成员 `auto_ptr` 。

#### <a name="remarks"></a>备注

选择运算符返回[get](#get) `( )` ，以便表达式*ap* ->  **成员**的行为与（ *ap*）相同。 **get**（））->**成员**，其中， *ap*是类的对象 `auto_ptr` \< **Type**> 。 因此，存储的指针不能为 null，并且 `Type` 必须是包含成员的类、结构或联合类型 `member` 。

#### <a name="example"></a>示例

有关如何使用成员函数的示例，请参阅[auto_ptr](#auto_ptr)。

### <a name="operator-auto_ptrltothergt"></a><a name="op_auto_ptr_lt_other_gt"></a>运算符 auto_ptr &lt; 其他&gt;

将某种 `auto_ptr` 强制转换为另一种 `auto_ptr`。

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>返回值

类型强制转换运算符返回 `auto_ptr` \< **Other**> （ ** \* this**）。

#### <a name="example"></a>示例

```cpp
// auto_ptr_op_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;
int main()
{
   auto_ptr<int> pi ( new int( 5 ) );
   auto_ptr<const int> pc = ( auto_ptr<const int> )pi;
}
```

### <a name="operator-auto_ptr_refltothergt"></a><a name="op_auto_ptr_ref_lt_other_gt"></a>运算符 auto_ptr_ref &lt; 其他&gt;

将 `auto_ptr` 强制转换为 `auto_ptr_ref`。

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>返回值

类型强制转换运算符返回**auto_ptr_ref** \< **Other**> （ ** \* this**）。

#### <a name="example"></a>示例

```cpp
// auto_ptr_op_auto_ptr_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class C {
public:
    C(int _i) : m_i(_i) {
    }
    ~C() {
        cout << "~C:  " << m_i << "\n";
    }
    C &operator =(const int &x) {
        m_i = x;
        return *this;
    }
    int m_i;
};
void f(auto_ptr<C> arg) {
};
int main()
{
    const auto_ptr<C> ciap(new C(1));
    auto_ptr<C> iap(new C(2));

    // Error: this implies transfer of ownership of iap's pointer
    // f(ciap);
    f(iap); // compiles, but gives up ownership of pointer

            // here, iap owns a destroyed pointer so the following is bad:
            // *iap = 5; // BOOM

    cout << "main exiting\n";
}
```

```Output
~C:  2
main exiting
~C:  1
```

### <a name="release"></a><a name="release"></a>拆卸

该成员将存储的指针 `myptr` 替换为 Null 指针，并返回以前存储的指针。

```cpp
Type *release() throw();
```

#### <a name="return-value"></a>返回值

以前存储的指针。

#### <a name="remarks"></a>备注

该成员将存储的指针 `myptr` 替换为 Null 指针，并返回以前存储的指针。

#### <a name="example"></a>示例

```cpp
// auto_ptr_release.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int() {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;

};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="reset"></a><a name="reset"></a>&

成员函数计算表达式的 `delete myptr` 值，但仅在存储的指针值因函数调用而更改时才计算 `myptr` 。 然后它将存储的指针替换为 `ptr`。

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>参数

*ptr*\
指定用于替换已存储指针的指针 `myptr` 。

#### <a name="example"></a>示例

```cpp
// auto_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int()
    {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;
};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="see-also"></a>另请参阅

[unique_ptr 类](../standard-library/unique-ptr-class.md)
