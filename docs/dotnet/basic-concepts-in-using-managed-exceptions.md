---
title: 使用托管异常中的基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: 4eeec5db00ceca5429f4a3a270e1b249a8955249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230917"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>使用托管异常中的基本概念

本主题讨论托管应用程序中的异常处理。 也就是说，使用 **/clr**编译器选项编译的应用程序。

## <a name="in-this-topic"></a>本主题内容

- [在/clr 下引发异常](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [CLR 扩展的 Try/Catch 块](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>备注

如果使用 **/clr**选项进行编译，则可以处理 clr 异常以及标准 <xref:System.Exception> 类提供许多用于处理 clr 异常的有用方法，并建议将其用作用户定义的异常类的基类。

在 **/clr**下，不支持捕获从接口派生的异常类型。 此外，公共语言运行时不允许捕获堆栈溢出异常;堆栈溢出异常将终止进程。

有关托管和非托管应用程序中的异常处理差异的详细信息，请参阅[Managed Extensions for C++ 下的异常处理行为的差异](../dotnet/differences-in-exception-handling-behavior-under-clr.md)。

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>在/clr 下引发异常

对 c + + throw 表达式进行扩展，以引发 CLR 类型的句柄。 下面的示例创建一个自定义异常类型，并引发该类型的实例：

```cpp
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

在引发之前，必须对值类型进行装箱：

```cpp
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>CLR 扩展的 Try/Catch 块

相同的 **`try`** / **`catch`** 块结构可用于同时捕获 CLR 和本机异常：

```cpp
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>输出

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>C + + 对象的展开顺序

对于带有析构函数的任何 c + + 对象（可能在引发函数与处理函数之间的运行时堆栈上），将发生展开。 因为 CLR 类型是在堆上分配的，所以展开不应用于它们。

引发的异常的事件顺序如下所示：

1. 运行时将遍历查找适当的 catch 子句的堆栈，对于 SEH，则会遍历该堆栈（SEH 除外）来捕获异常。 先按词法顺序搜索 Catch 子句，然后在调用堆栈中动态向下搜索。

1. 找到正确的处理程序后，堆栈将被展开到该点。 对于堆栈上的每个函数调用，其本地对象是销毁的，并且从最嵌套的外部执行 __finally 块。

1. 堆栈展开后，会执行 catch 子句。

### <a name="catching-unmanaged-types"></a>捕获非托管类型

当引发非托管对象类型时，它将包装为类型为的异常 <xref:System.Runtime.InteropServices.SEHException> 。 搜索相应的子句时 **`catch`** ，有两种可能的情况。

- 如果遇到本机 c + + 类型，则会将异常解包，并将其与遇到的类型进行比较。 此比较允许以正常方式捕获本机 c + + 类型。

- 但是，如果 **`catch`** 首先检查类型为**SEHException**或其任何基类的子句，子句将截获该异常。 因此，应将捕获本机 c + + 类型的所有 catch 子句放在 CLR 类型的任何 catch 子句之前。

请注意：

```
catch(Object^)
```

和

```
catch(...)
```

将捕获任何引发的类型，包括 SEH 异常。

如果 catch （Object ^）捕获非托管类型，则不会销毁引发的对象。

引发或捕获非托管异常时，建议使用[/ehsc](../build/reference/eh-exception-handling-model.md)编译器选项，而不是 **/ehs**或 **/eha**。

## <a name="see-also"></a>另请参阅

[异常处理](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[异常处理](../cpp/exception-handling-in-visual-cpp.md)
