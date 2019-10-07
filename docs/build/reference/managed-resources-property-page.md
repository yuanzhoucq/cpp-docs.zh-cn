---
title: “托管资源”属性页
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 14802996e63392bfb5fcc22096ef5f3d9db197c2
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177524"
---
# <a name="managed-resources-property-page"></a>“托管资源”属性页

在/Cli 程序中C++使用 .net 资源时, "**托管**资源" 属性页公开了托管资源编译器[resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)的以下属性:

- **资源逻辑名称**

   指定生成的中间 .resources 文件的逻辑名称。 逻辑名称是用于加载资源的名称。 如果未指定逻辑名称，则使用资源 (.resx) 文件名作为逻辑名称。

- **输出文件名**

   指定此资源 (.resx) 文件构成的最终输出文件的名称。

- **默认本地化资源**

   指定给定的 .resx 文件是构成默认资源还是附属 .dll。

有关如何访问 "**托管资源**" 属性页的信息, 请[参阅C++在 Visual Studio 中设置编译器和生成属性](../working-with-project-properties.md)。

## <a name="see-also"></a>请参阅

[使用 RC（RC 命令行）](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[C++项目属性页引用](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE（嵌入托管资源）](assemblyresource-embed-a-managed-resource.md)
