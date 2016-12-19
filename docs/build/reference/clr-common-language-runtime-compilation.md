---
title: "-clr（公共语言运行时编译） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLR"
  - "VC.Project.VCNMakeTool.CompileAsManaged"
  - "VC.Project.VCCLCompilerTool.CompileAsManaged"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 公共语言运行时选项"
  - "-clr 编译器选项 [C++]"
  - "clr 编译器选项 [C++]"
  - "/clr 编译器选项 [C++]"
  - "C++ 托管扩展, 编译"
  - "公共语言运行时, /clr 编译器选项"
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
caps.latest.revision: 72
caps.handback.revision: 72
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /clr（公共语言运行时编译）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许应用程序和组件使用公共语言运行时 \(CLR\) 中的功能。  
  
## 语法  
  
```  
/clr[:options]  
```  
  
## 参数  
 `options`  
 下列开关中的一个或多个（以逗号分隔）。  
  
 **\/clr**  
 为应用程序创建元数据。 其他 CLR 应用程序可以使用该元数据，并且该应用程序也可以使用其他 CLR 组件的元数据中的类型和数据。  
  
 有关详细信息，请参见  
  
 [混合（本机和托管）程序集](../../dotnet/mixed-native-and-managed-assemblies.md) 和  
  
 [如何：迁移到 \/clr](../../dotnet/how-to-migrate-to-clr.md)。  
  
 **\/clr:pure**  
 生成不包含本机可执行代码的仅 Microsoft 中间语言 \(MSIL\) 输出文件。 但是，它可以包含编译为 MSIL 的本机类型。  
  
 有关详细信息，请参阅[纯代码和可验证代码](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 \/clr:pure 已弃用。 未来版本的编译器可能不支持此选项。 建议移植对 C\# 来说必须是纯 MSIL 的代码。  
  
 **\/clr:safe**  
 生成仅 MSIL（非本机可执行代码）可验证输出文件。**\/clr:safe** 启用验证诊断（[PEVerify 工具 \(Peverify.exe\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md)）。  
  
 有关详细信息，请参阅 [NIB：编写可验证类型安全代码](http://msdn.microsoft.com/zh-cn/d18f10ef-3b48-4f47-8726-96714021547b)。  
  
 \/clr:safe 已弃用。 未来版本的编译器可能不支持此选项。 建议移植对 C\# 来说必须是可验证的纯 MSIL 的代码。  
  
 **\/clr:noAssembly**  
 指定不应将程序集清单插入输出文件中。 默认情况下，**noAssembly** 选项是无效的。  
  
 **NoAssembly** 选项已弃用。 请改用 [\/LN（创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)。  
  
 清单中不具有程序集元数据的托管程序称为*“模块”*。**noAssembly** 选项只能用于生成模块。 如果使用 [\/c](../../build/reference/c-compile-without-linking.md) 和 **\/clr:noAssembly** 进行编译，请在创建模块的链接器阶段指定 [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) 选项。  
  
 在低于 Visual C\+\+ 2005 的版本中，**\/clr:noAssembly** 需要 **\/LD**。 现在，指定 **\/clr:noAssembly** 时即暗含 **\/LD**。  
  
 **\/clr:initialAppDomain**  
 允许 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 应用程序在 CLR 版本 1 上运行。 如果使用 **initialAppDomain**，那么你可能会看到在 Microsoft 支持网站上的 [BUG：在使用 Visual C\+\+ 组件的托管扩展时发生 AppDomainUnloaded 异常](http://go.microsoft.com/fwlink/?LinkID=169465)中讨论的一些问题。  
  
 使用 **initialAppDomain** 编译的应用程序不应由使用 ASP.NET 的应用程序使用，因为它在 CLR 版本 1 中不受支持 。  
  
 **\/clr:nostdlib**  
 指示编译器忽略默认 \\clr 目录。 如果包含 DLL 的多个版本（如 System.dll），则编译器将产生错误。 使用此选项可指定编译过程中要使用的特定框架。  
  
## 备注  
 托管代码是可以由 CLR 检查和管理的代码。 托管代码可以访问托管对象。 有关详细信息，请参阅[\/clr 限制](../../build/reference/clr-restrictions.md)。  
  
 有关如何开发定义和使用托管类型的应用程序的信息，请参阅 [适用于运行时平台的组件扩展](../../windows/component-extensions-for-runtime-platforms.md)。  
  
 使用 **\/clr** 编译的应用程序可以包含也可以不包含托管数据。  
  
 若要在托管应用程序上启用调试，请参阅 [\/ASSEMBLYDEBUG（添加 DebuggableAttribute）](../../build/reference/assemblydebug-add-debuggableattribute.md)。  
  
 只有 CLR 类型会在垃圾回收堆上实例化。 有关更多信息，请参见[类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)。 若要将函数编译为本机代码，请使用 `unmanaged` 杂注。 有关详细信息，请参阅[managed、unmanaged](../../preprocessor/managed-unmanaged.md)。  
  
 默认情况下，**\/clr** 是无效的。 当 **\/clr** 有效时，**\/MD** 也有效。 有关详细信息，请参阅[\/MD、\/MT、\/LD（使用运行库）](../../build/reference/md-mt-ld-use-run-time-library.md)。**\/MD** 确保从标准头 \(.h\) 文件中选择动态链接的多线程版本运行时例程。 托管编程必须进行多线程处理，因为 CLR 垃圾回收器将在辅助线程中运行终结器。  
  
 如果使用 **\/c** 进行编译，可以通过 [\/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md) 指定生成输出文件的 CLR 映像类型（IJW 映像、安全映像或纯映像）。  
  
 **\/clr** 暗含 **\/EHa**，且 **\/clr** 不支持任何其他 **\/EH** 选项。 有关详细信息，请参阅[\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)。  
  
 有关如何确定文件的 CLR 映像类型的信息，请参阅 [\/CLRHEADER](../../build/reference/clrheader.md)。  
  
 传递给链接器给定调用的所有模块都必须使用相同的运行时编译器选项（**\/MD** 或 **\/LD**）进行编译。  
  
 使用 [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) 链接器选项以在程序集中嵌入资源。[\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)、[\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) 和 [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 链接器选项也允许自定义程序集的创建方式。  
  
 使用 **\/clr** 时，`_MANAGED` 符号定义为 1。 有关更多信息，请参见[预定义的宏](../../preprocessor/predefined-macros.md)。  
  
 先初始化本机对象文件中的全局变量（如果可执行文件是 DLL，即在 DllMain 期间进行），再初始化托管部分的全局变量（在运行任何托管代码之前进行）。`#pragma`[init\_seg](../../preprocessor/init-seg.md) 仅影响托管和非托管类别中的初始化顺序。  
  
 使用 **\/clr:safe** 进行编译相当于在 C\# 等语言中使用 [\/platform:anycpu](../Topic/-platform%20\(C%23%20Compiler%20Options\).md) 进行编译。  
  
## 安全映像和纯映像  
 纯映像使用 CLR 版本的 C 运行时 \(CRT\) 库。 但 CRT 不可验证，因此使用 **\/clr:safe** 进行编译时不能使用 CRT。 有关详细信息，请参阅[CRT 库功能](../../c-runtime-library/crt-library-features.md)。  
  
 不能出现在纯映像中的本机代码的示例包括内联程序集、[setjmp](../../c-runtime-library/reference/setjmp.md) 和 [longjmp](../../c-runtime-library/reference/longjmp.md)。  
  
 纯映像或安全映像的每个入口点都是托管的。 使用 **\/clr** 进行编译时，入口点在本机。 有关详细信息，请参阅[\_\_clrcall](../../cpp/clrcall.md)。  
  
 使用 **\/clr:safe** 进行编译时，变量默认为 [appdomain](../../cpp/appdomain.md) 且不能是按进程的。 对于 **\/clr:pure**，尽管默认为 **appdomain**，但仍可使用 [process](../../cpp/process.md) 变量。  
  
 当运行在 64 位操作系统上使用 **\/clr** 或 **\/clr:pure** 进行编译的 32 位 .exe 文件时，该应用程序将在 WOW64 下运行，这使得 32 位应用程序能够在 64 位操作系统中的 32 位 CLR 上运行。 默认情况下，使用 **\/clr:safe** 编译的 .exe 文件将在运行 64 位操作系统的计算机中的 64 位 CLR 上运行。 （在 32 位操作系统中，相同的 .exe 文件将在 32 位 CLR 上运行。） 但是，安全应用程序可以加载 32 位组件。 在这种情况下，加载 32 位应用程序时，在 64 位操作系统支持下运行的安全映像将失败 \(BadFormatException\)。 为确保在加载 32 位映像时安全映像继续在 64 位操作系统上运行，必须使用 [\/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md) 来更改元数据 \(.corflags\)，并将其标记为在 WOW64 下运行。 以下命令行是一个示例。 （替换你自己的输入符号。）  
  
 **cl \/clr:safe t.cpp \/link \/clrimagetype:pure \/entry:?main@@$$HYMHXZ \/subsystem:console**  
  
 有关如何获取修饰名的信息，请参阅[修饰名](../../build/reference/decorated-names.md)。 有关 64 位编程的详细信息，请参阅[配置 64 位的程序](../../build/configuring-programs-for-64-bit-visual-cpp.md)。 有关使用纯 CLR 代码的信息，请参阅[如何：迁移到 \/clr:pure](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md) 和[纯代码和可验证代码](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## 元数据和未命名类  
 未命名类将出现在按以下方式命名的元数据中：`$UnnamedClass$`*crc\-of\-current\-file\-name*`$`*index*`$`，其中 *index* 是未命名类在编译中的顺序计数。 例如，下面的代码示例将在元数据中生成一个未命名类。  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 使用 ildasm.exe 查看元数据。  
  
## C\+\+ 托管扩展  
 Visual C\+\+ 不再支持 **\/clr:oldsyntax** 选项。 此选项在 Visual Studio 2005 中已弃用。 使用 C\+\+ 编写托管代码所支持的语法是 C\+\+\/CLI。 有关更多信息，请参见[适用于运行时平台的组件扩展](../../windows/component-extensions-for-runtime-platforms.md)。  
  
 如果具有使用 Managed Extensions for C\+\+ 的代码，建议将其移植为使用 C\+\+\/CLI 语法。 有关如何移植代码的信息，请参阅 [C\+\+\/CLI 迁移入门](../../dotnet/cpp-cli-migration-primer.md)。  
  
#### 在 Visual Studio 中设置此编译器选项  
  
1.  在**“解决方案资源管理器”**中，右键单击项目名，然后选择**“属性”**以打开项目的**“属性页”**对话框。  
  
2.  选择**“配置属性”**文件夹。  
  
3.  在**“常规”**属性页上，修改**“公共语言运行时支持”**属性。  
  
    > [!NOTE]
    >  在“属性页”对话框中启用 **\/clr** 时，还将根据需要调整与 **\/clr** 不兼容的编译器选项属性。 例如，如果设置了 **\/RTC**，又启用了 **\/clr**，则将关闭 **\/RTC**。  
    >   
    >  此外，调试 **\/clr** 应用程序时，请将“调试器类型”属性设置为“混合”或“仅限托管”。 有关更多信息，请参见[C\+\+ 调试配置的项目设置](../Topic/Project%20Settings%20for%20a%20C++%20Debug%20Configuration.md)。  
  
     有关如何创建模块的信息，请参阅 [\/NOASSEMBLY（创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md)。  
  
#### 以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)