---
title: 如何：迁移到-clr
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
ms.openlocfilehash: 337dc69b60537fba8484837981fc6be0971c69cb
ms.sourcegitcommit: 40ffe764244784c715b086c79626ac390b855d47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "79544482"
---
# <a name="how-to-migrate-to-clr"></a>如何：迁移到 /clr

本主题讨论用 **/clr**编译本机代码时引发的问题（有关详细信息，请参阅[/Clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) ）。 **/clr**除了其他C++本机C++代码外，还允许从 .net 程序集调用和调用本机代码。 有关通过 **/clr**进行编译的优点的详细信息，请参阅[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)以及[本机和 .net 互操作性](../dotnet/native-and-dotnet-interoperability.md)。

## <a name="known-issues-compiling-library-projects-with-clr"></a>用/clr 编译库项目的已知问题

Visual Studio 在通过 **/clr**编译库项目时包含一些已知问题：

- 你的代码可以在运行时通过[CRuntimeClass：： FromName](../mfc/reference/cruntimeclass-structure.md#fromname)查询类型。 但是，如果某一类型位于 MSIL （使用 **/clr**编译的）中，则对 `FromName` 的调用可能会失败（如果它在托管 .dll 中运行之前出现，则不会出现此问题，如果在托管 .dll 中执行了代码，则将不会出现此问题）。 若要解决此问题，可以通过以下方式强制构造托管静态构造函数：在托管 .dll 中定义一个函数，将该函数导出，并从本机 MFC 应用程序调用它。 例如：

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>用视觉对象编译C++

在项目中的任何模块上使用 **/clr**之前，请先使用 Visual Studio 2010 编译和链接本机项目。

按照顺序执行以下步骤，为 **/clr**编译提供最简单的路径。 在上述每个步骤后编译和运行项目很重要。

### <a name="versions-prior-to-visual-studio-2003"></a>Visual Studio 2003 之前的版本

如果要从 Visual studio 2003 之前的版本升级到 Visual Studio 2010，可能会看到与 Visual Studio 中的增强C++标准一致性相关的编译器错误2003

### <a name="upgrading-from-visual-studio-2003"></a>从 Visual Studio 2003 升级

以前用 Visual Studio 2003 生成的项目还应该首先进行编译（不带 **/clr** ），因为 Visual studio 现已增加 ANSI/ISO 相容性和一些重大更改。 最需要注意的更改是[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。 使用 CRT 的代码很可能会产生弃用警告。 可以禁止显示这些警告，但最好是迁移到新的[安全增强版本的 CRT 函数](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)，因为它们提供了更好的安全性，并可能会揭示代码中的安全问题。

### <a name="upgrading-from-managed-extensions-for-c"></a>从的托管扩展升级C++

从 Visual Studio 2005 开始，不会在 **/clr**下编译C++用托管扩展编写的代码。

## <a name="convert-c-code-to-c"></a>将 C 代码转换为C++

尽管 Visual Studio 将编译 C 文件，但需要将其转换为才能C++进行 **/clr**编译。 不需要更改实际文件名;可以使用 **/tp** （请参阅[/tc、/tp、/tc、/Tp （指定源文件类型）](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。）请注意， C++尽管 **/clr**需要源代码文件，但并不需要将代码重新因式分解为使用面向对象的模式。

在编译为C++文件时，C 代码很可能需要更改。 类型C++安全规则是严格的，因此必须通过强制转换使类型转换成为显式的。 例如，malloc 返回 void 指针，但可以使用强制转换将其分配给 C 中任何类型的指针：

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

函数指针在中C++是严格的类型安全的，因此需要修改以下 C 代码。 在C++这种情况下，最好创建一个定义函数指针类型的 `typedef`，然后使用该类型强制转换函数指针：

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++还要求函数具有原型或完全定义，然后才能引用或调用。

必须C++重命名发生在 C 代码中的标识符（如**virtual**、 **new**、 **delete**、 **bool**、 **true**、 **false**等）。 通常可以通过简单的搜索和替换操作来实现此目的。

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>重新配置项目设置

项目在 Visual Studio 2010 中编译和运行后，应为 **/clr**创建新的项目配置，而不是修改默认配置。 **/clr**与一些编译器选项不兼容，创建单独的配置使你可以将项目生成为本机或托管。 当在 "属性页" 对话框中选择 " **/clr** " 时，将禁用与 **/clr**不兼容的项目设置（如果随后取消选择 **/clr** ，则不会自动还原已禁用的选项）。

### <a name="create-new-project-configurations"></a>创建新的项目配置

您可以使用 "**新建项目配置" 对话框**中的 "**复制设置**" 选项（"**生成**" > **Configuration Manager** > **活动解决方案配置**" > **新建**"）来基于现有项目设置创建项目配置。 为调试配置执行此操作一次，对发布配置执行此操作。 之后的更改只能应用于特定于 **/clr**的配置，而保留原始项目配置不变。

使用自定义生成规则的项目可能需要特别注意。

对于使用生成程序的项目，此步骤具有不同的含义。 在这种情况下，可以配置单独的生成目标，或者可以从原始的副本创建特定于 **/clr**编译的版本。

### <a name="change-project-settings"></a>更改项目设置

按照[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)中的说明，可以在开发环境中选择 **/clr** 。 如前所述，此步骤会自动禁用冲突的项目设置。

> [!NOTE]
>  从 Visual Studio 2003 升级托管库或 web 服务项目时，将在 "**命令行**" 属性页中添加 " **/zl**编译器" 选项。 这将导致 LNK2001。 从 "**命令行**" 属性页中删除 **/zl**以解析。 有关详细信息，请参阅[/zl （省略默认库名称）](../build/reference/zl-omit-default-library-name.md)和[设置编译器和生成属性](../build/working-with-project-properties.md)。 或者，将 msvcrt.lib 和 msvcmrt.lib 添加到链接器的**附加依赖项**属性。

对于用生成程序生成的项目，添加 **/clr**后必须手动禁用不兼容的编译器选项。 有关与 **/clr**不兼容的编译器选项的信息，请参阅/[/clr 限制](../build/reference/clr-restrictions.md)。

### <a name="precompiled-headers"></a>预编译标头

在 **/clr**下支持预编译头。 但是，如果只用 **/clr**编译部分 CPP 文件（将 rest 编译为本机），则需要进行一些更改，因为随 **/clr**一起生成的预编译头与没有 **/clr**生成的预编译头不兼容。 这种不兼容性的原因是 **/clr**生成并需要元数据。 因此，编译的 **/clr**模块不能使用未包含元数据的预编译标头，并且非 **/clr**模块不能使用包含元数据的预编译头文件。

若要编译某个项目（其中某些模块编译为 **/clr** ），最简单的方法是完全禁用预编译头。 （在 "项目属性页" 对话框中，打开 CC++ /节点，然后选择 "预编译头"。 然后，将 "创建/使用预编译标头" 属性更改为 "不使用预编译标头"。）

但是，尤其是对于大型项目，预编译标头提供更好的编译速度，因此不需要禁用此功能。 在这种情况下，最好将 **/clr**和非 **/clr**文件配置为使用单独的预编译头。 为此，可以使用以下方法之一执行此操作：多重选择**要使用** **解决方案资源管理器**编译的模块，右键单击该组，然后选择 "属性"。 然后，将 "创建/使用 PCH 到文件" 和 "预编译头文件" 属性分别更改为使用不同的标头文件名称和 PCH 文件。

## <a name="fixing-errors"></a>修复错误

用 **/clr**编译可能导致编译器、链接器或运行时错误。 本部分讨论最常见的问题。

### <a name="metadata-merge"></a>元数据合并

不同版本的数据类型可能会导致链接器失败，因为为这两个类型生成的元数据不匹配。 （这通常是在按条件定义类型的成员时导致的，但对于使用该类型的所有 CPP 文件而言，条件并不相同。）在这种情况下，链接器将失败，只报告符号名称和定义了该类型的第二个 OBJ 文件的名称。 通常，可以将 OBJ 文件发送到链接器的顺序旋转，以发现其他版本的数据类型的位置。

### <a name="loader-lock-deadlock"></a>加载程序锁死锁

"加载程序锁死锁" 可能发生，但却是确定性的，并且在运行时检测和报告。 有关详细背景、指南和解决方案，请参阅[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)。

### <a name="data-exports"></a>数据导出

导出 DLL 数据容易出错，不建议使用。 这是因为在执行 DLL 的某个托管部分之前，不能保证初始化 DLL 的数据部分。 用[#using 指令](../preprocessor/hash-using-directive-cpp.md)引用元数据。

### <a name="type-visibility"></a>类型可见性

本机类型默认为私有类型。 这可能导致本机类型在 DLL 外不可见。 通过向这些类型添加 `public` 来解决此错误。

### <a name="floating-point-and-alignment-issues"></a>浮点和对齐问题

公共语言运行时不支持 `__controlfp` （有关详细信息[，请参阅 _control87、_controlfp \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) ）。 CLR 也不会遵循[对齐](../cpp/align-cpp.md)。

### <a name="com-initialization"></a>COM 初始化

当初始化模块时，公共语言运行时将自动初始化 COM （当 COM 自动初始化时，它将作为 MTA 来实现）。 因此，显式初始化 COM 会生成返回代码，指示 COM 已初始化。 当 CLR 已将 COM 初始化为另一线程模型时，尝试用一个线程模型显式初始化 COM 会导致应用程序失败。

默认情况下，公共语言运行时将 COM 作为 MTA 启动;使用[/CLRTHREADATTRIBUTE （设置 CLR 线程特性）](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)修改此。

### <a name="performance-issues"></a>性能问题

当间接调用生成到 MSIL 的C++本机方法（虚函数调用或使用函数指针）时，可能会出现性能下降的情况。 若要了解有关此情况的详细信息，请参阅[Double thunk](../dotnet/double-thunking-cpp.md)。

从本机转换到 MSIL 时，你会注意到工作集的大小增加。 这是因为公共语言运行时提供了许多功能，以确保程序正确运行。 如果 **/clr**应用程序未正常运行，可能需要启用 C4793 （默认情况下为 off），有关详细信息，请参阅[编译器警告（等级1和3） C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) 。

### <a name="program-crashes-on-shutdown"></a>关机时程序崩溃

在某些情况下，CLR 可以在托管代码运行完成之前关闭。 使用 `std::set_terminate` 和 `SIGTERM` 会导致此问题。 有关详细信息，请参阅[信号常量](../c-runtime-library/signal-constants.md)和[set_terminate](../c-runtime-library/abnormal-termination.md) 。

## <a name="using-new-visual-c-features"></a>使用新的C++视觉功能

在应用程序进行编译、链接和运行后，可以在使用 **/clr**编译的任何模块中开始使用 .net 功能。 有关详细信息，请参阅[运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)。

有关 .NET 编程的详细信息， C++请参阅：

- [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)

- [适用于运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>另请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
