---
title: 清单工具独立 COM 属性 (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: a6188eeb53b4ffcd3eee754e88a8891310fb2d51
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738839"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>“&lt;项目名&gt; 属性页”对话框 ->“配置属性”->“清单工具”->“独立 COM”

使用此对话框指定 [Mt.exe](https://msdn.microsoft.com/library/aa375649) 的“独立 COM”选项。

若要访问此属性页对话框，请打开项目或属性表的属性页。 展开“常用属性”下的“清单工具节点”，然后选择“独立 COM”。

## <a name="task-list"></a>任务列表

- [如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)

## <a name="uielement-list"></a>UIElement 列表

- **类型库文件**

   使用 /tlb 选项指定类型库文件（.tlb 文件）的名称，清单工具将使用该文件来生成清单文件。

- **注册器脚本文件**

   使用 /rgs 选项指定注册器脚本文件（.rgs 文件）的名称，清单工具将使用该文件来生成清单文件。

- **组件文件名**

   使用 /dll 选项指定清单工具将生成的资源的名称。 指定“类型库文件”或“注册器脚本文件”时，必须输入此属性的值。

- **替换文件**

   使用 /replacements 选项，为包含 .rgs 文件中可替换字符串的值的文件指定完整路径。

## <a name="see-also"></a>请参阅

[独立的应用程序](/windows/desktop/SbsCs/isolated-applications)<br>
[ndptecclick](/visualstudio/deployment/clickonce-application-manifest)<br>
[清单工具属性页](../ide/manifest-tool-property-pages.md)<br>
[使用项目属性](../ide/working-with-project-properties.md)
