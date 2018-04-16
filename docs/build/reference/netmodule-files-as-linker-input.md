---
title: "用作链接器输入的.netmodule 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1c30c56012dc14392ecdc6a089dcd88a217d6d8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="netmodule-files-as-linker-input"></a>用作链接器输入的 .netmodule 文件
link.exe 现在接受 MSIL .obj 和 .netmodule 作为输入。 链接器生成的输出文件将是一个与输入到链接器的任何 .obj 或 .netmodule 没有运行时依赖关系的程序集或 .netmodule。  
  
 .netmodule 文件由带有的 Visual c + + 编译器[/LN （创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)或通过使用链接器[/NOASSEMBLY （创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md)。 .obj 始终是在 Visual c + + 编译中创建的。 对于其他 Visual Studio 编译器中，使用**/target: module**编译器选项。  
  
  你将需要将传递给链接器.obj 文件中，从创建.netmodule 的 Visual c + + 编译。 不再支持.netmodule 传入，因为**/clr: pure**和**/clr: safe**编译器选项在 Visual Studio 2015 中弃用，并将编译器的未来版本中删除。   
  
 有关如何以调用从命令行链接器的信息，请参阅[链接器命令行语法](../../build/reference/linker-command-line-syntax.md)，[命令行上的生成 C/c + + 代码](../../build/building-on-the-command-line.md)，和[设置的路径和环境变量命令行生成](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 到链接器传递的.netmodule 或.dll 文件进行编译使用 Visual c + + 编译器**/clr**可能会导致链接器错误。 有关详细信息，请参阅[选择.netmodule 输入文件的格式](../../build/reference/choosing-the-format-of-netmodule-input-files.md)。  
  
 链接器接受本机.obj 文件，以及编译的 MSIL 的.obj 文件**/clr**。 在相同的版本中传递混合的.obj 时, 生成的输出文件的可验证性，默认情况下，将等于输入模块的可验证性的最低级别。 
  
 如果您当前拥有由两个或更多程序集组成的应用程序，并且您希望该应用程序包含在一个程序集中，则必须对程序集进行重新编译，然后链接 .obj 或 .netmodule 以生成单个程序集。  
  
 必须指定入口点使用[/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)时创建的可执行映像。  
  
 当链接 MSIL.obj 或.netmodule 文件，使用[/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)，否则当链接器遇到的 MSIL.obj 或.netmodule 时，它将重新启动具有 /LTCG 的链接。  
  
 MSIL .obj 或 .netmodule 文件也可以传递到 cl.exe。  
  
 输入 MSIL 或 .obj .netmodule 文件不能有嵌入的资源。 与输出文件 （模块或程序集） 中嵌入的资源[/ASSEMBLYRESOURCE （嵌入托管资源）](../../build/reference/assemblyresource-embed-a-managed-resource.md)链接器选项或与**/resource**在其他 Visual Studio 编译器中的编译器选项。  
  
 当执行 MSIL 链接，并不同时指定[/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)，你将看到信息性消息，报告链接正在重新启动。 此消息可以忽略，但若要提高链接器性能通过 MSIL 链接、 显式指定**/LTCG**。  
  
## <a name="example"></a>示例  
 在 c + + 代码中的对应 try catch 块将调用为非系统异常。 但是，默认情况下，CLR 包装非系统异常<xref:System.Runtime.CompilerServices.RuntimeWrappedException>。 当从 Visual c + + 创建程序集和非 Visual c + + 模块，而您希望在 c + + 代码时 try 块引发非系统异常时，必须添加要调用从其相应的重试子句的 catch 块  
  
 [assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)] 特性应用到非 c + + 模块的源代码。  
  
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
  
## <a name="example"></a>示例  
 通过更改 WrapNonExceptionThrows 属性的布尔值，你可以修改 Visual c + + 代码能够捕捉非系统的异常。  
  
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
  
```Output  
caught non System exception in C++ source code file  
```  
  
## <a name="see-also"></a>请参阅  
 [LINK 输入的文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)