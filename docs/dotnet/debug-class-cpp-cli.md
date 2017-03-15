---
title: "Debug 类 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], 调试类"
  - "调试类"
  - "Trace 类, Visual C++"
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Debug 类 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 应用程序中使用 <xref:System.Diagnostics.Debug> 时，行为在调试版本和发布版本之间不发生更改。  
  
## 备注  
 <xref:System.Diagnostics.Trace> 的行为与 Debug 类的行为相同，但是依赖于正被定义的符号 TRACE。  这意味着必须 `#ifdef` 任何与 Trace 相关的代码，以防止在发布版本中出现调试行为。  
  
## 示例  
  
### 说明  
 无论您是用 **\/DDEBUG** 还是用 **\/DTRACE** 编译，下面的示例总是执行输出语句。  
  
### 代码  
  
```  
// mcpp_debug_class.cpp  
// compile with: /clr  
#using <system.dll>  
using namespace System::Diagnostics;  
using namespace System;  
  
int main() {  
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );  
   Trace::AutoFlush = true;  
   Trace::Indent();  
   Trace::WriteLine( "Entering Main" );  
   Console::WriteLine( "Hello World." );  
   Trace::WriteLine( "Exiting Main" );  
   Trace::Unindent();  
  
   Debug::WriteLine("test");  
}  
```  
  
### Output  
  
```  
    Entering Main  
Hello World.  
    Exiting Main  
test  
```  
  
## 示例  
  
### 说明  
 若要获得预期的行为（即发布版本不打印“test”输出），必须使用 `#ifdef` 和 `#endif` 指令。  上述代码示例经过如下修改以说明此修复：  
  
### 代码  
  
```  
// mcpp_debug_class2.cpp  
// compile with: /clr  
#using <system.dll>  
using namespace System::Diagnostics;  
using namespace System;  
  
int main() {  
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );  
   Trace::AutoFlush = true;  
   Trace::Indent();  
  
#ifdef TRACE   // checks for a debug build  
   Trace::WriteLine( "Entering Main" );  
   Console::WriteLine( "Hello World." );  
   Trace::WriteLine( "Exiting Main" );  
#endif  
   Trace::Unindent();  
  
#ifdef DEBUG   // checks for a debug build  
   Debug::WriteLine("test");  
#endif   //ends the conditional block  
}  
```  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)