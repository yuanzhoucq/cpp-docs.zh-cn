---
title: "auto_ptr 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
dev_langs: C++
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 960da86c5ae3efa0cb50077becfb526000f71b4d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="autoptr-class"></a>auto_ptr 类
在资源周围包装智能指针，确保在块失去控制权时自动销毁该资源。  
  
 功能更强大的 `unique_ptr` 类可取代 `auto_ptr`。 有关详细信息，请参阅 [unique_ptr 类](../standard-library/unique-ptr-class.md)。  
  
 有关 `throw()` 和异常处理的详细信息，请参阅[异常规范（引发）](../cpp/exception-specifications-throw-cpp.md)。  
  
## <a name="syntax"></a>语法  
 ```   
class auto_ptr {
public:
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
#### <a name="parameters"></a>参数  
 `right`  
 可从中获取现有资源的 `auto_ptr`。  
  
 `ptr`  
 指定用于替换已存储指针的指针。  
  
## <a name="remarks"></a>备注  
 此模板类描述调用的智能指针`auto_ptr`，指向已分配对象。 指针必须为 Null 或指定 `new` 所分配的对象。 如果 `auto_ptr` 的存储值已分配给其他对象，则它将转移所有权。 （它在与 Null 指针进行转移后替换存储值。）`auto_ptr<Type>` 的析构函数将删除已分配的对象。 `auto_ptr<Type>` 可确保在块失去控制权时（甚至在已引发异常的情况下）自动删除已分配的对象。 不应构造两个拥有相同对象的 `auto_ptr<Type>` 对象。  
  
 可以将 `auto_ptr<Type>` 对象作为函数调用的参数按值传递。 `auto_ptr` 不能是任何标准库容器的元素。 你无法使用 C++ 标准库容器可靠地管理一系列 `auto_ptr<Type>` 对象。  
  
## <a name="members"></a>成员  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[auto_ptr](#auto_ptr)|`auto_ptr` 类型的对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[element_type](#element_type)|该类型是模板参数 `Type` 的同义词。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[get](#get)|该成员函数将返回存储的指针 `myptr`。|  
|[release](#release)|该成员将存储的指针 `myptr` 替换为 Null 指针，并返回以前存储的指针。|  
|[reset](#reset)|此成员函数对表达式 `delete myptr` 进行求值，但仅在存储的指针值 `myptr` 因函数调用而更改时进行。 然后它将存储的指针替换为 `ptr`。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator=](#op_eq)|一个赋值运算符，用于将所有权从一个 `auto_ptr` 对象转移到到其他对象。|  
|[operator*](#op_star)|`auto_ptr` 类型的对象的取消引用运算符。|  
|[operator->](#operator-_gt)|允许成员访问的运算符。|  
|[operator auto_ptr\<Other>](#op_auto_ptr_lt_other_gt)|将某种 `auto_ptr` 强制转换为另一种 `auto_ptr`。|  
|[operator auto_ptr_ref\<Other>](#op_auto_ptr_ref_lt_other_gt)|将 `auto_ptr` 强制转换为 `auto_ptr_ref`。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<memory>  
  
 **命名空间：** std  
  
##  <a name="auto_ptr"></a>  auto_ptr::auto_ptr  
 `auto_ptr` 类型的对象的构造函数。  
  
```   
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>  
auto _ptr(auto _ptr<Other>& right) throw();
```  
  
### <a name="parameters"></a>参数  
 `ptr`  
 指向 `auto_ptr` 封装的对象的指针。  
  
 `right`  
 由构造函数复制的 `auto_ptr` 对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数将 `ptr` 存储在 **myptr** 中，存储的指针指向已分配对象。 第二个构造函数通过存储 `right` 转移 `right` 中存储的指针的所有权。 **myptr** 中的 [release](#release)。  
  
 第三个构造函数的行为与第二个相同，只不过它存储 **right**。 `ref`。 **myptr** 中的 **release**，其中 `ref` 是 `right` 中存储的引用。  
  
 模板构造函数与第二个构造函数的行为相同，前提是指向 **Other** 的指针可以隐式转换为指向 **Type** 的指针。  
  
### <a name="example"></a>示例  
  
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
  
##  <a name="element_type"></a>  auto_ptr::element_type  
 该类型是模板参数 **Type** 的同义词。  
  
```  
 
