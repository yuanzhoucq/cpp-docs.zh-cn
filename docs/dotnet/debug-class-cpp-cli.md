---
title: Debug 类 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fddf192b21b878c82ca663da657c55e32fd9173d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106201"
---
# <a name="debug-class-ccli"></a>Debug 类 (C++/CLI)
使用时<xref:System.Diagnostics.Debug>在 Visual c + + 应用程序，该行为不会更改调试版本和发布版本之间。  
  
## <a name="remarks"></a>备注  
 行为<xref:System.Diagnostics.Trace>等同于 Debug 类的行为，但依赖于跟踪正在定义的符号。 这意味着你必须`#ifdef`任何与跟踪相关的代码，以防止在发布版本中的调试行为。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例执行速度始终都输出语句，而不考虑是否使用编译 **/DDEBUG**或 **/DTRACE**。  
  
### <a name="code"></a>代码  
  
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
  
### <a name="output"></a>输出  
  
```  
    Entering Main  
Hello World.  
    Exiting Main  
test  
```  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 若要获取的预期的行为 （即，没有"test"的输出为打印的发布版本），你必须使用`#ifdef`和`#endif`指令。 前面的代码示例如下修改，以说明此修补程序：  
  
### <a name="code"></a>代码  
  
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
  
## <a name="see-also"></a>请参阅  
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)