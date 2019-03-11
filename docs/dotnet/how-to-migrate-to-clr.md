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
ms.openlocfilehash: 02e678f98773f9ae7bb4f611210329a7a1116f17
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749108"
---
# <a name="how-to-migrate-to-clr"></a>如何：迁移到 /clr

本主题讨论编译本机代码时出现的问题 **/clr** (请参阅[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)有关详细信息)。 **/clr**允许本机 c + + 代码调用和被调用从除了其他本机 c + + 代码的.NET 程序集。 请参阅[混合 （本机和托管） 程序集](../dotnet/mixed-native-and-managed-assemblies.md)并[本机和.NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)有关详细信息进行编译的优势 **/clr**。

## <a name="known-issues-compiling-library-projects-with-clr"></a>已知的问题编译类库项目使用 /clr

编译以下位置使用的库项目时，visual Studio 包含一些已知的问题 **/clr**:

- 你的代码可能会查询在运行时使用的类型[CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname)。 但是，如果类型是 MSIL.dll 中 (使用编译 **/clr**)，在调用`FromName`发生 （您不会看到此问题如果 FromName 调用发生后的代码具有托管.dll 中的静态构造函数运行之前可能会失败执行托管.dll 中）。 若要解决此问题，您可以通过托管的.dll 文件中定义函数、 导出它，并从本机 MFC 应用程序中调用它强制托管静态构造函数的构造。 例如：

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>使用 Visual c + + 编译

使用之前 **/clr**上你的项目中的任何模块，首次编译和链接本机项目使用 Visual Studio 2010。

以下步骤，遵循的顺序，提供的最简单路径 **/clr**编译。 务必要编译并在每个步骤后运行你的项目。

### <a name="versions-prior-to-visual-c-2003"></a>Visual c + + 2003年之前的版本

如果要从 Visual c + + 2003年之前的版本升级到 Visual Studio 2010，您可能会看到与 Visual c + + 2003年中增强的 c + + 标准一致性相关的编译器错误

### <a name="upgrading-from-visual-c-2003"></a>从 Visual c + + 2003年升级

