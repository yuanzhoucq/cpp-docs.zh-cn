---
title: “链接器”属性页 | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs:
- C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec1620d9ae84e5c0b957b7426ad388c70626813
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379211"
---
# <a name="linker-property-pages"></a>“链接器”属性页

本主题讨论“常规”链接器属性页上的以下属性。 若要查看本页面的 Linux 版本，请参阅[链接器属性 (Linux C++)](../linux/prop-pages/linker-linux.md)。

## <a name="general-page-properties"></a>“常规页”属性

### <a name="ignore-import-library"></a>Ignore Import Library

此属性指示链接器不要将基于该版本生成的任何 .lib 输出链接到任何相关项目。 这允许项目系统处理在生成时不创建 .lib 文件的 .dll 文件。 如果项目依赖于创建 DLL 的另一个项目，则项目系统会自动链接该子项目生成的 .lib 文件。 正在生成 COM DLL 或纯资源 DLL 的项目可能无需执行此操作，这些 DLL 的输出不具任何意义。 如果 DLL 没有导出项，链接器不会生成 .lib 文件。 如果磁盘上没有导出 .lib 文件，并且项目系统指示链接器链接此（缺少的）DLL，则链接将失败。 使用 Ignore Import Library 属性解决此问题。 设置为“是”时，项目系统会忽略是否存在该 .lib 文件，并导致依赖于此项目的任何项目不与非存在的 .lib 文件进行链接。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>Register Output

在生成输出上运行 `regsvr32.exe /s $(TargetPath)`，仅在 .dll 项目上有效。 对于 .exe 项目，则忽略此属性。 要注册 .exe 输出，请在配置上设置生成后事件以执行注册 .exe 文件始终所需的自定义注册。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>Per-user Redirection

传统上，Visual Studio 中的注册是在 HKEY_CLASSES_ROOT (HKCR) 中完成的。 如果使用 Windows Vista 及更高版本的操作系统，则必须在提升模式下运行 Visual Studio 才能访问 HKCR。 开发人员并非总是希望在提升模式下运行，但仍然必须注册。 使用 Per-user Redirection，可在非此模式下运行时进行注册。

Per-user Redirection 强制将任何对 HKCR 的写入重定向到 HKEY\_CURRENT\_USER (HKCU)。 如果关闭了 Per-user Redirection，当程序试图写入到 HKCR 时，可能导致[项目生成错误 PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md)。

### <a name="link-library-dependencies"></a>链接库依赖项

指定是否链接由依赖项目生成的 .lib 文件。 通常，需要链接 .lib 文件，但某些 DLL 可能并非如此。

也可通过提供文件名和相对路径来指定 .obj 文件，如“..\\..\MyLibProject\MyObjFile.obj”。 如果 .obj 文件 的源代码包含预编译标头（如 pch.h），则 pch.obj 文件位于 MyObjFile.obj 所在的文件夹中，且必须将 pch.obj 添加为附加依赖项。

### <a name="use-library-dependency-inputs"></a>使用库依赖项输入

在大型项目中，当依赖项目生成 .lib 文件时，将禁用增量链接。 如果有许多依赖项目生成 .lib 文件，则生成应用程序可能需要很长时间。 当此属性设置为“是”时，项目系统链接 .obj 文件中依赖项目生成的 .lib 文件，从而启用增量链接。

若要了解如何访问“常规”链接器属性页，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>请参阅

[“选项”对话框 ->“项目和解决方案”->“VC++ 项目设置”](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)<br>
[属性页](../ide/property-pages-visual-cpp.md)