---
title: 如何： 将迁移到 clr |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5d7dafdc377723e33372529af1b8f125561366e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-to-clr"></a>如何：迁移到 /clr
本主题讨论了在编译本机代码时出现的问题 **/clr** (请参阅[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)有关详细信息)。 **/clr**允许 Visual c + + 模块调用和被调用在保留与非托管模块的兼容性的同时从.NET 程序集。 请参阅[混合 （本机和托管） 程序集](../dotnet/mixed-native-and-managed-assemblies.md)和[本机和.NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)有关详细信息进行编译的优点 **/clr**。  
  
## <a name="known-issues-compiling-library-projects-with-clr"></a>已知的问题编译库项目与 /clr  
 Visual Studio 包含的一些已知的问题，当编译库项目与 **/clr**:  
  
-   你的代码可能查询在运行时使用的类型[CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname)。 但是，如果某个类型的 MSIL.dll (使用编译 **/clr**)，调用`FromName`之前静态构造函数中托管的.dll 文件 （如果你将不看到此问题的代码后，会发生情况 FromName 调用运行时可能会失败在中执行托管.dll）。 若要解决此问题，你可以通过在托管的.dll 文件中定义函数、 导出它，并从本机 MFC 应用程序调用它强制托管的静态构造函数构造。 例如：  
  
    ```  
    // MFC extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## <a name="compile-with-visual-c"></a>Visual c + + 编译  
 在使用之前 **/clr**上你的项目中的任何模块，首次编译和链接使用 Visual Studio 2010 本机项目。  
  
 以下步骤中，遵循的顺序，提供的最简单路径 **/clr**编译。 很重要，若要编译并在每个步骤后运行你的项目。  
  
### <a name="versions-prior-to-visual-c-2003"></a>Visual c + + 2003年之前的版本  
 如果要从 Visual c + + 2003年之前的版本升级到 Visual Studio 2010，你可能会看到与 Visual c + + 2003年中增强的 c + + 标准一致性相关的编译器错误  
  
### <a name="upgrading-from-visual-c-2003"></a>从 Visual c + + 2003年升级  
 生成 Visual c + + 2003 中的项目以前应也应该首先编译而无需 **/clr**如 Visual Studio 现在增加了 ANSI/ISO 法规遵从性和一些重大更改。 可能需要最关注的更改是[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。 使用 CRT 的代码是很有可能会生成弃用警告。 这些警告可以禁止显示，但需要迁移到新[Security-Enhanced 版本的 CRT 函数](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)是首选方法，因为它们提供更佳的安全性，并且可能会泄露你的代码中的安全问题。  
  
### <a name="upgrading-from-managed-extensions-for-c"></a>C + + 托管扩展升级  
 启动 Visual Studio 2005 中，使用 Managed Extensions for c + + 编写的代码不会在下编译 **/clr**。  
  
## <a name="convert-c-code-to-c"></a>将 C 代码转换为 c + +  
 虽然 Visual Studio 将编译 C 文件，就必须将它们转换为用于 c + + **/clr**编译。 实际文件名无需更改;你可以使用 **/Tp** (请参阅[/Tc、 /Tp、 /TC、 /TP （指定源文件类型）](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。)请注意，尽管 c + + 源代码文件所需的 **/clr**，不需要重构代码以使用面向对象的范例。  
  
 C 代码是很有可能需要更改时编译为 c + + 文件。 C + + 类型安全规则非常严格，，因此必须显式的强制转换进行类型转换。 例如，malloc 返回 void 的指针，但可以分配给指向在 C 中使用强制转换的任何类型的指针：  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 函数指针也都是严格类型安全在 c + +，因此下面的 C 代码需要修改。 在 c + + 最好创建`typedef`，它定义的函数指针类型，并将该类型转换函数指针：  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C + + 还要求这些函数是原型或完全定义它们可以引用或调用之前。  
  
 在 C 代码中使用恰好是 c + + 中的关键字的标识符 (如`virtual`， `new`， `delete`， `bool`， `true`，`false`等) 必须重命名。 这通常可以使用简单的搜索和替换操作完成。  
  
 最后，而 C 样式 COM 调用需要显式使用 v-表和`this`指针，c + + 不：  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## <a name="reconfigure-project-settings"></a>重新配置项目设置  
 你的项目将编译并运行在 Visual Studio 2010 之后应创建新的项目配置为 **/clr**而不修改默认配置。 **/clr**与某些编译器选项不兼容，并创建单独的配置允许您为本机或托管将项目生成。 当 **/clr**在属性页对话框中，与不兼容的项目设置中选择 **/clr**已禁用 (和禁用的选项不会自动还原如果 **/clr**随后取消选择)。  
  
### <a name="create-new-project-configurations"></a>创建新的项目配置  
 你可以使用**从此处复制设置**选项[新项目配置对话框](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be)创建基于现有项目设置的项目配置。 执行此操作一次针对调试配置，第一次为发布配置。 然后，后续更改可以应用于 **/clr** -特定配置，使原始的项目配置保持不变。  
  
 使用自定义生成规则的项目可能需要特别小心。  
  
 此步骤有不同的含义，对于使用生成文件项目。 在此情况下，可以配置单独的 build 目标或特定于版本 **/clr**编译可以创建从原始的副本。  
  
### <a name="change-project-settings"></a>更改项目设置  
 **/clr**可以选择在开发环境中，按照中的说明[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。 如前所述，此步骤将自动禁用冲突的项目设置。  
  
> [!NOTE]
>  从 Visual c + + 2003 中，升级托管的库或 web 服务项目时 **/Zl**编译器选项将添加到**命令行**属性页。 这将导致 LNK2001。 删除 **/Zl**从**命令行**属性页后，可以解决。 请参阅[/Zl （省略默认库名）](../build/reference/zl-omit-default-library-name.md)和[使用项目属性](../ide/working-with-project-properties.md)有关详细信息。 或者，将 msvcrt.lib 和 msvcmrt.lib 添加到链接器的**附加依赖项**属性。  
  
 对于使用生成文件生成的项目，不兼容的编译器选项必须处于禁用状态手动一次 **/clr**添加。 请参阅 /[/clr 限制](../build/reference/clr-restrictions.md)有关与不兼容的编译器选项信息 **/clr**。  
  
### <a name="precompiled-headers"></a>预编译标头  
 预编译标头支持下 **/clr**。 但是，如果你仅编译的一些与你 CPP 文件 **/clr** （编译为本机 rest） 的某些更改需要因为预编译标头使用生成 **/clr**与那些不兼容无需生成 **/clr**。 此不兼容性是由于这样一个事实： **/clr**生成，并需要元数据。 已编译的模块 **/clr**因此可以不使用预编译标头不包含元数据，和非 **/clr**模块不能使用预编译标头文件包含元数据。  
  
 若要编译一些模块已编译的项目的最简单方法 **/clr**是完全禁用预编译标头。 （在项目属性页对话框中，打开 C/c + + 节点中，并选择预编译标头。 然后将更改的创建/使用预编译标头属性为"不使用预编译头"。）  
  
 但是，特别是对于大型项目中，预编译标头提供更好的编译速度，因此不需要禁用此功能。 在这种情况下最好配置 **/clr**和非 **/clr**文件以使用单独的预编译标头。 这可以通过一个步骤中选择多要编译的模块 **/clr**使用解决方案资源管理器、 右键单击组，并选择属性。 然后将更改的创建/使用 PCH 通过文件和预编译标头文件的属性，以分别使用不同的头文件的名称和 PCH 文件。  
  
## <a name="fixing-errors"></a>修复错误  
 使用编译 **/clr**可能会导致编译器、 链接器或运行时错误。 本部分讨论最常见的问题。  
  
### <a name="metadata-merge"></a>元数据合并  
 不同版本的数据类型可能会导致链接器失败，因为生成的两个类型的元数据不匹配。 （这通常被由于时有条件地定义类型的成员，但情况不是使用类型的所有 CPP 文件相同。）在这种情况下链接器失败时，报表仅的符号名称和定义该类型的第二个 OBJ 文件的名称。 通常它可用于旋转，OBJ 文件会发送到链接器以发现的数据类型的其他版本的位置的顺序。  
  
### <a name="loader-lock-deadlock"></a>加载程序锁死锁  
 在 Visual Studio 2010 及更高版本，如在早期版本，但确定性，并且仍会发生"加载程序锁死锁"检测到，并且在运行时报告。 请参阅[初始化混合程序集的](../dotnet/initialization-of-mixed-assemblies.md)的详细的背景、 指南和解决方案。  
  
### <a name="data-exports"></a>数据导出  
 导出 DLL 数据是容易出错且不建议这样做。 这是因为不能保证 DLL 的数据部分初始化之前已执行的 DLL 某些托管的部分。 引用元数据与[#using 指令](../preprocessor/hash-using-directive-cpp.md)。  
  
### <a name="type-visibility"></a>类型可见性  
 本机类型是私有的默认值。 这可能导致不可在 DLL 外可见的本机类型。 通过添加解决此错误`public`到这些类型。  
  
### <a name="floating-point-and-alignment-issues"></a>浮点和对齐方式问题  
 `__controlfp` 不支持公共语言运行时 (请参阅[_control87、 _controlfp、 \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)有关详细信息)。 CLR 将也不会考虑在[对齐](../cpp/align-cpp.md)。  
  
### <a name="com-initialization"></a>COM 初始化  
 公共语言运行时初始化 COM 自动初始化模块时 （在自动初始化 COM 时它还执行该操作作为 MTA）。 因此，显式初始化 COM 生成，该值指示 COM 已初始化的返回代码。 尝试显式初始化与一个线程处理模型 COM，CLR 已到另一个线程模型初始化 COM 时可能会导致应用程序失败。  
  
 公共语言运行时启动 COM MTA 作为默认设置。使用[/CLRTHREADATTRIBUTE （设置 CLR 线程特性）](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)若要修改此。  
  
### <a name="performance-issues"></a>性能问题  
 生成为 MSIL 的本机 c + + 方法间接调用时，你可能会看到性能降低 （虚函数调用或使用函数指针）。 若要了解详细信息，请参阅[双重形式转换](../dotnet/double-thunking-cpp.md)。  
  
 当从本机为 MSIL 时，你将注意到的工作集大小的增加。 这是因为公共语言运行时提供了许多功能，以确保该程序正确运行。 如果你 **/clr**应用程序未正确运行，但你可能想以便 C4793 （默认情况下关闭），请参阅[编译器警告 （等级 1 和 3） C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)有关详细信息。  
  
### <a name="program-crashes-on-shutdown"></a>在关闭程序崩溃  
 在某些情况下，CLR 可以关闭，在完成你的托管的代码之前运行。 使用`std::set_terminate`和`SIGTERM`可能导致此。 请参阅[signal 常量](../c-runtime-library/signal-constants.md)和[set_terminate](../c-runtime-library/abnormal-termination.md)有关详细信息。  
  
## <a name="using-new-visual-c-features"></a>使用新的 Visual c + + 功能  
 在应用程序编译、 链接和运行之后, 可以开始使用编译的任何模块中使用.NET 功能 **/clr**。 有关详细信息，请参阅[运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。  
  
 如果用于 c + + 托管扩展，你可以转换你的代码以使用新的语法。 有关转换为 c + + 托管扩展的详细信息，请参阅[C + + /cli 迁移入门](../dotnet/cpp-cli-migration-primer.md)。  
  
 在 Visual c + + 编程的.NET 上的信息请参阅：  
  
-   [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)  
  
## <a name="see-also"></a>请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)