---
title: /clr（公共语言运行时编译）
ms.date: 05/16/2019
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: fa2be3d3ce17df104cda121e4869c975ec6dd440
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837310"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr（公共语言运行时编译）

允许应用程序和组件使用公共语言运行时 (CLR) 中的功能。

## <a name="syntax"></a>语法

> **/clr**[ **:** _options_]

## <a name="arguments"></a>自变量

*options*<br/>
下列开关中的一个或多个（以逗号分隔）。

- 无

   不带选项，/clr 为应用程序创建元数据。 其他 CLR 应用程序可以使用该元数据，并且该应用程序也可以使用其他 CLR 组件的元数据中的类型和数据。 有关详细信息，请参阅[混合（本机和托管）程序集](../../dotnet/mixed-native-and-managed-assemblies.md)。

- **pure**

   **/clr:pure 已弃用**。 在 Visual Studio 2017 及更高版本中，该选项已删除。 建议移植对 C# 来说必须是纯 MSIL 的代码。

- **安全**

   **/clr:safe 已弃用**。 在 Visual Studio 2017 及更高版本中，该选项已删除。 建议移植对 C# 来说必须是安全 MSIL 的代码。

- **noAssembly**

   **/clr:noAssembly 已弃用**。 请改用 [/LN (Create MSIL Module)](ln-create-msil-module.md) 。

   指定不应将程序集清单插入输出文件中。 默认情况下， **noAssembly** 选项是无效的。

   清单中不具有程序集元数据的托管程序称为 *“模块”* 。 **noAssembly** 选项只能用于生成模块。 如果使用 [/c](c-compile-without-linking.md) 和 **/clr:noAssembly**进行编译，请在创建模块的链接器阶段指定 [/NOASSEMBLY](noassembly-create-a-msil-module.md) 选项。

   在低于 Visual Studio 2005 的版本中，/clr:noAssembly 需要 /LD。 现在，指定 **/LD** 时即暗含 **/LD**。

- **initialAppDomain**

   允许 Visual C++ 应用程序在 CLR 版本 1 上运行。  使用 **initialAppDomain** 编译的应用程序不应由使用 ASP.NET 的应用程序使用，因为它在 CLR 版本 1 中不受支持 。

- **nostdlib**

   指示编译器忽略默认 \clr 目录。 如果包含 DLL 的多个版本（如 System.dll），则编译器将产生错误。 使用此选项可指定编译过程中要使用的特定框架。

## <a name="remarks"></a>备注

托管代码是可以由 CLR 检查和管理的代码。 托管代码可以访问托管对象。 有关详细信息，请参阅 [/clr Restrictions](clr-restrictions.md)。

有关如何开发定义和使用托管类型的应用程序的信息，请参阅 [Component Extensions for Runtime Platforms](../../extensions/component-extensions-for-runtime-platforms.md)。

使用 **/clr** 编译的应用程序可以包含也可以不包含托管数据。

若要在托管应用程序上启用调试，请参阅 [/ASSEMBLYDEBUG（添加 DebuggableAttribute）](assemblydebug-add-debuggableattribute.md)。

只有 CLR 类型会在垃圾回收堆上实例化。 有关更多信息，请参阅[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)。 若要将函数编译为本机代码，请使用 `unmanaged` 杂注。 有关详细信息，请参阅[托管和非托管](../../preprocessor/managed-unmanaged.md)。

默认情况下， **/clr** 是无效的。 当 **/clr** 有效时， **/MD** 也有效。 有关详细信息，请参阅 [/MD、/MT、/LD（使用运行时库）](md-mt-ld-use-run-time-library.md)。 **/MD** 确保从标准头 (.h) 文件中选择动态链接的多线程版本运行时例程。 托管编程必须进行多线程处理，因为 CLR 垃圾回收器将在辅助线程中运行终结器。

如果使用 /c 进行编译，可以通过 [/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md) 指定生成的输出文件的 CLR 类型。

**/clr** 暗含 **/EHa**，且 **/clr** 不支持任何其他 **/EH**选项。 有关详细信息，请参阅 [/EH（异常处理模型）](eh-exception-handling-model.md)。

有关如何确定文件的 CLR 映像类型的信息，请参阅 [/CLRHEADER](clrheader.md)。

传递给链接器给定调用的所有模块都必须使用相同的运行时编译器选项（ **/MD** 或 **/LD**）进行编译。

使用 [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) 链接器选项以在程序集中嵌入资源。 [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)、 [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)和 [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 链接器选项也允许自定义程序集的创建方式。

使用 **/clr** 时， `_MANAGED` 符号定义为 1。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。

先初始化本机对象文件中的全局变量（如果可执行文件是 DLL，即在 DllMain 期间进行），再初始化托管部分的全局变量（在运行任何托管代码之前进行）。 `#pragma` [init_seg](../../preprocessor/init-seg.md) 仅影响托管和非托管类别中的初始化顺序。

## <a name="metadata-and-unnamed-classes"></a>元数据和未命名类

未命名类将出现在按以下方式命名的元数据中： `$UnnamedClass$`*crc-of-current-file-name*`$`*index*`$`，其中 *index* 是未命名类在编译中的顺序计数。 例如，下面的代码示例将在元数据中生成一个未命名类。

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

使用 ildasm.exe 查看元数据。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