Visual c + + 2003年生成的项目之前应首先编译而无需 **/clr**如 Visual Studio 现在增加了 ANSI/ISO 符合性和一些重大更改。 可能需要最大关注的更改是[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。 使用 CRT 的代码是很有可能会生成弃用警告。 这些警告可以禁止显示，但正在迁移到新[Security-Enhanced 版本的 CRT 函数](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)是首选方法，因为它们提供更佳的安全性，但可能会泄露你的代码中的安全问题。

### <a name="upgrading-from-managed-extensions-for-c"></a>从托管扩展升级 c + +

从 Visual Studio 2005 中，使用托管扩展 c + + 编写的代码将不会编译下 **/clr**。

## <a name="convert-c-code-to-c"></a>将 C 代码转换为 c + +

尽管 Visual Studio 将编译 C 文件，但有必要将其转换为用于 c + + **/clr**编译。 实际文件名并不需要进行更改;可以使用 **/Tp** (请参阅[/Tc、 /Tp、 /TC、 /TP （指定源文件类型）](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。)请注意，虽然 c + + 源代码文件所需 **/clr**，不需要重构代码以使用面向对象的模式。

C 代码是非常可能需要更改编译为 c + + 文件时。 C + + 类型安全规则非常严格，，因此必须使用强制转换显式进行类型转换。 例如，malloc 返回 void 的指针，但可以分配给指向 C 中使用强制转换任何类型的指针：

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

函数指针是还严格类型安全的 c + +，因此下面的 C 代码需要进行修改。 C + + 中最好创建`typedef`的定义的函数指针类型，以及如何将该类型强制转换函数指针：

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C + + 还要求这些函数是原型或完全定义可以引用或调用之前。

在 C 代码中使用恰好是 c + + 中的关键字的标识符 (如**虚拟**，**新**，**删除**， **bool**， **，则返回 true**， **false**等) 必须重命名。 这通常可以通过简单的搜索和替换操作。

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>重新配置项目设置

你的项目将编译并运行在 Visual Studio 2010 之后应创建新的项目配置为 **/clr**而不修改默认配置。 **/clr**与一些编译器选项不兼容，并创建单独的配置允许您为本机或托管将项目生成。 当 **/clr**在属性页对话框中，与不兼容的项目设置中选择 **/clr**已禁用 (和禁用的选项不会自动还原如果 **/clr**随后取消选择)。

### <a name="create-new-project-configurations"></a>创建新的项目配置

可以使用**从此处复制设置**选项**新建项目配置对话框**(**生成** > **Configuration Manager** > **活动解决方案配置** > **新建**) 来创建基于现有项目设置的项目配置。 执行此操作一次调试配置的一次针对发布配置。 然后，后续更改可以应用于 **/clr**的特定配置，使原始项目配置保持不变。

使用自定义生成规则的项目可能需要额外关注。

此步骤具有不同的影响，对于使用生成文件项目。 在此情况下，可以配置单独的生成目标或特定于版本 **/clr**编译可以创建从原始副本。

### <a name="change-project-settings"></a>更改项目设置

**/clr**可以通过中的说明在开发环境中选取[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。 正如前面提到的此步骤将自动禁用冲突的项目设置。

> [!NOTE]
>  从 Visual c + + 2003 中，升级托管的库或 web 服务项目时 **/Zl**编译器选项将添加到**命令行**属性页。 这将导致 LNK2001。 删除 **/Zl**从**命令行**属性页后，可以解决。 请参阅[/Zl （省略默认库名）](../build/reference/zl-omit-default-library-name.md)并[使用项目属性](../ide/working-with-project-properties.md)有关详细信息。 或添加到链接器的 msvcrt.lib 和 msvcmrt.lib**附加依赖项**属性。

对于使用生成文件生成的项目，不兼容的编译器选项必须处于禁用状态一次手动 **/clr**添加。 请参阅 /[/clr 限制](../build/reference/clr-restrictions.md)为与不兼容的编译器选项的信息 **/clr**。

### <a name="precompiled-headers"></a>预编译标头

预编译标头受 **/clr**。 但是，如果您仅编译某些 CPP 文件与 **/clr** （编译为本机 rest） 的某些更改将需要因为预编译标头生成具有 **/clr**与那些不兼容生成不含 **/clr**。 此不兼容性是由于在于 **/clr**生成，并需要的元数据。 编译的模块 **/clr**因此可以不使用预编译标头不包含元数据，和非 **/clr**模块不能使用预编译标头文件包含元数据。

编译的项目编译某些模块的位置的最简单办法 **/clr**是完全禁用预编译标头。 （在项目属性页对话框中，打开 C/c + + 节点，并选择预编译标头。 然后创建/使用预编译标头属性更改为"不使用预编译标头"。）

但是，特别是对于大型项目中，预编译标头提供更好的编译速度，因此禁用此功能不需要这样做。 在这种情况下最好配置 **/clr**和非 **/clr**文件以使用单独的预编译标头。 这可以通过一个步骤中选择多要编译的模块 **/clr**使用**解决方案资源管理器**、 右键单击组，并选择属性。 然后更改通过文件创建/使用 PCH 和预编译头文件的属性，以分别使用不同的标头文件的名称和 PCH 文件。

## <a name="fixing-errors"></a>修复错误

使用编译 **/clr**可能会导致编译器、 链接器或运行时错误。 本部分讨论最常见的问题。

### <a name="metadata-merge"></a>元数据合并

不同版本的数据类型可能会导致链接器失败，因为生成两种类型的元数据不匹配。 （这通常被由于时有条件地定义类型的成员，但条件是不同的使用类型的所有 CPP 文件。）在这种情况下链接器将失败，报告只有符号名和定义类型的第二个 OBJ 文件的名称。 通常它可用于旋转，OBJ 文件发送到链接器以发现另一版本的数据类型的位置的顺序。

### <a name="loader-lock-deadlock"></a>加载程序锁死锁

"加载程序锁死锁"可能会发生，但具有确定性并将检测到并在运行时报告。 请参阅[混合程序集初始化](../dotnet/initialization-of-mixed-assemblies.md)的详细的背景、 指南和解决方案。

### <a name="data-exports"></a>数据导出

导出 DLL 数据是容易出错且不建议这样做。 这是因为 DLL 的数据部分不能保证已执行的 DLL 的某些托管的部分之前进行初始化。 与引用元数据[#using 指令](../preprocessor/hash-using-directive-cpp.md)。

### <a name="type-visibility"></a>类型可见性

本机类型是私有的默认值。 这可能导致不可在 DLL 外可见的本机类型。 通过添加解决此错误`public`到这些类型。

### <a name="floating-point-and-alignment-issues"></a>浮点和对齐问题

`__controlfp` 不支持公共语言运行时 (请参阅[_control87、 _controlfp， \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)有关详细信息)。 CLR 还将不遵守[对齐](../cpp/align-cpp.md)。

### <a name="com-initialization"></a>COM 初始化

公共语言运行时初始化 COM 自动初始化模块时 （自动初始化 COM 时它已经作为 MTA）。 因此，显式初始化 COM 生成，该值指示 COM 已初始化的返回代码。 尝试显式与一个线程处理模型初始化 COM 在 CLR 已初始化 COM 到另一个线程处理模型时可能会导致应用程序失败。

公共语言运行时启动 COM MTA 作为默认设置。使用[/CLRTHREADATTRIBUTE （设置 CLR 线程特性）](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)若要修改此。

### <a name="performance-issues"></a>性能问题

生成为 MSIL 的本机 c + + 方法间接调用时，可能会看到性能降低 （虚拟函数调用或使用函数指针）。 若要了解详细信息，请参阅[双重形式转换](../dotnet/double-thunking-cpp.md)。

当从 MSIL 的本机移动，请将注意到您的工作集大小的增加。 这是因为公共语言运行时提供了许多功能，以确保该程序正确运行。 如果你 **/clr**应用程序没有正常运行，你可能想要启用 C4793 （默认情况下关闭），请参阅[编译器警告 （等级 1 和 3） C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)有关详细信息。

### <a name="program-crashes-on-shutdown"></a>在关闭程序故障

在某些情况下，CLR 可关闭，完成您的托管的代码之前运行。 使用`std::set_terminate`和`SIGTERM`可以导致这。 请参阅[signal 常量](../c-runtime-library/signal-constants.md)并[set_terminate](../c-runtime-library/abnormal-termination.md)有关详细信息。

## <a name="using-new-visual-c-features"></a>使用 Visual c + + 的新功能

应用程序编译、 链接和运行之后, 可以开始在编译使用的任何模块中使用.NET 功能 **/clr**。 有关详细信息，请参阅[运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。

如果用于 c + + 托管扩展，可以转换代码以使用新语法。 转换为 c + + 托管扩展的详细信息，请参阅[C + + /cli 迁移入门](../dotnet/cpp-cli-migration-primer.md)。

有关.NET 中 Visual c + + 编程的信息，请参阅：

- [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)

- [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
