---
title: "如何：迁移到 /clr | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 迁移到"
  - "编译本机代码 [C++]"
  - "互操作 [C++], /clr 编译器选项"
  - "互操作性 [C++], /clr 编译器选项"
  - "迁移 [C++], /clr 编译器选项"
  - "升级 Visual C++ 应用程序, /clr 编译器选项"
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：迁移到 /clr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论使用 **\/clr** 编译本机代码时引发的问题（有关更多信息，请参见 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)）。  **\/clr** 允许 Visual C\+\+ 模块从 .NET 程序集调用和被调用，同时保留与非托管模块的兼容性。  有关使用 **\/clr** 进行编译的优点的更多信息，请参见[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)和[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)。  
  
## 使用 \/clr 编译库项目的已知问题  
 Visual Studio 包含一些与使用 **\/clr** 编译库项目有关的已知问题：  
  
-   在运行时，代码可以用 [CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md) 查询类型。  但是，如果某个类型位于 MSIL .dll（用 **\/clr** 编译）中，那么，在托管 .dll 中运行静态构造函数之前，对 [CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md) 的调用可能会失败（如果在托管 .dll 中执行代码之后调用 FromName，您将看不到此问题）。  为了解决此问题，可以通过以下方法来强制构造托管静态构造函数：在托管 .dll 中定义一个函数，导出它并从本机 MFC 应用程序中调用它。  例如：  
  
    ```  
    // Extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## 使用 Visual C\+\+ 进行编译  
 对项目中的任何模块使用 **\/clr** 之前，首先使用 Visual Studio 2010 编译并链接您的本机项目。  
  
 按顺序执行下列步骤是进行 **\/clr** 编译的最简便途径。  在其中每个步骤后编译并运行您的项目是很重要的。  
  
### Visual C\+\+ 2003 之前的版本  
 如果从 Visual C\+\+ 2003 之前的版本升级到 Visual Studio 2010，则可能出现与 Visual C\+\+ 2003 中增强的 C\+\+ 标准一致性相关的编译器错误。  
  
### 从 Visual C\+\+ 2003 升级  
 以前使用 Visual C\+\+ 2003 生成的项目也应首先在不使用 **\/clr** 的情况下编译，因为 Visual Studio 现在提高了 ANSI\/ISO 遵从性并进行了一些重大更改。  可能最需要注意的更改是 [CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。  使用 CRT 的代码很可能产生否决警告。  可以取消这些警告，但最好迁移到新的 [CRT 函数的安全增强版本](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)，因为它们提供更好的安全性并可能显示代码中的安全问题。  
  
### 从 C\+\+ 托管扩展升级  
 通过使用 C\+\+ 托管扩展的 Visual C\+\+ .NET 或 Visual C\+\+ 2003 生成的项目将需要对项目设置至少进行一次更改，因为现在否决了这些扩展。  因此，用 C\+\+ 托管扩展编写的代码将不能在 **\/clr** 下编译。  请改用 **\/clr:oldSyntax**。  
  
## 将 C 代码转换为 C\+\+ 代码  
 尽管 Visual Studio 能够编译 C 文件，但需要将它们转换为 C\+\+ 才能进行 **\/clr** 编译。  不必更改实际文件名；可以使用 **\/Tp**（请参见 [\/Tc、\/Tp、\/TC、\/TP（指定源文件类型）](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)）。请注意，尽管 **\/clr** 需要 C\+\+ 源代码文件，但是不必重构您的代码来使用面向对象的范例。  
  
 C 代码在编译为 C\+\+ 文件时很可能需要更改。  C\+\+ 类型安全规则是严格的，所以必须使用强制转换进行显式类型转换。  例如，malloc 返回一个 void 指针，但可以使用强制转换将其分配给一个指向 C 中任一类型的指针：  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 函数指针在 C\+\+ 中也是严格类型安全的，所以下面的 C 代码需要修改。  在 C\+\+ 中，最好创建一个定义函数指针类型的 `typedef`，然后使用该类型强制转换函数指针：  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C\+\+ 还要求这些函数是原型或完全定义的，才可以引用或调用它们。  
  
 如果 C 代码中使用的标识符恰好是 C\+\+ 中的关键字（如 `virtual`、`new`、`delete`、`bool`、`true`、`false` 等），必须重命名这些标识符。  这通常可以使用简单的搜索和替换操作来完成。  
  
 最后，尽管 C 样式的 COM 调用需要显式使用 v\-table 和 `this` 指针，但是 C\+\+ 不需要：  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## 重新配置项目设置  
 您的项目在 Visual Studio 2010 中编译和运行后，您应当为 **\/clr** 创建新的项目配置，而不是修改默认配置。  **\/clr** 与某些编译器选项不兼容，创建单独的配置可使您将项目生成为本机或托管的。  当在属性页对话框中选择了 **\/clr** 时，将禁用与 **\/clr** 不兼容的项目设置（如果随后取消选择 **\/clr**，禁用的选项不会自动还原）。  
  
### 创建新的项目配置  
 您可以使用 [New Project Configuration Dialog Box](http://msdn.microsoft.com/zh-cn/cca616dc-05a6-4fe3-bdc1-40c72a66f2be) 中的**“从此处复制设置”**选项来创建基于现有项目设置的项目配置。  对“调试”配置和“发布”配置各执行一次该操作。  然后，后面的更改可仅应用于特定于 **\/clr** 的配置，而保留原始项目配置不变。  
  
 可能需要格外注意使用自定义生成规则的项目。  
  
 此步骤对使用生成文件的项目有不同的含义。  在此情况下，可以配置单独的生成目标，也可以从原始版本的副本创建特定于 **\/clr** 编译的版本。  
  
### 更改项目设置  
 按照 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 中的指导进行操作，可以在开发环境中选择 **\/clr**。  如前所述，此步骤将自动禁用冲突的项目设置。  
  
> [!NOTE]
>  在从 Visual C\+\+ 2003 升级托管库或 Web 服务项目时，**\/Zl** 编译器选项将添加到**“命令行”**属性页中。  这将导致 LNK2001。  将 **\/Zl** 从**“命令行”**属性页移除可以解决此问题。  有关更多信息，请参见[\/Zl（省略默认库名）](../build/reference/zl-omit-default-library-name.md)和[如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)。  或者，将 msvcrt.lib 和 msvcmrt.lib 添加到链接器的**“附加依赖项”**属性。  
  
 对于使用生成文件生成的项目，一旦添加了 **\/clr**，就必须手动禁用不兼容的编译器选项。  有关与 **\/clr** 不兼容的编译器选项的信息，请参见 \/[\/clr 限制](../build/reference/clr-restrictions.md)。  
  
### 预编译头  
 在 **\/clr** 下支持预编译头。  但是，如果您仅使用 **\/clr** 编译某些 CPP 文件（将其余 CPP 文件编译为本机的），则需要进行一些更改，因为使用 **\/clr** 生成的预编译头与在不使用 **\/clr** 的情况下生成的那些预编译头不兼容。  这种不兼容性的原因是 **\/clr** 生成并需要元数据。  因此，用 **\/clr** 编译的模块无法使用不包含元数据的预编译头，并且非 **\/clr** 模块无法使用包含元数据的预编译头文件。  
  
 编译一个项目（其中某些模块是用 **\/clr** 编译的）的最简单方法是完全禁用预编译头。（在项目的“属性页”对话框中，打开“C\/C\+\+”节点，并选择“预编译头”。  然后，将“创建\/使用预编译头”属性更改为“不使用预编译头”。）  
  
 但是，尤其对于大型项目，预编译头提供的编译速度快得多，所以禁用此功能并不合适。  在此情况下，最好将 **\/clr** 和非 **\/clr** 文件配置为使用单独的预编译头。  这可以通过一个步骤来完成，方法是：使用“解决方案资源管理器”选择多个要使用 **\/clr** 编译的模块，右击该组，并选择“属性”。  然后，分别将“通过文件创建\/使用 PCH”和“预编译头文件”属性更改为使用不同的头文件名和 PCH 文件。  
  
## 修复错误  
 使用 **\/clr** 进行编译可能导致编译器错误、链接器错误或运行时错误。  本节讨论最常见的问题。  
  
### 元数据合并  
 数据类型的版本不同可能导致链接器失败，原因在于为两种类型生成的元数据不匹配。（如果根据条件定义了类型的成员，而这些条件对使用该类型的所有 CPP 文件并不相同，通常会导致此问题。）在此情况下，链接器将失败，仅报告符号名称和第二个 OBJ 文件（其中定义了该类型）的名称。  颠倒 OBJ 文件发送到链接器的顺序以发现其他版本的数据类型的位置经常是有用的。  
  
### 加载程序锁死锁  
 在 Visual C\+\+ .NET 和 Visual C\+\+ 2003 中，**\/clr** 下的初始化容易受到非确定性死锁的影响。  此问题称为“加载程序锁死锁”。  在 Visual Studio 2010 中，此死锁更容易避免，它在运行时被检测并报告，并且不再是非确定性的。  仍然可能遇到加载程序锁问题，但是现在它更容易避免和修复了。  有关详细背景、指导和解决方案，请参见 [混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)。  
  
### 数据导出  
 导出 DLL 数据易于出错，而且不建议这样做。  这是因为在执行 DLL 的某些托管部分之前，不能保证对 DLL 的数据节进行了初始化。  使用 [\#using 指令](../preprocessor/hash-using-directive-cpp.md) 引用元数据。  
  
### 类型可见性  
 现在，本机类型在默认情况下是私有的。  在 Visual C\+\+ .NET 2002 和 Visual C\+\+ 2003 中，本机类型在默认情况下是公共的。  这可能导致本机类型在 DLL 外不可见。  通过将 `public` 添加到这些类型可以解决此错误。  有关更多信息，请参见[类型和成员可见性](../misc/type-and-member-visibility.md)。  
  
### 浮点和对齐问题  
 公共语言运行时上不支持 `__controlfp`（有关更多信息，请参见 [\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)）。  CLR 也将不支持 [align](../cpp/align-cpp.md)。  
  
### COM 初始化  
 公共语言运行时在模块初始化时自动初始化 COM（在 COM 自动初始化时，它作为 MTA 初始化）。  因此，显式初始化 COM 生成返回代码，指示 COM 已初始化。  当 CLR 已经将 COM 初始化为线程模型时，如果尝试用另一个线程模型显式初始化 COM，则可能会导致应用程序失败。  
  
 默认情况下，公共语言运行时启动 COM 作为 MTA；请使用 [\/CLRTHREADATTRIBUTE（设置 CLR 线程特性）](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) 修改此设置。  
  
### 性能问题  
 当间接调用（虚函数调用或使用函数指针）对 MSIL 生成的本机 C\+\+ 方法时，可能发现性能降低。  若要了解关于此内容的更多信息，请参见 [双重形式转换](../dotnet/double-thunking-cpp.md)。  
  
 当从本机语言向 MSIL 迁移时，您将注意到工作集的大小增加了。  这是因为公共语言运行时提供许多功能来确保该程序正确运行。  如果您的 **\/clr** 应用程序没有正确运行，可能需要启用 C4793（默认情况下为关闭状态），有关更多信息，请参见 [编译器警告（等级 1 和等级 3）C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)。  
  
### 程序在关闭时出现故障  
 在某些情况下，CLR 可能在托管代码完成运行前关闭。  使用 `std::set_terminate` 和 `SIGTERM` 可能导致此问题。  有关更多信息，请参见[signal 常量](../c-runtime-library/signal-constants.md)和[set\_terminate](../Topic/set_terminate%20\(%3Cexception%3E\).md)。  
  
## 使用新的 Visual C\+\+ 功能  
 在您的应用程序编译、链接和运行后，您可以在使用 **\/clr** 编译的任何模块中开始使用 .NET 功能。  有关详细信息，请参阅[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。  
  
 如果使用了 C\+\+ 托管扩展，可以转换您的代码以使用新语法。  有关语法区别的摘要，请参见 [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/zh-cn/edbded88-7ef3-4757-bd9d-b8f48ac2aada)。  有关转换 C\+\+ 托管扩展的详细信息，请参见 [C\+\+\/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)。  
  
 有关在 Visual C\+\+ 中进行 .NET 编程的信息，请参见：  
  
-   [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)