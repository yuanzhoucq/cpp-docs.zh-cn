---
title: /MD、-MT、-LD （使用运行时库）
ms.date: 11/04/2016
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
ms.openlocfilehash: a953a63409c0b6c281533466797e1fc0c30c7a66
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415820"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD、/MT、/LD（使用运行时库）

指示多线程模块是否为 DLL，并指定运行库的零售版本或调试版本。

## <a name="syntax"></a>语法

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>备注

|选项|描述|
|------------|-----------------|
|**/MD**|使此应用程序使用特定于多线程和 DLL 的运行库版本。 定义 `_MT` 和 `_DLL`，并使编译器将库名 MSVCRT.lib 放入 .obj 文件中。<br /><br /> 用此选项编译的应用程序静态链接到 MSVCRT.lib。 此库提供使链接器能够解析外部引用的代码的层。 实际的工作代码包含在 MSVCR*versionnumber*。DLL，必须在运行时对与 MSVCRT.lib 链接的应用程序中可用。|
|**/MDd**|定义 `_DEBUG`、`_MT` 和 `_DLL`，并使此应用程序使用特定于多线程和 DLL 的调试版本的运行库。 它还会让编译器将库名称 MSVCRTD.lib 放入 .obj 文件中。|
|**/MT**|使此应用程序使用运行库的多线程的静态版本。 定义 `_MT`，并使编译器将库名 LIBCMT.lib 放入 .obj 文件中，以便链接器使用 LIBCMT.lib 解析外部符号。|
|**/MTd**|定义 `_DEBUG` 和 `_MT`。 此选项还会让编译器将库名称 LIBCMTD.lib 放置到 .obj 文件中，以便链接器将使用 LIBCMTD.lib 来解析外部符号。|
|**/LD**|创建一个 DLL。<br /><br /> Pass **/DLL**到链接器选项。 链接器查找 `DllMain` 函数，但并不需要该函数。 如果没有编写 `DllMain` 函数，则链接器将插入返回 TRUE 的 `DllMain` 函数。<br /><br /> 链接 DLL 启动代码。<br /><br /> 如果未在命令行上指定导出 (.exp) 文件，则创建导入库 (.lib)。 将导入库链接到调用 DLL 的应用程序。<br /><br /> 解释[/Fe （命名 EXE 文件）](../../build/reference/fe-name-exe-file.md)为命名 DLL 而不是.exe 文件。 默认情况下，程序名称将成为*basename*.dll 而不是*basename*.exe。<br /><br /> 暗指 **/MT**除非显式指定，否则 **/MD**。|
|**/LDd**|创建调试 DLL。 定义 `_MT` 和 `_DEBUG`。|

有关 C 运行时库和使用进行编译时要使用哪些库的详细信息[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)，请参阅[CRT 库功能](../../c-runtime-library/crt-library-features.md)。

传递给链接器给定调用的所有模块必须使用相同的运行时库编译器选项都编译 (**/MD**， **/MT**， **/LD**)。

有关如何使用运行时库的调试版本的详细信息，请参阅[C 运行时库参考](../../c-runtime-library/c-run-time-library-reference.md)。

有关 Dll 的详细信息，请参阅[Visual c + + 中的 Dll](../../build/dlls-in-visual-cpp.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开**C/c + +** 文件夹。

1. 选择**代码生成**属性页。

1. 修改**运行时库**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
