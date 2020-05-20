---
title: /MD、-MT、-LD （使用运行时库）
ms.date: 07/17/2019
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
ms.openlocfilehash: a66677ebbef984e9a4c8190f184ca3a9126a7b83
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550753"
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

|选项|说明|
|------------|-----------------|
|**/MD**|使此应用程序使用特定于多线程和 DLL 的运行库版本。 定义 `_MT` 和 `_DLL`，并使编译器将库名 MSVCRT.lib 放入 .obj 文件中。<br /><br /> 用此选项编译的应用程序静态链接到 MSVCRT.lib。 此库提供使链接器能够解析外部引用的代码的层。 实际工作代码包含在 MSVCR*versionnumber*中。DLL，它必须在运行时可用于链接到 MSVCRT.LIB 的应用程序。|
|**/MDd**|定义 `_DEBUG`、`_MT` 和 `_DLL`，并使此应用程序使用特定于多线程和 DLL 的调试版本的运行库。 它还会让编译器将库名称 MSVCRTD.lib 放入 .obj 文件中。|
|**/MT**|使此应用程序使用运行库的多线程的静态版本。 定义 `_MT`，并使编译器将库名 LIBCMT.lib 放入 .obj 文件中，以便链接器使用 LIBCMT.lib 解析外部符号。|
|**/MTd**|定义 `_DEBUG` 和 `_MT`。 此选项还会让编译器将库名称 LIBCMTD.lib 放置到 .obj 文件中，以便链接器将使用 LIBCMTD.lib 来解析外部符号。|
|**/LD**|创建一个 DLL。<br /><br /> 将 **/DLL**选项传递到链接器。 链接器查找 `DllMain` 函数，但并不需要该函数。 如果没有编写 `DllMain` 函数，则链接器将插入返回 TRUE 的 `DllMain` 函数。<br /><br /> 链接 DLL 启动代码。<br /><br /> 如果未在命令行上指定导出 (.exp) 文件，则创建导入库 (.lib)。 将导入库链接到调用 DLL 的应用程序。<br /><br /> 将[/Fe （名称 EXE 文件）](fe-name-exe-file.md)解释为 DLL 而不是 .exe 文件的命名。 默认情况下，程序名称将变为*basename*，而不是*basename*。<br /><br /> 除非显式指定 **/md**，否则请隐含 **/mt** 。|
|**/LDd**|创建调试 DLL。 定义 `_MT` 和 `_DEBUG`。|

有关 C 运行时库以及使用[/clr （公共语言运行时编译）](clr-common-language-runtime-compilation.md)进行编译时使用的库的详细信息，请参阅[CRT 库功能](../../c-runtime-library/crt-library-features.md)。

传递给链接器给定调用的所有模块都必须使用相同的运行时库编译器选项（**/md**、 **/mt**、 **/ld**）进行编译。

有关如何使用运行时库的调试版本的详细信息，请参阅[C 运行时库引用](../../c-runtime-library/c-run-time-library-reference.md)。

有关 Dll 的详细信息，请参阅[在 Visual Studio 中创建 c/c + + dll](../dlls-in-visual-cpp.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **代码生成**" 属性页。

1. 修改 "**运行时库**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
