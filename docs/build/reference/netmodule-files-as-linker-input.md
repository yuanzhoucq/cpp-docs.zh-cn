---
title: .netmodule 文件作为链接器输入
description: 描述如何使用 mixed。obj 与.netmodule 创建 .NET 程序集时作为链接器输入的文件。
ms.date: 01/30/2020
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodule files
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
no-loc:
- obj
- netmodule
- clr
- pure
- safe
ms.openlocfilehash: 83eab25624bdb81ba9191e4efe6a774551502ee0
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912819"
---
# <a name="opno-locnetmodule-files-as-linker-input"></a>.netmodule 文件作为链接器输入

share.exe 接受 MSIL *`.obj`* 和 *`.netmodule`* 文件作为输入。 链接器生成的输出文件是程序集或 *`.netmodule`* 文件，对任何 *`.obj`* 或 *`.netmodule`* 文件的任何输入链接器都没有运行时依赖关系。

## <a name="remarks"></a>备注

*`.netmodule`* 文件由 MSVC 编译器使用[/LN （创建 msil 模块）](ln-create-msil-module.md)或链接器使用[/NOASSEMBLY （创建 msil 模块）](noassembly-create-a-msil-module.md)创建。 *`.obj`* 文件始终在C++编译中创建。 对于其他 Visual Studio 编译器，请使用“/target:module”编译器选项。

必须从创建 *`.netmodule`* 的C++编译将 *`.obj`* 文件传递给链接器。 由于 **/clr：pure** 和 **/clr：safe** 编译器选项在 visual studio 2015 中被弃用并且在 visual studio 2017 和更高版本中不受支持，因此不再支持传入 *`.netmodule`* 。

有关如何从命令行调用链接器的信息，请参阅[链接器命令行语法](linking.md)，[从命令行使用 MSVC 工具集](../building-on-the-command-line.md)，并[为命令行生成设置路径和环境变量](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

使用 **/clr** 将 *`.netmodule`* 或 *`.dll`* 文件传递到 MSVC 编译器编译的链接器会导致链接器错误。 有关详细信息，请参阅[netmodule 输入文件的格式](choosing-the-format-of-netmodule-input-files.md)。

链接器接受用 **/clr** 编译的本机 *`.obj`* 文件和 MSIL *`.obj`* 文件。 可以在同一版本中传递混合的 *`.obj`* 文件。 生成的输出文件的默认可验证性与最低输入模块的可验证性相同。

您可以更改由两个或多个程序集组成的应用程序，使其包含在一个程序集中。 重新编译程序集的源，并链接 *`.obj`* 文件或 *`.netmodule`* 文件以生成单个程序集。

创建可执行映像时，请使用[/ENTRY （入口点符号）](entry-entry-point-symbol.md)指定入口点。

使用 MSIL *`.obj`* 或 *`.netmodule`* 文件链接时，请使用[/ltcg （链接时间代码生成）](ltcg-link-time-code-generation.md)，否则，当链接器遇到 MSIL *`.obj`* 或 *`.netmodule`* 时，它将使用 **/ltcg**重新启动链接。 你将看到一条信息性消息，指出链接正在重新启动。 您可以忽略此消息，但为了提高链接器性能，请显式指定 **/ltcg**。

MSIL *`.obj`* 或 *`.netmodule`* 文件也可以传递给 cl .exe。

输入 MSIL *`.obj`* 或 *`.netmodule`* 文件不能具有嵌入的资源。 使用[/ASSEMBLYRESOURCE （嵌入托管资源）](assemblyresource-embed-a-managed-resource.md)链接器选项将资源嵌入到输出模块或程序集文件中。 或者，使用其他 Visual Studio 编译器中的 **/resource**编译器选项。

## <a name="examples"></a>示例

在C++代码中，将为非`System` 异常调用相应 **`try`** 的 **`catch`** 块。 不过，默认情况下，CLR 使用 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>包装非`System` 异常。 如果程序集是从C++和非C++模块创建的，并且你希望在 **`try`** 块引发非`System` 异常时，在代码中C++ C++从其相应的 **`try`** 子句调用 **`catch`** 块，则必须将 `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` 特性添加到非模块的源代码中。

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

通过更改 `WrapNonExceptionThrows` 特性的 `Boolean` 值，可以修改C++代码捕获非`System` 异常的能力。

```csharp
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

## <a name="see-also"></a>另请参阅

- [LINK 输入文件](link-input-files.md)
- [MSVC 链接器选项](linker-options.md)
