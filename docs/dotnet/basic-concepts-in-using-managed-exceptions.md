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
ms.openlocfilehash: 6bc1e9c6d40599ae9a821179dcf56dbb7e21bf10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372532"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>使用托管异常中的基本概念

本主题讨论托管应用程序中的异常处理。 也就是说，使用 **/clr**编译器选项编译的应用程序。

## <a name="in-this-topic"></a>本主题内容

- [在 /clr 下引发异常](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [CLR 扩展的尝试/捕获块](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>备注

如果使用 **/clr**选项进行编译，则可以处理 CLR 异常以及标准<xref:System.Exception>类提供了许多用于处理 CLR 异常的有用方法，建议作为用户定义的异常类的基类。

**在 /clr**下不支持捕获从接口派生的异常类型。 此外，通用语言运行时不允许捕获堆栈溢出异常;堆栈溢出异常将终止进程。

有关托管和非托管应用程序中异常处理差异的详细信息，请参阅[C++ 的"托管扩展下异常处理行为差异](../dotnet/differences-in-exception-handling-behavior-under-clr.md)"。

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>在 /clr 下引发异常

C++引发表达式将扩展以将句柄扔到 CLR 类型。 下面的示例创建自定义异常类型，然后引发该类型的实例：

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

在引发之前，必须装箱值类型：

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

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>CLR 扩展的尝试/捕获块

相同的**try**/**catch**块结构可用于捕获 CLR 和本机异常：

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

### <a name="order-of-unwinding-for-c-objects"></a>C++对象的展开顺序

对于具有析构函数的任何C++对象，这些对象可能在引发函数和处理函数之间的运行时堆栈上。 由于 CLR 类型在堆上分配，因此展开不适用于它们。

引发异常的事件顺序如下：

1. 运行时遍网查找适当的 catch 子句，或者对于 SEH（SEH 的筛选器除外）的情况，则运行以捕获异常。 先按词法顺序搜索 Catch 子句，然后动态向下调用堆栈。

1. 找到正确的处理程序后，堆栈将解缠到该点。 对于堆栈上的每个函数调用，其本地对象都会被破坏，并且__finally块从大多数嵌套向外执行。

1. 解包后，将执行 catch 子句。

### <a name="catching-unmanaged-types"></a>捕获非托管类型

引发非托管对象类型时，将用 类型<xref:System.Runtime.InteropServices.SEHException>的异常包装它。 搜索适当的 CATCH 子**句**时，有两种可能性。

- 如果遇到本机C++类型，则取消包装异常，并将其与遇到的类型进行比较。 此比较允许以正常方式捕获本机C++类型。

- 但是，如果首先检查**SEHException**类型或其任何基类的**catch**子句，则子句将截取异常。 因此，应首先将捕获本机C++类型的所有 catch 子句放在 CLR 类型的任何 catch 子句之前。

请注意：

```
catch(Object^)
```

and

```
catch(...)
```

都会捕获任何引发类型，包括 SEH 异常。

如果非托管类型被 catch（Object_）捕获，则不会破坏引发的对象。

在引发或捕获非托管异常时，我们建议您使用[/EHsc](../build/reference/eh-exception-handling-model.md)编译器选项而不是 **/EHs**或 **/EHa**。

## <a name="see-also"></a>另请参阅

[异常处理](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[异常处理](../cpp/exception-handling-in-visual-cpp.md)
