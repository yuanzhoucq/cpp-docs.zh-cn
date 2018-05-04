---
title: 链接器属性页 |Microsoft 文档
ms.custom: ''
ms.date: 11/21/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31b44b6711153d29ab6a9c542a6e5677e6279432
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="linker-property-pages"></a>“链接器”属性页

本主题讨论以下属性上**常规**链接器属性页。 有关此页的 Linux 版本，请参阅[链接器属性 （Linux c + +）](../linux/prop-pages/linker-linux.md)。

## <a name="general-page-properties"></a>常规页属性

### <a name="ignore-import-library"></a>忽略导入库

此属性指示链接器无法将此生成到依赖项目中生成任何.lib 输出链接。 这样，项目系统以处理.dll 文件，不会产生时生成的.lib 文件。 如果一个项目依赖于另一个生成 DLL 的项目，项目系统将自动链接该子项目生成的.lib 文件。 这可能不需要的 COM Dll 或纯资源 Dll; 生成的项目这些 Dll 不具有任何有意义的导出。 如果 DLL 没有导出，链接器将不生成的.lib 文件。 如果不不存在，磁盘上的任何导出.lib 文件，项目系统通知链接后，将其与此 （缺少） DLL 链接的链接失败。 使用**忽略导入库**属性来解决此问题。 当设置为**是**，项目系统将忽略该.lib 文件是否存在并导致依赖于此项目，从而不与不存在的.lib 文件链接任何项目。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>注册输出

运行`regsvr32.exe /s $(TargetPath)`上生成输出，即仅在.dll 项目上有效。 对于.exe 项目，将忽略此属性。 若要注册.exe 输出，设置配置为始终是必需的已注册的.exe 文件的自定义注册生成后事件。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>每个用户重定向

Visual Studio 中的注册传统上已完成 HKEY_CLASSES_ROOT (HKCR)。 与 Windows Vista 和更高版本操作系统中，若要访问 HKCR 你必须运行 Visual Studio 在提升模式下。 开发人员始终不希望在提升模式下运行，但仍必须适用于注册。 每个用户重定向，可注册而无需在此模式下运行。

每个用户重定向将强制写入的所有数据转换成 HKCR 重定向到 HKEY\_当前\_用户 (HKCU)。 如果每个用户重定向已关闭，它可能会导致[项目生成错误 PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md)当程序尝试写入 HKCR。

### <a name="link-library-dependencies"></a>链接库依赖项

指定是否将由依赖项目生成的.lib 文件链接。 通常，你想要链接在.lib 文件中，但这可能不是某些 Dll 这种情况。

你还可以通过以下方式指定.obj 文件通过提供的文件名和相对路径，例如"...\\..\MyLibProject\MyObjFile.obj"。 如果源代码.obj 文件 #includes 预编译标头，例如 pch.h 中，则 pch.obj 文件位于与 MyObjFile.obj，相同的文件夹，并且还必须将 pch.obj 添加为附加依赖项。

### <a name="use-library-dependency-inputs"></a>使用库依赖项输入

在大型项目中，当依赖项目生成的.lib 文件，增量链接处于禁用状态。 如果有许多依赖项目生成的.lib 文件，生成应用程序可能需要很长时间。 当此属性设置为**是**，.lib 的.obj 文件中的项目系统链接生成依赖项目，从而启用增量链接。

有关如何访问**常规**链接器属性页上，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>请参阅

[“选项”对话框 ->“项目和解决方案”->“VC++ 项目设置”](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)  
[属性页](../ide/property-pages-visual-cpp.md)  