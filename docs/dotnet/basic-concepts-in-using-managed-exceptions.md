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
ms.openlocfilehash: e2aed98d9131b3d7b96cdc3e3297823d69d0ad38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393787"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>使用托管异常中的基本概念

本主题讨论托管应用程序中的异常处理。 也就是说，使用编译的应用程序 **/clr**编译器选项。

## <a name="in-this-topic"></a>在本主题中

- [引发的异常在 /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Try/Catch 块的 CLR 扩展](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>备注

如果使用编译 **/clr**选项，您可以处理 CLR 异常，以及标准<xref:System.Exception>类提供许多有用的方法，用于处理 CLR 异常和建议作为用户定义的异常的基类类。

捕获从接口派生的异常类型下，不支持 **/clr**。 此外，公共语言运行时不会不允许您捕获堆栈溢出异常;堆栈溢出异常将终止该进程。

有关在托管和非托管应用程序中的异常处理之间的差异的详细信息，请参阅[差异在异常处理行为下托管扩展中的C++ ](../dotnet/differences-in-exception-handling-behavior-under-clr.md)。

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> 引发的异常在 /clr

C++引发表达式扩展为 CLR 类型引发一个句柄。 下面的示例创建一个自定义异常类型，然后引发该类型的实例：

```
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

引发之前，必须将装箱值类型：

```
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

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> Try/Catch 块的 CLR 扩展

相同**尝试**/**捕获**块结构可用于捕获 CLR 和本机异常：

```
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

### <a name="output"></a>Output

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>你可以为展开的顺序C++对象

展开发生在任何C++具有析构函数可能引发函数和处理函数之间的运行时堆栈上的对象。 因为 CLR 类型的分配堆上，展开不适用于它们。

引发的异常事件的顺序是按如下所示：

1. 运行时遍历堆栈以查找适当的 catch 子句，或对于 SEH，除了 SEH，以捕获异常的筛选器。 Catch 子句按词汇顺序首先搜索，然后动态向下调用堆栈。

1. 一旦找到正确的处理程序，堆栈的展开到该点。 每个函数调用堆栈上，会销毁了其本地对象和块被执行 __finally，从大多数由里向外嵌套。

1. 展开堆栈后，执行 catch 子句。

### <a name="catching-unmanaged-types"></a>捕获非托管的类型

时引发的非托管的对象类型，则将其包装的类型异常<xref:System.Runtime.InteropServices.SEHException>。 搜索相应时**捕获**子句中，有两种可行方法。

- 如果一个本机C++遇到类型、 解包，相比所遇到的类型异常。 这种比较允许一个本机C++类型以正常方式捕获。

- 但是，如果**捕获**类型的子句**SEHException**或首先检查任何其基类，该子句将截获的异常。 因此，应将捕获的所有 catch 子句本机C++首先类型之前任何 catch 子句的 CLR 类型。

请注意：

```
catch(Object^)
```

和

```
catch(...)
```

同时会捕获任何则引发该异常的类型包括 SEH 异常。

如果非托管的类型由 catch(Object^) 捕获，它不会销毁则引发该异常的对象。

当引发或捕捉非托管异常时，我们建议你使用[/EHsc](../build/reference/eh-exception-handling-model.md)编译器选项代替 **/EHs**或 **/EHa**。

## <a name="see-also"></a>请参阅

[异常处理](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[异常处理](../cpp/exception-handling-in-visual-cpp.md)
