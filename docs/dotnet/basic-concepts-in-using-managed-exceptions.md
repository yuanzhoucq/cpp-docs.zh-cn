---
title: "使用托管异常中的基本概念 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__finally 关键字, 托管异常"
  - "捕捉块"
  - "异常, 托管"
  - "引发异常, 托管异常"
  - "try-catch 异常处理"
  - "try-catch 异常处理, 托管应用程序"
  - "Visual C++, 处理托管异常"
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 使用托管异常中的基本概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论托管应用程序中的异常处理。  即用 **\/clr** 编译选项编译的应用程序。  
  
## 主题内容  
  
-   [在 \/clr 下抛出的异常。](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [CLR 扩展的 try\/catch 块](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## 备注  
 如果编译带有 **\/clr** 选项，可以像标准的 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md) 和 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md) （SEH）一样处理 CLR 异常。  CLR 异常是由托管类型抛出的任何异常。  [System::Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx) 类为处理 CLR 异常提供了许多有用方法并推荐作为用户定义的异常类的基类。  
  
 从接口派生的捕获异常类型不支持位于 **\/clr**下。  此外，公共语言运行时不允许捕捉堆栈溢出异常；堆栈溢出异常将终止进程。  
  
 有关位于托管和非托管应用程序中的异常处理差异的更多信息，请参见 [在 C\+\+ 托管扩展中异常处理行为的区别](../dotnet/differences-in-exception-handling-behavior-under-clr.md)。  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> 在 \/clr 下抛出的异常。  
 C\+\+ throw 表达式被扩展为抛出句柄到 CLR 类型。  下面的示例演示了创建自定义异常类型并随后抛出该类型的实例：  
  
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
  
 值类型必须在抛出之前装箱：  
  
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
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> CLR 扩展的 try\/catch 块  
 同一个 **try**\/**catch** 块结构可同时用于捕获 CLR 和本机异常：  
  
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
  
### Output  
  
```  
In 'catch(CMyClass& catchC)'  
2  
In 'catch(MyStruct^ catchException)'  
11  
```  
  
### C\+\+ 对象解旋的顺序  
 解旋发生在任何具有处于抛出函数和处理函数之间的运行时堆栈上的析构函数的 C\+\+ 对象。  由于 CLR 类型在堆中分配，解旋不适用于它们。  
  
 对于已抛出异常的事件的顺序如下所示：  
  
1.  运行时遍历查找堆栈适当的 Catch 子句，或者对于 SEH，查找除她以外的筛选器，来捕捉异常。  Catch 子句首先在词法顺序搜索，然后动态按调用堆栈顺序向下。  
  
2.  一旦找到正确的处理程序，其将在该点解旋。  对于调用堆栈上的每个函数，其本地对象被析构，并从 \_\_finally 块嵌套向外执行。  
  
3.  一旦堆栈被展开，catch 子句执行。  
  
### 捕获非托管类型  
 当非托管对象类型引发时，它将使用 [System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx) 类型的异常。  当搜索适当的 **catch** 子句时，有两种可能。  
  
-   如果遇到本机 C\+\+ 类型，异常就会展开并与遇到的类型进行比较。  此比较使得本机 C\+\+ 类型可以以常规方式捕获。  
  
-   但是，如果 **catch** 子句为 **SEHException** 类型或任何其基类被首先检查，该子句将截获异常。  因此，应首先将捕获本机 C\+\+ 类型的所有 catch 子句放在任何捕获 CLR 类型的 catch 子句之前。  
  
 请注意  
  
```  
catch(Object^)  
```  
  
 和  
  
```  
catch(...)  
```  
  
 都将捕获任何包括 SEH 异常的抛出类型。  
  
 如果非托管类型被 catch\(Object^\) 语句捕获，它将不会损坏抛出对象。  
  
 当抛出或捕获了非托管异常，建议您改用 [\/EHsc](../build/reference/eh-exception-handling-model.md) 编译器选项代替 **\/EHs** 或 **\/EHa**。  
  
## 请参阅  
 [异常处理](../windows/exception-handling-cpp-component-extensions.md)   
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)