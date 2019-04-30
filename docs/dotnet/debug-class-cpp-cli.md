---
title: Debug 类 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 3a262a0d2ef429cb94f4648eb7c7180e7b130279
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393774"
---
# <a name="debug-class-ccli"></a>Debug 类 (C++/CLI)

使用时<xref:System.Diagnostics.Debug>视觉对象中C++应用程序，该行为不会更改调试版本和发布版本之间。

## <a name="remarks"></a>备注

行为<xref:System.Diagnostics.Trace>Debug 类的行为完全相同，但依赖于跟踪正在定义的符号。 这意味着您必须`#ifdef`任何与跟踪相关的代码以避免在发布版本中的调试行为。

## <a name="example"></a>示例

### <a name="description"></a>描述

下面的示例始终执行的输出语句，而不考虑是否使用编译 **/DDEBUG**或 **/DTRACE**。

### <a name="code"></a>代码

```cpp
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

### <a name="output"></a>Output

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example"></a>示例

### <a name="description"></a>描述

若要获取的预期的行为 （即，没有"test"打印输出的发布版本），则必须使用`#ifdef`和`#endif`指令。 下面修改上面的代码示例来演示此修补程序：

### <a name="code"></a>代码

```cpp
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
