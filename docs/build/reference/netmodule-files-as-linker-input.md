---
title: 用作链接器输入的 .netmodule 文件
ms.date: 11/04/2016
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: fcba363cff567c69ac0fbd0a541953dfe2c8e910
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818097"
---
# <a name="netmodule-files-as-linker-input"></a>用作链接器输入的 .netmodule 文件

link.exe 现在接受 MSIL .obj 和 .netmodule 作为输入。 链接器生成的输出文件是程序集或.netmodule 没有运行时依赖于任何.obj 或.netmodule 输入到链接器。

由具有 MSVC 编译器创建.netmodule [/LN （创建 MSIL 模块）](ln-create-msil-module.md)或通过使用链接器[/NOASSEMBLY （创建 MSIL 模块）](noassembly-create-a-msil-module.md)。 .obj 始终创建 Visual c + + 编译中。 对于其他 Visual Studio 的编译器，使用 **/target: module**编译器选项。

您必须将传递到链接器.obj 文件中，从创建.netmodule 的 Visual c + + 编译。 不再支持.netmodule 中的传递，因为 **/clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

有关如何调用链接器命令行中的信息，请参阅[链接器命令行语法](linking.md)，[使用命令行中的 MSVC 工具集](../building-on-the-command-line.md)，和[设置路径和环境变量有关命令行生成](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

编译到链接器传递的.netmodule 或.dll 文件时的 MSVC 编译器 **/clr**可能会导致链接器错误。 有关详细信息，请参阅[选择.netmodule 输入文件的格式](choosing-the-format-of-netmodule-input-files.md)。

链接器接受本机.obj 文件，以及使用编译的 MSIL.obj 文件 **/clr**。 要在相同的版本中传递混合的.obj 时, 生成的输出文件的可验证性，默认情况下，将等于输入模块的可验证性的最低级别。

如果您当前拥有由两个或更多程序集组成的应用程序，并且您希望该应用程序包含在一个程序集中，则必须对程序集进行重新编译，然后链接 .obj 或 .netmodule 以生成单个程序集。

必须指定入口点使用[/ENTRY （入口点符号）](entry-entry-point-symbol.md)时创建的可执行映像。

链接时与 MSIL.obj 或.netmodule 文件，使用[/LTCG （链接时间代码生成）](ltcg-link-time-code-generation.md)，否则当链接器遇到 MSIL.obj 或.netmodule 时，它将重新启动与 /LTCG 的链接。

MSIL .obj 或 .netmodule 文件也可以传递到 cl.exe。

输入 MSIL 或 .obj .netmodule 文件不能有嵌入的资源。 与在输出文件 （模块或程序集） 中嵌入的资源[/ASSEMBLYRESOURCE （嵌入托管资源）](assemblyresource-embed-a-managed-resource.md)链接器选项或使用 **/resource**其他 Visual Studio 编译器中的编译器选项。

执行 MSIL 链接时，如果您还不指定[/LTCG （链接时间代码生成）](ltcg-link-time-code-generation.md)，将看到 reporting 链接正在重新启动一条信息性消息。 此消息可以忽略，但若要提高链接器性能与 MSIL 链接、 显式指定 **/LTCG**。

## <a name="example"></a>示例

在 c + + 代码**捕获**块的相应**尝试**将非系统异常的调用。 但是，默认情况下，CLR 将包装非系统异常和<xref:System.Runtime.CompilerServices.RuntimeWrappedException>。 当从 Visual c + + 和非-Visual c + + 模块创建程序集，并且您希望**捕获**阻止在 c + + 代码中要调用从其对应**尝试**子句时**尝试**块引发非系统异常，则必须添加`[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]`属性为非 c + + 模块的源代码。

```cpp
// MSIL_linking.cpp
// compile with: /c /clr
value struct V {};

ref struct MCPP {
   static void Test() {
      try {
         throw (gcnew V);
      }
      catch (V ^) {
         System::Console::WriteLine("caught non System exception in C++ source code file");
      }
   }
};

/*
int main() {
   MCPP::Test();
}
*/
```

## <a name="example"></a>示例

通过更改的布尔值`WrapNonExceptionThrows`属性，您可以修改 Visual c + + 代码能够捕获非系统异常。

```cpp
// MSIL_linking_2.cs
// compile with: /target:module /addmodule:MSIL_linking.obj
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console
using System.Runtime.CompilerServices;

// enable non System exceptions
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]

class MLinkTest {
   public static void Main() {
      try {
         MCPP.Test();
      }
      catch (RuntimeWrappedException) {
         System.Console.WriteLine("caught a wrapped exception in C#");
      }
   }
}
```

```Output
caught non System exception in C++ source code file
```

## <a name="see-also"></a>请参阅

- [LINK 输入文件](link-input-files.md)
- [MSVC 链接器选项](linker-options.md)
