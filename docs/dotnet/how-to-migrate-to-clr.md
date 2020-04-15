---
title: 如何：迁移到 -clr
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 339b1f3172d8b82ece3e98f117f53ed399cbd4e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376070"
---
# <a name="how-to-migrate-to-clr"></a>如何：迁移到 /clr

本主题讨论使用 **/clr**编译本机代码时出现的问题（有关详细信息，请参阅[/clr（通用语言运行时编译）。](../build/reference/clr-common-language-runtime-compilation.md) **/clr**允许本机C++代码调用和调用从 .NET 程序集以及其他本机C++代码。 有关使用 **/clr**编译的优势的详细信息，请参阅[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)以及[本机和 .NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)。

## <a name="known-issues-compiling-library-projects-with-clr"></a>使用 /clr 编译库项目的已知问题

可视化工作室包含一些已知问题，在编译库项目与 **/clr**：

- 您的代码可能会在运行时使用[CRuntimeClass 查询类型：：fromName](../mfc/reference/cruntimeclass-structure.md#fromname)。 但是，如果类型位于 MSIL .dll 中（使用 **/clr**编译），则`FromName`调用 调用可能会失败，如果它发生在静态构造函数在托管 .dll 中运行之前（如果 FromName 调用是在托管 .dll 中执行代码之后发生的，则调用 该调用可能会失败。 要解决此问题，可以通过在托管 .dll 中定义函数、导出函数并从本机 MFC 应用程序调用它来强制构造托管静态构造函数。 例如：

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>使用可视化C++编译

在项目中的任何模块上使用 **/clr**之前，请首先编译本机项目并将其链接到 Visual Studio 2010。

以下步骤（按顺序执行）提供了 **/clr**编译的最简单路径。 在每个步骤之后编译和运行项目非常重要。

### <a name="versions-prior-to-visual-studio-2003"></a>Visual Studio 2003 之前的版本

如果要从 Visual Studio 2003 之前的版本升级到 Visual Studio 2010，您可能会在 Visual Studio 2003 中看到与增强C++标准符合性相关的编译器错误

### <a name="upgrading-from-visual-studio-2003"></a>从视觉工作室升级 2003

以前使用 Visual Studio 2003 构建的项目也应首先在没有 **/clr**的情况下编译，因为 Visual Studio 现在提高了 ANSI/ISO 合规性和一些重大更改。 可能需要最关注的更改是[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。 使用 CRT 的代码极可能生成弃用警告。 这些警告可以被抑制，但迁移到[新的 CRT 函数的安全增强版本](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)是首选，因为它们提供更好的安全性，并可能揭示代码中的安全问题。

### <a name="upgrading-from-managed-extensions-for-c"></a>从托管扩展升级C++

从 Visual Studio 2005 开始，使用托管扩展编写的C++代码将不会在 **/clr**下编译。

## <a name="convert-c-code-to-c"></a>将 C 代码转换为C++

尽管 Visual Studio 将编译 C 文件，但有必要将它们转换为**C++ 以进行 /clr**编译。 不需要更改实际的文件名;您可以使用 **/Tp（** 请参阅[/Tc、/Tp、/TC、/TP、/TP（指定源文件类型））](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)请注意，虽然 C++ 源代码文件是 **/clr**所必需的，但不必重新考虑代码以使用面向对象的范例。

当编译为C++文件时，C 代码很可能需要更改。 C++类型安全规则很严格，因此必须使用强制转换显式进行类型转换。 例如，malloc 返回 void 指针，但可以分配给具有强制转换的 C 中任何类型的指针：

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

函数指针在C++中也严格类型安全，因此以下 C 代码需要修改。 在C++最好创建定义函数指针类型的，`typedef`然后使用该类型对函数指针进行强制转换：

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++还要求在引用或调用函数之前，对函数进行原型设计或完全定义。

C 代码中使用的标识符恰好是C++中的关键字（如**虚拟**、**新**、**删除**、**布尔**、**真**、**假**等）必须重命名。 这通常可以通过简单的搜索和替换操作来完成。

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>重新配置项目设置

在 Visual Studio 2010 中编译和运行项目后，应为 **/clr**创建新的项目配置，而不是修改默认配置。 **/clr**与某些编译器选项不兼容，创建单独的配置允许您将项目构建为本机或托管。 在属性页对话框中选择 **/clr**时，将禁用与 **/clr**不兼容的项目设置（如果随后未选中 **/clr，** 则不会自动还原禁用选项）。

### <a name="create-new-project-configurations"></a>创建新项目配置

您可以使用 **"新建项目配置"对话框**中的 **"从复制设置"** 选项（**生成** > **配置管理器** > **活动解决方案配置** > **New）** 来基于现有项目设置创建项目配置。 对于调试配置执行此操作一次，对发布配置执行一次。 然后，后续更改只能应用于 **/clr**特定配置，保持原始项目配置不变。

使用自定义生成规则的项目可能需要格外注意。

此步骤对使用 makefiles 的项目具有不同的含义。 在这种情况下，可以配置单独的生成目标，也可以从原始副本创建特定于 **/clr**编译的版本。

### <a name="change-project-settings"></a>更改项目设置

**/clr**可以按照[/clr（通用语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)中的说明在开发环境中选择。 如前所述，此步骤将自动禁用冲突的项目设置。

> [!NOTE]
> 从 Visual Studio 2003 升级托管库或 Web 服务项目时 **，/Zl**编译器选项将添加到**命令行**属性页。 这将导致 LNK2001。 从**命令行**属性页中删除 **/Zl**以进行解析。 有关详细信息[，请参阅 /Zl（Omit 默认库名称）](../build/reference/zl-omit-default-library-name.md)和[设置编译器和生成属性](../build/working-with-project-properties.md)。 或者，将 msvcrt.lib 和 msvcmrt.lib 添加到链接器的附加**依赖项**属性。

对于使用 makefile 生成的项目，在添加 **/clr**后，必须手动禁用不兼容的编译器选项。 有关与 **/clr**不兼容的编译器选项的信息，请参阅[/ clr 限制](../build/reference/clr-restrictions.md)。

### <a name="precompiled-headers"></a>预编译标头

在 **/clr**下支持预编译标头。 但是，如果您只编译一些使用 **/clr**的 CPP 文件（将其余文件编译为本机），则需要进行一些更改，因为使用 **/clr**生成的预编译标头与在没有 **/clr**时生成的标头不兼容。 这种不兼容是由于 **/clr**生成和需要元数据。 因此，编译的**模块 /clr**不能使用不包含元数据的预编译标头，并且非 **/clr**模块不能使用包含元数据的预编译标头文件。

编译某些模块编译 **/clr**的项目的最简单方法是完全禁用预编译标头。 （在项目属性页对话框中，打开 C/C++ 节点，然后选择预编译标头。 然后，将"创建/使用预编译标头"属性更改为"不使用预编译标头"。

但是，特别是对于大型项目，预编译标头提供了更好的编译速度，因此禁用此功能是不可取的。 在这种情况下，最好将 **/clr**和非 **/clr**文件配置为使用单独的预编译标头。 这可以通过多选择要使用**解决方案资源管理器**编译**的模块/clr、** 右键单击组以及选择属性来分一步完成。 然后更改"通过文件创建/使用 PCH"和"预编译的标头文件"属性，分别使用不同的头文件名和 PCH 文件。

## <a name="fixing-errors"></a>修复错误

使用 **/clr**编译可能会导致编译器、链接器或运行时错误。 本节讨论最常见的问题。

### <a name="metadata-merge"></a>元数据合并

数据类型的不同版本可能导致链接器失败，因为为两种类型生成的元数据不匹配。 （这通常是在有条件地定义类型成员时造成的，但对于使用该类型的所有 CPP 文件的条件不同。在这种情况下，链接器失败，仅报告符号名称和定义类型的第二个 OBJ 文件的名称。 旋转将 OBJ 文件发送到链接器的顺序以发现数据类型的其他版本的位置通常很有用。

### <a name="loader-lock-deadlock"></a>装载机锁定死锁

可能发生"加载程序锁死锁"，但具有确定性，并在运行时检测到并报告。 有关详细的背景、指导和解决方案，请参阅[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)。

### <a name="data-exports"></a>数据导出

导出 DLL 数据容易出错，不建议导出数据。 这是因为 DLL 的数据部分不保证在 DLL 的某些托管部分执行之前进行初始化。 具有[#using指令](../preprocessor/hash-using-directive-cpp.md)的引用元数据。

### <a name="type-visibility"></a>类型可见性

默认情况下，本机类型是私有的。 这可能导致本机类型在 DLL 之外不可见。 通过添加到`public`这些类型来解决此错误。

### <a name="floating-point-and-alignment-issues"></a>浮点和对齐问题

`__controlfp`公共语言运行时不支持（有关详细信息[，请参阅_control87、_controlfp、_control87_2）。 \_](../c-runtime-library/reference/control87-controlfp-control87-2.md) CLR 也不会尊重[对齐](../cpp/align-cpp.md)。

### <a name="com-initialization"></a>COM 初始化

当模块初始化时，通用语言运行时会自动初始化 COM（当 COM 自动初始化时，它作为 MTA 进行初始化）。 因此，显式初始化 COM 会产生返回代码，指示 COM 已初始化。 当 CLR 已经将 COM 初始化到另一个线程模型时，尝试使用一个线程模型显式初始化 COM 可能会导致应用程序失败。

默认情况下，通用语言运行时将 COM 作为 MTA 启动;使用[/CLRTHREADATTRIBUTE（设置 CLR 线程属性）](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)来修改此。

### <a name="performance-issues"></a>性能问题

当间接调用生成到 MSIL 的本机C++方法（虚拟函数调用或使用函数指针）时，您可能会看到性能下降。 要了解有关此点的更多，请参阅[双汤。](../dotnet/double-thunking-cpp.md)

从本机移动到 MSIL 时，您会注意到工作集大小的增加。 这是因为通用语言运行时提供了许多功能，以确保程序正常运行。 如果 **/clr**应用程序运行不正常，您可能需要启用 C4793（默认情况下关闭），有关详细信息，请参阅[编译器警告（级别 1 和 3） C4793。](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)

### <a name="program-crashes-on-shutdown"></a>程序在关闭时崩溃

在某些情况下，CLR 可以在托管代码完成运行之前关闭。 使用`std::set_terminate``SIGTERM`和 可能会导致此。 有关详细信息[，请参阅信号常量](../c-runtime-library/signal-constants.md)和[set_terminate。](../c-runtime-library/abnormal-termination.md)

## <a name="using-new-visual-c-features"></a>使用新的视觉C++功能

在应用程序编译、链接和运行后，可以在使用 **/clr**编译的任何模块中使用 .NET 功能。 有关更多信息，请参见 [Component Extensions for Runtime Platforms](../extensions/component-extensions-for-runtime-platforms.md)。

有关 Visual C++ 中的 .NET 编程的信息，请参阅：

- [.NET 编程，带C++/CLI（视觉C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)

- [适用于运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>另请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
