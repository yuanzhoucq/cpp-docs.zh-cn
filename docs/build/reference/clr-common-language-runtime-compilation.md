---
title: "-clr （公共语言运行时编译） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a754e6c2fd8c709fd0397a2c0f78a7385819c586
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="clr-common-language-runtime-compilation"></a>/clr（公共语言运行时编译）
允许应用程序和组件使用公共语言运行时 (CLR) 中的功能。  
  
## <a name="syntax"></a>语法  
  
```  
/clr[:options]  
```  
  
## <a name="arguments"></a>参数  
 `options`  
 下列开关中的一个或多个（以逗号分隔）。  
  
 **/clr**  
 为应用程序创建元数据。 其他 CLR 应用程序可以使用该元数据，并且该应用程序也可以使用其他 CLR 组件的元数据中的类型和数据。  
  
 有关详细信息，请参见  
  
 [混合 （本机和托管） 程序集](../../dotnet/mixed-native-and-managed-assemblies.md)和  
  
 [How to: Migrate to /clr](../../dotnet/how-to-migrate-to-clr.md)。  
  
 **/clr:pure**  
 /clr:pure 已弃用。 未来版本的编译器可能不支持此选项。 建议移植对 C# 来说必须是纯 MSIL 的代码。  
  
 **/clr:safe**  
 /clr:safe 已弃用。 未来版本的编译器可能不支持此选项。 我们建议你移植必须是对 C# 的安全 MSIL 的代码。 
  
 **/clr:noAssembly**  
 指定不应将程序集清单插入输出文件中。 默认情况下， **noAssembly** 选项是无效的。  
  
 **NoAssembly** 选项已弃用。 请改用 [/LN (Create MSIL Module)](../../build/reference/ln-create-msil-module.md) 。  
  
 清单中不具有程序集元数据的托管程序称为 *“模块”*。 **noAssembly** 选项只能用于生成模块。 如果使用 [/c](../../build/reference/c-compile-without-linking.md) 和 **/clr:noAssembly**进行编译，请在创建模块的链接器阶段指定 [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) 选项。  
  
 在低于 Visual C++ 2005 的版本中， **/clr:noAssembly** 需要 **/LD**。 现在，指定**/LD** 时即暗含 **/LD**。  
  
 **/clr:initialAppDomain**  
 允许 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 应用程序在 CLR 版本 1 上运行。 如果你使用**initialAppDomain**，那么你可能会看到的一些问题中所述[BUG: AppDomainUnloaded 异常使用时托管 Visual c + + 组件扩展](http://go.microsoft.com/fwlink/p/?linkid=169465)的 microsoft支持网站。  
  
 使用 **initialAppDomain** 编译的应用程序不应由使用 ASP.NET 的应用程序使用，因为它在 CLR 版本 1 中不受支持 。  
  
 **/clr:nostdlib**  
 指示编译器忽略默认 \clr 目录。 如果包含 DLL 的多个版本（如 System.dll），则编译器将产生错误。 使用此选项可指定编译过程中要使用的特定框架。  
  
## <a name="remarks"></a>备注  
 托管代码是可以由 CLR 检查和管理的代码。 托管代码可以访问托管对象。 有关详细信息，请参阅 [/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
 有关如何开发定义和使用托管类型的应用程序的信息，请参阅 [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md)。  
  
 使用 **/clr** 编译的应用程序可以包含也可以不包含托管数据。  
  
 若要启用调试上托管的应用程序，请参阅[/ASSEMBLYDEBUG (添加 DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md)。  
  
 只有 CLR 类型会在垃圾回收堆上实例化。 有关详细信息，请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。 若要将函数编译为本机代码，请使用 `unmanaged` 杂注。 有关详细信息，请参阅[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。  
  
 默认情况下， **/clr** 是无效的。 当 **/clr** 有效时， **/MD** 也有效。 有关详细信息，请参阅 [/MD、/MT、/LD（使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)。 **/MD** 确保从标准头 (.h) 文件中选择动态链接的多线程版本运行时例程。 托管编程必须进行多线程处理，因为 CLR 垃圾回收器将在辅助线程中运行终结器。  
  
 如果通过使用编译**/c**，你可以指定与生成的输出文件的 CLR 类型[/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。  
  
 **/clr** 暗含 **/EHa**，且 **/clr** 不支持任何其他 **/EH**选项。 有关详细信息，请参阅 [/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)。  
  
 有关如何确定文件的 CLR 映像类型的信息，请参阅 [/CLRHEADER](../../build/reference/clrheader.md)。  
  
 传递给链接器给定调用的所有模块都必须使用相同的运行时编译器选项（**/MD** 或 **/LD**）进行编译。  
  
 使用 [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) 链接器选项以在程序集中嵌入资源。 [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)、 [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)和 [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 链接器选项也允许自定义程序集的创建方式。  
  
 使用 **/clr** 时， `_MANAGED` 符号定义为 1。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。  
  
 先初始化本机对象文件中的全局变量（如果可执行文件是 DLL，即在 DllMain 期间进行），再初始化托管部分的全局变量（在运行任何托管代码之前进行）。 `#pragma`[init_seg](../../preprocessor/init-seg.md)仅影响托管和非托管类别中的初始化顺序。  
  
## <a name="metadata-and-unnamed-classes"></a>元数据和未命名类  
 未命名类将出现在按以下方式命名的元数据中： `$UnnamedClass$`*crc-of-current-file-name*`$`*index*`$`，其中 *index* 是未命名类在编译中的顺序计数。 例如，下面的代码示例将在元数据中生成一个未命名类。  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 使用 ildasm.exe 查看元数据。  
  
## <a name="managed-extensions-for-c"></a>C++ 托管扩展  
 Visual C++ 不再支持 **/clr:oldsyntax** 选项。 此选项在 Visual Studio 2005 中已弃用。 使用 C++ 编写托管代码所支持的语法是 C++/CLI。 有关更多信息，请参见 [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md)。  
  
 如果具有使用 Managed Extensions for C++ 的代码，建议将其移植为使用 C++/CLI 语法。 有关如何移植代码的信息，请参阅 [C++/CLI Migration Primer](../../dotnet/cpp-cli-migration-primer.md)。  
  
#### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项  
  
1.  在 **“解决方案资源管理器”**中，右键单击项目名，然后选择 **“属性”** 以打开项目的 **“属性页”** 对话框。  
  
2.  选择 **“配置属性”** 文件夹。  
  
3.  在 **“常规”** 属性页上，修改 **“公共语言运行时支持”** 属性。  
  
    > [!NOTE]
    >  在“属性页”对话框中启用 **/clr** 时，还将根据需要调整与 **/clr** 不兼容的编译器选项属性。  例如，如果设置了 **/RTC** ，又启用了 **/clr** ，则将关闭 **/RTC** 。  
    >   
    >  此外，当调试**/clr**应用程序，来设置**调试器类型**属性**混合**或**仅限托管**。 有关详细信息，请参阅[用于 c + + 调试配置的项目设置](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)。  
  
     了解如何创建模块，请参阅[/NOASSEMBLY （创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md)。  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)