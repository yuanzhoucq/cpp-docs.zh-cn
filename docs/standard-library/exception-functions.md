---
title: '&lt;exception&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 34a34c48be8bb0e319a7d0eebeccba805cafbc1f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246060"
---
# <a name="ltexceptiongt-functions"></a>&lt;exception&gt; 函数

## <a name="current_exception"></a> current_exception

获取指向当前异常的智能指针。

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>返回值

指向当前异常的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 对象。

### <a name="remarks"></a>备注

调用 catch 块中的 `current_exception` 函数。 如果异常处于飞行状态，而且 catch 块可捕获该异常，则 `current_exception` 函数将返回引用该异常的 `exception_ptr` 对象。 否则，该函数将返回 null `exception_ptr` 对象。

`current_exception`函数会捕获的异常处于飞行状态，而不管是否**捕获**语句指定[异常声明](../cpp/try-throw-and-catch-statements-cpp.md)语句。

当前异常的析构函数调用的末尾**捕获**阻止如果不重新引发异常。 但是，即使调用析构函数中的 `current_exception` 函数，该函数仍返回引用当前异常的 `exception_ptr` 对象。

对 `current_exception` 函数的相继调用将返回引用当前异常的不同副本的 `exception_ptr` 对象。 因此，由于对象引用不同的副本，即使副本具有相同的二进制值，其比较结果也是不相等。

## <a name="make_exception_ptr"></a> make_exception_ptr

创建保留异常副本的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 对象。

```cpp
template <class E>
    exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>参数

*除外*\
具有要复制的异常的类。 通常，指定[异常类](../standard-library/exception-class.md)对象作为参数传递给 `make_exception_ptr` 函数，但任意类对象都可以是参数。

### <a name="return-value"></a>返回值

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)指向的当前异常副本的对象*除*。

### <a name="remarks"></a>备注

调用 `make_exception_ptr` 函数等效于引发 C++ 异常、在 catch 块中捕获它并调用 [current_exception](../standard-library/exception-functions.md#current_exception) 函数以返回引用异常的 `exception_ptr` 对象。 Microsoft 实现的 `make_exception_ptr` 函数比调用并捕获异常更高效。

应用程序通常不需要 `make_exception_ptr` 函数，因此，我们不建议使用此函数。

## <a name="rethrow_exception"></a> rethrow_exception

引发作为参数传递的异常。

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>参数

*P*\
要再次引发的已捕获异常。 如果*P*为 null [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)，该函数将引发[std:: bad_exception](../standard-library/bad-exception-class.md)。

### <a name="remarks"></a>备注

在 `exception_ptr` 对象中存储捕获的异常后，主线程便可以处理该对象。 在主线程中，调用 `rethrow_exception` 函数，将 `exception_ptr` 对象作为其参数。 `rethrow_exception` 函数从 `exception_ptr` 对象中提取异常，然后在主线程的上下文中引发异常。

## <a name="get_terminate"></a> get_terminate

获取当前的 `terminate_handler` 函数。

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a> set_terminate

建立程序终止时要调用的新 `terminate_handler`。

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>参数

*fnew*\
终止时要调用的函数。

### <a name="return-value"></a>返回值

上一个在终止时用于调用的函数的地址。

### <a name="remarks"></a>备注

该函数建立新[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)如同函数 * *fnew*。 因此， *fnew*必须不能为 null 指针。 函数将返回上一个终止处理程序的地址。

### <a name="example"></a>示例

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}
```

## <a name="get_unexpected"></a> get_unexpected

获取当前的 `unexpected_handler` 函数。

```cpp
unexpected_handler get_unexpected();
```

## <a name="rethrow_if_nested"></a> rethrow_if_nested

```cpp
template <class E> 
    void rethrow_if_nested(const E& e);
```

### <a name="remarks"></a>备注

如果不是多态类类型，或者如果`nested_exception`无法访问或不明确的没有任何影响。 否则，执行动态强制转换。

## <a name="set_unexpected"></a> set_unexpected

建立遇到意外异常时要调用的新 `unexpected_handler`。

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>参数

*fnew*\
遇到意外异常时要调用的函数。

### <a name="return-value"></a>返回值

上一个 `unexpected_handler` 的地址。

### <a name="remarks"></a>备注

*fnew*必须不能为 null 指针。

C++ 标准要求在函数引发其引发列表中未包含的异常时调用 `unexpected`。 当前实现不支持此操作。 以下示例直接调用 `unexpected`，后者随后调用 `unexpected_handler`。

### <a name="example"></a>示例

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}
```

## <a name="terminate"></a> 终止

调用终止处理程序。

```cpp
void terminate();
```

### <a name="remarks"></a>备注

该函数将调用终止处理程序，类型的函数**void**。 如果`terminate`调用直接通过程序终止处理程序最新的项目设置通过调用[set_terminate](../standard-library/exception-functions.md#set_terminate)。 如果`terminate`调用的任何其他原因引发表达式计算期间，终止处理程序是一个有效 throw 表达式求值后。

终止处理程序可能不会返回至其调用方。 程序启动时，终止处理程序调用的函数`abort`。

### <a name="example"></a>示例

有关 `terminate` 的使用示例，请参阅 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。

## <a name="throw_with_nested"></a> throw_with_nested

```cpp
template <class T> [[noreturn]]
    void throw_with_nested(T&& t);
```

### <a name="remarks"></a>备注

将引发嵌套异常的异常。

## <a name="uncaught_exception"></a> uncaught_exception

仅当引发的异常当前正在处理时返回 **true**。

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>返回值

返回 **，则返回 true**完成引发表达式和完成的匹配处理程序或调用中的异常声明初始化之前评估后[意外](../standard-library/exception-functions.md#unexpected)为引发表达式。 具体而言，`uncaught_exception`将返回**true**从异常展开期间调用的析构函数中调用时。 在设备上，仅 Windows CE 5.00 及更高版本（包括 Windows Mobile 2005 平台）支持 `uncaught_exception`。

### <a name="example"></a>示例

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a> 意外

调用意外处理程序。

```cpp
void unexpected();
```

### <a name="remarks"></a>备注

C++ 标准要求在函数引发其引发列表中未包含的异常时调用 `unexpected`。 当前实现不支持此操作。 此示例直接调用会调用意外处理程序的 `unexpected`。

该函数将调用意外处理程序，类型的函数**void**。 如果直接通过程序调用了 `unexpected`，则此意外处理程序是最近通过对 [set_unexpected](../standard-library/exception-functions.md#set_unexpected) 的调用设置的那一个。

意外处理程序可能不会返回其调用方。 其可能通过以下方式终止执行：

- 引发异常规范中所列出的类型的对象，或如果直接通过程序调用了意外处理程序，则引发任意类型的对象。

- 引发 [bad_exception](../standard-library/bad-exception-class.md) 类型的对象。

- 调用[终止](../standard-library/exception-functions.md#terminate)，`abort`或**退出**(`int`)。

程序启动时，意外处理程序是调用 [terminate](../standard-library/exception-functions.md#terminate) 的函数。

### <a name="example"></a>示例

有关 `unexpected` 的使用示例，请参阅 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。
