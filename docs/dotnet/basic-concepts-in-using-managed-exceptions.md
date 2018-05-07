---
title: 托管异常中使用的基本概念 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 255a7d053228b73b2b0eb13f4732e9a7829549ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>使用托管异常中的基本概念
本主题讨论托管应用程序中的异常处理。 也就是说，编译应用程序与 **/clr**编译器选项。  
  
## <a name="in-this-topic"></a>在本主题中  
  
-   [引发异常下 /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [Try/Catch 块的 CLR 扩展](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## <a name="remarks"></a>备注  
 如果使用编译 **/clr**选项，你可以处理 CLR 异常，以及标准[c + + 异常处理](../cpp/cpp-exception-handling.md)和[结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)(SEH)。 CLR 异常是由托管类型引发任何异常。 [System:: exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx)类提供用于处理 CLR 异常许多有用的方法，并建议将其作为用户定义的异常类的基类。  
  
 捕捉从接口派生的异常类型不支持下 **/clr**。 此外，，公共语言运行时不允许你要捕获堆栈溢出异常;堆栈溢出异常将终止进程。  
  
 有关在托管和非托管应用程序中的异常处理方面的差异的详细信息，请参阅[扩展之间的差异异常处理行为下托管的 c + +](../dotnet/differences-in-exception-handling-behavior-under-clr.md)。  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> 引发异常下 /clr  
 C + + throw 表达式扩展为 CLR 类型引发句柄。 下面的示例创建一个自定义异常类型，然后引发该类型的实例：  
  
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
  
 必须在引发之前装箱值类型：  
  
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
 相同**重**/**捕获**块结构可以用于捕获 CLR 和本机异常：  
  
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
  
### <a name="output"></a>输出  
  
```  
In 'catch(CMyClass& catchC)'  
2  
In 'catch(MyStruct^ catchException)'  
11  
```  
  
### <a name="order-of-unwinding-for-c-objects"></a>可以为 c + + 对象展开的顺序  
 展开时发生的析构函数可能引发的函数和处理函数之间的运行时堆栈上的任何 c + + 对象。 由于 CLR 类型分配堆上，展开不适用于它们。  
  
 引发的异常事件的顺序如下所示：  
  
1.  运行时遍历堆栈进行调试查找为适当的 catch 子句，或者如果 SEH，除 SEH，以捕获异常的筛选器。 Catch 子句首先搜索在词法顺序中上下然后动态调用堆栈。  
  
2.  一旦找到正确的处理程序，则堆栈将展开到该点。 每个函数调用堆栈上，其本地对象被销毁和块执行 __finally，可以从大多数由里向外嵌套。  
  
3.  展开堆栈后，执行 catch 子句。  
  
### <a name="catching-unmanaged-types"></a>捕捉非托管的类型  
 当引发时的非托管的对象类型时，则它将包装类型的异常[System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx)。 搜索适当时**捕获**子句中，有两种可能。  
  
-   如果遇到本机 c + + 类型时，此异常将解包并相比所遇到的类型。 这种比较允许以常规方式捕获的本机 c + + 类型。  
  
-   但是，如果**捕获**类型子句**SEHException**或任何其基类三思而后，子句将截获异常。 因此，你应将放置任何 catch 子句的 CLR 类型之前先捕获本机 c + + 类型的所有 catch 子句。  
  
 请注意：  
  
```  
catch(Object^)  
```  
  
 和  
  
```  
catch(...)  
```  
  
 同时将捕获任何则引发该异常的类型，包括 SEH 异常。  
  
 如果通过 catch(Object^) 捕获到非托管的类型，则它不会破坏则引发该异常的对象。  
  
 时可以引发或捕捉非托管异常，我们建议你使用[/EHsc](../build/reference/eh-exception-handling-model.md)编译器选项，而不是 **/EHs**或 **/EHa**。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)