---
title: "如何：使用本机类型声明句柄 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "gcroot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gcroot 关键字 [C++]"
  - "句柄, 声明"
  - "类型 [C++], 声明句柄"
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用本机类型声明句柄
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不能在本机类型中声明句柄类型。vcclr.h 提供类型安全包装模板 `gcroot` 指从 C\+\+ 堆的 CLR 对象。  此模板使您可以在本机类型中嵌入虚句柄，并且将其视为基础类型。  在大多数情况下，可以将 `gcroot` 对象作为嵌入类型使用，而不需要任何转换。  但是，对于 [for each，in](../dotnet/for-each-in.md)，必须使用 `static_cast` 来检索基础托管引用。  
  
 `gcroot` 模板是使用值类 System::Runtime::InteropServices::GCHandle 的功能实现的，该值类将“句柄”提供到垃圾回收堆中。  请注意，句柄本身不是回收的垃圾，并且不再使用时会被 `gcroot` 类中的析构函数（无法手动调用此析构函数）释放。  如果在本机堆上实例化 `gcroot` 对象，则必须对该资源调用删除操作。  
  
 运行时将维护句柄与 CLR 对象之间的关联，它将引用该关联。  当 CLR 对象与垃圾回收堆一起移动时，该句柄将返回该对象的新地址。  变量指派给 `gcroot` 模板前不必被固定。  
  
## 示例  
 此示例演示如何在本机堆栈上创建 `gcroot` 对象。  
  
```  
// mcpp_gcroot.cpp  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
class CppClass {  
public:  
   gcroot<String^> str;   // can use str as if it were String^  
   CppClass() {}  
};  
  
int main() {  
   CppClass c;  
   c.str = gcnew String("hello");  
   Console::WriteLine( c.str );   // no cast required  
}  
```  
  
  **hello**   
## 示例  
 此示例演示如何在本机堆上创建 `gcroot` 对象。  
  
```  
// mcpp_gcroot_2.cpp  
// compile with: /clr  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
struct CppClass {  
   gcroot<String ^> * str;  
   CppClass() : str(new gcroot<String ^>) {}  
  
   ~CppClass() { delete str; }  
  
};  
  
int main() {  
   CppClass c;  
   *c.str = gcnew String("hello");  
   Console::WriteLine( *c.str );  
}  
```  
  
  **hello**   
## 示例  
 此示例演示如何通过对装箱类型使用 `gcroot`，来实现用 `gcroot` 保存对本机类型中的值类型（不是引用类型）的引用。  
  
```  
// mcpp_gcroot_3.cpp  
// compile with: /clr  
#include < vcclr.h >  
using namespace System;  
  
public value struct V {  
   String^ str;  
};  
  
class Native {  
public:  
   gcroot< V^ > v_handle;  
};  
  
int main() {  
   Native native;  
   V v;  
   native.v_handle = v;  
   native.v_handle->str = "Hello";  
   Console::WriteLine("String in V: {0}", native.v_handle->str);  
}  
```  
  
  **String in V: Hello**   
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)