typedef Type element  _type;  
```  
  
##  <a name="get"></a>  auto_ptr::get  
 该成员函数将返回存储指针 **myptr**。  
  
```   
Type *get() const throw();
```  
  
### <a name="return-value"></a>返回值  
 存储指针 **myptr**。  
  
### <a name="example"></a>示例  
  
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
  
##  <a name="op_eq"></a>  auto_ptr::operator=  
 一个赋值运算符，用于将所有权从一个 `auto_ptr` 对象转移到到其他对象。  
  
```  
template <class Other>  
auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```  
  
### <a name="parameters"></a>参数  
 `right`  
 一个 `auto_ptr` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 对类型为 `auto_ptr`\< **Type**>. 的对象的引用。  
  
### <a name="remarks"></a>备注  
 赋值将对表达式 **delete myptr** 进行求值，但是仅存储指针 **myptr** 因赋值而更改时才进行。 然后，它通过存储 \_ *Right* 转移存储在 _ *Right* 中的指针的所有权。 **myptr** 中的 [release](#release)。 该函数返回 **\*this**。  
  
### <a name="example"></a>示例  
  有关成员运算符的用法的示例，请参阅 [auto_ptr:: auto_ptr](#auto_ptr)。  
  
##  <a name="op_star"></a>  auto_ptr::operator*  
 `auto_ptr` 类型的对象的取消引用运算符。  
  
```   
Type& operator*() const throw();
```  
  
### <a name="return-value"></a>返回值  
 对指针所拥有的类型 **Type** 的对象的引用。  
  
### <a name="remarks"></a>备注  
 间接运算符返回 `*`[get](#get)。 因此，存储的指针不能为空。  
  
### <a name="example"></a>示例  
  有关如何使用成员函数的示例，请参阅 [auto_ptr:: auto_ptr](#auto_ptr)。  
  
##  <a name="auto_ptr__operator-_gt"></a>  auto_ptr::operator-&gt;  
 允许成员访问的运算符。  
  
```   
Type * operator->() const throw();
```  
  
### <a name="return-value"></a>返回值  
 **auto_ptr** 所拥有的对象的成员。  
  
### <a name="remarks"></a>备注  
 选择运算符返回 [get](#get)`( )`，以便让表达式 *ap*-> **member** 的行为与 ( *ap* 相同。 **get**( ) )-> **member**，其中 *ap* 是类 `auto_ptr`\< **Type**> 的对象。 因此，存储的指针不能为空且 **Type** 必须是类、结构或成员为 **member** 的联合类型。  
  
### <a name="example"></a>示例  
  有关如何使用成员函数的示例，请参阅 [auto_ptr:: auto_ptr](#auto_ptr)。  
  
##  <a name="op_auto_ptr_lt_other_gt"></a>  auto_ptr::operator auto_ptr&lt;Other&gt;  
 将某种 `auto_ptr` 强制转换为另一种 `auto_ptr`。  
  
```   
template <class Other>  
operator auto _ptr<Other>() throw();
```  
  
### <a name="return-value"></a>返回值  
 该类型强制转换运算符返回 `auto_ptr` \< **Other**>( **\*this**)。  
  
### <a name="example"></a>示例  
  
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
  
##  <a name="op_auto_ptr_ref_lt_other_gt"></a>  auto_ptr::operator auto_ptr_ref&lt;Other&gt;  
 将 `auto_ptr` 强制转换为 **auto_ptr_ref**。  
  
```   
template <class Other>  
operator auto _ptr  _ref<Other>() throw();
```  
  
### <a name="return-value"></a>返回值  
 该类型强制转换运算符返回 **auto_ptr_ref**\< **Other**>( **\*this**)。  
  
### <a name="example"></a>示例  
  
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
  
##  <a name="release"></a>  auto_ptr::release  
 该成员将存储指针 **myptr** 替换为 Null 指针，并返回以前存储的指针。  
  
```   
Type *release() throw();
```  
  
### <a name="return-value"></a>返回值  
 以前存储的指针。  
  
### <a name="remarks"></a>备注  
 该成员将存储指针 **myptr** 替换为 Null 指针，并返回以前存储的指针。  
  
### <a name="example"></a>示例  
  
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
  
##  <a name="reset"></a>  auto_ptr::reset  
 成员函数的计算结果表达式**删除** **myptr**，但是只有当存储的指针值**myptr**因函数调用而更改。 然后它将存储的指针替换为 **ptr**。  
  
```   
void reset(Type* ptr = 0);
```  
  
### <a name="parameters"></a>参数  
 `ptr`  
 指定用于替换已存储指针 **myptr** 的指针。  
  
### <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [unique_ptr 类](../standard-library/unique-ptr-class.md)

