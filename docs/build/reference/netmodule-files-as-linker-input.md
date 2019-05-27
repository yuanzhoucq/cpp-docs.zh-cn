---
title: 用作链接器输入的 .netmodule 文件
ms.date: 05/16/2019
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: 50a0f0a1ff5f65a7512e8372de2fe5296c866dca
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837428"
---
# <a name="netmodule-files-as-linker-input"></a>用作链接器输入的 .netmodule 文件

link.exe 现在接受 MSIL .obj 和 .netmodule 作为输入。 链接器生成的输出文件是一个与输入到链接器的任何 .obj 或 .netmodule 没有运行时依赖关系的程序集或 .netmodule。

.netmodules 由 MSVC 编译器使用 [/LN（创建 MSIL 模块）](ln-create-msil-module.md)创建，或由链接器使用 [/NOASSEMBLY（创建 MSIL 模块）](noassembly-create-a-msil-module.md)创建。 .objs 始终在 Visual C++ 编译中创建。 对于其他 Visual Studio 编译器，请使用“/target:module”编译器选项。

必须从创建 .netmodule 的 Visual C++ 编译中向链接器传递 .obj 文件。 不再支持传入 .netmodule，因为“/clr:pure”和“/clr:safe”编译器选项在 Visual Studio 2015 中已弃用，并且在 Visual Studio 2017 和更高版本中不受支持。

有关如何从命令行调用链接器的信息，请参阅[链接器命令行语法](linking.md)、[从命令行使用 MSVC 工具集](../building-on-the-command-line.md)以及[为命令行生成设置路径和环境变量](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

向链接器传递由 MSVC 编译器使用“/clr”编译的 .netmodule 或 .dll 文件可能导致链接器错误。 有关详细信息，请参阅[选择 .netmodule 输入文件的格式](choosing-the-format-of-netmodule-input-files.md)。

链接器接受本机 .obj 文件以及使用“/clr”编译的 MSIL .obj 文件。 在同一个生成中传递混合 .objs 时，所生成输出文件的可验证性级别将默认等于输入模块的最低可验证性级别。

如果您当前拥有由两个或更多程序集组成的应用程序，并且您希望该应用程序包含在一个程序集中，则必须对程序集进行重新编译，然后链接 .obj 或 .netmodule 以生成单个程序集。

创建可执行映像时，必须使用 [/ENTRY（入口点符号）](entry-entry-point-symbol.md)指定入口点。

与 MSIL .obj 或 .netmodule 文件链接时，请使用 [/LTCG（链接时代码生成）](ltcg-link-time-code-generation.md)，否则，当链接器遇到 MSIL .obj 或 .netmodule 时，它将重新启动与 /LTCG 的链接。

MSIL .obj 或 .netmodule 文件也可以传递到 cl.exe。

输入 MSIL 或 .obj .netmodule 文件不能有嵌入的资源。 使用 [/ASSEMBLYRESOURCE（嵌入托管资源）](assemblyresource-embed-a-managed-resource.md)链接器选项将资源嵌入到输出文件（模块或程序集）中，但在其他 Visual Studio 中，请使用“/resource”编译器选项嵌入资源。

执行 MSIL 链接时，如果还未指定 [/LTCG（链接时代码生成）](ltcg-link-time-code-generation.md)，将看到一条报告链接正在重新启动的信息性消息。 此消息可忽略，但若要通过 MSIL 链接提高链接器性能，请显式指定“/LTCG”。

## <a name="example"></a>示例

在 C++ 代码中，对于非系统异常，将调用相应的“try”的“catch”块。 但是，默认情况下，CLR 使用 <xref:System.Runtime.CompilerServices.RuntimeWrappedException> 包装非系统异常。 如果从 Visual C++ 和非 Visual C++ 模块创建程序集，并且希望在“try”块引发非系统异常时从其相应的“try”子句调用 C++ 代码中的“catch”块，则必须将 `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` 属性添加到非 C++ 模块的源代码中。

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

通过更改 `WrapNonExceptionThrows` 属性的布尔值，可以修改 Visual C++ 代码捕获非系统异常的能力。

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
