---
title: "用作链接器输入的 .netmodule 文件 | Microsoft Docs"
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
  - ".netmodules"
  - "链接 [C++], 模块"
  - "模块, Visual C++"
  - "MSIL 链接"
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用作链接器输入的 .netmodule 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

link.exe 现在接受 MSIL .obj 和 .netmodules 作为输入。  链接器生成的输出文件是程序集还是 .netmodule 不在输入到链接器的"运行时依赖关系，任何或 .obj .netmodules。  
  
 .netmodules 上的运行时依赖项，.netmodules 由 Visual C\+\+ 编译器通过 [\/LN（创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)或由链接器通过 [\/NOASSEMBLY（创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md) 创建。.objs 始终在 Visual C\+\+ 编译中创建。  对于其他 Visual Studio 编译器，请使用 **\/target:module** 编译器选项。  
  
 在大多数情况下，您会需要向链接器传递来自创建 .netmodule 的 Visual C\+\+ 编译的 .obj 文件，除非创建具有 .netmodule，[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  链接器输入的MSIL .netmodules 必须是纯 MSIL，它可通过使用 **\/clr:safe** 由 Visual C\+\+ 编译器生成。  默认情况下，其他 Visual Studio 编译器均生成纯 MSIL 模块。  
  
 有关如何从命令行调用链接器的信息，请参见 [链接器命令行语法](../../build/reference/linker-command-line-syntax.md) 和 [为命令行生成设置路径和环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 传递一个netmodule 或 .dll 文件传递到由 Visual C\+\+ 编译器使用 **\/clr** 或 **\/clr:pure** 编译的链接器可能导致链接器错误。  有关详细信息，请参阅[选择 .netmodule 输入文件的格式](../../build/reference/choosing-the-format-of-netmodule-input-files.md)。  
  
 链接器接受本机 .obj 文件以及使用 **\/clr**、**\/clr:pure** 或 **\/clr:safe** 编译的 MSIL .obj 文件。  在相同版本中传递混合 .obj 时，默认情况下，得到的输出文件的可验证性等于输入模块的最低级别可验证性。  例如，如果向链接器传递安全的纯 .obj，则输出文件将为纯 .obj。  需要时，可通过 [\/CLRIMAGETYPE（指定 CLR 映像的类型）](../../build/reference/clrimagetype-specify-type-of-clr-image.md) 指定较低级别的可验证性。  
  
 如果当前的应用程序由两个或更多的程序集组成，并且您希望该应用程序包含在一个程序集中，则必须对程序集进行重新编译，然后链接 .obj 或 .netmodules用来生成一个单独程序集。  
  
 创建可执行映像时，必须使用 [\/ENTRY（入口点符号）](../../build/reference/entry-entry-point-symbol.md) 指定入口点。  
  
 当链接包含 MSIL 或 .obj .netmodule 文件时，请使用 [\/LTCG（链接时代码生成）](../../build/reference/ltcg-link-time-code-generation.md)，否则，当链接器遇到 MSIL 或 .obj .netmodule 时，它将重新启动带 \/LTCG 的链接。  
  
 MSIL .obj or .netmodule 文件也可以传递到 cl.exe。  
  
 输入 MSIL 或 .obj .netmodule 文件不能有嵌入的资源。  在其他 Visual Studio 编译器中使用 [\/ASSEMBLYRESOURCE（嵌入托管资源）](../../build/reference/assemblyresource-embed-a-managed-resource.md) 链接器选项或 **\/resource** 编译器选项将资源嵌入到输出文件（模块或程序集）中。  
  
 当执行 MSIL 链接时，如果未同时指定 [\/LTCG（链接时代码生成）](../../build/reference/ltcg-link-time-code-generation.md)，则将出现一则信息性消息，报告正在重新启动链接。  此消息可忽略，但要通过 MSIL 链接提高链接器性能，请显式指定 **\/LTCG**。  
  
## 示例  
 在 C\+\+ 代码中，将针对非系统异常调用对应 try 的 catch 块。  但是，默认情况下，CLR 将用 <xref:System.Runtime.CompilerServices.RuntimeWrappedException> 包装非系统异常。  如果程序集是从 Visual C\+\+ 和非 Visual C\+\+ 模块创建的，而且您希望在 try 块引发非系统异常时，从 C\+\+ 代码中相应的 try 子句调用 catch 块，则必须将  
  
 \[assembly:System::Runtime::CompilerServices::RuntimeCompatibility\(WrapNonExceptionThrows\=false\)\] 特性添加到非 C\+\+ 模块的源代码中。  
  
```  
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
  
## 示例  
 通过更改 WrapNonExceptionThrows 特性的布尔值，可以修改 Visual C\+\+ 代码的功能以捕获非系统异常。  
  
```  
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
  
  **在 C\+\+ 源代码文件中捕获非系统异常**   
## 请参阅  
 [LINK 输入文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)