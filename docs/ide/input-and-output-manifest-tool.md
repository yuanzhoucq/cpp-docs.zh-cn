---
title: 清单工具输入和输出属性 (Visual C++)
ms.date: 08/27/2018
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
ms.openlocfilehash: 8aa007e41cdabe0bf548f1184b801c1f81655596
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624690"
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>“配置属性”->“清单工具”->“输入和输出”->“&lt;项目名&gt; 属性页”对话框

此对话框可用于指定 [Mt.exe](/windows/desktop/SbsCs/mt-exe) 的输入和输出选项。

若要访问此属性页对话框，请打开项目或属性表的属性页。 展开“配置属性”下的“清单工具”节点，然后选择“输入和输出”。

## <a name="uielement-list"></a>UIElement 列表

**其他清单文件**<br/>
使用“/manifest”选项指定清单工具将处理或合并的其他清单文件的完整路径。 以分号分隔完整路径。

**输入资源清单**<br/>
使用“/inputresource”选项指定 RT_MANIFEST 类型资源的完整路径，以输入到清单工具中。 该路径的后面可紧跟指定的资源 ID。 例如:

`dll_with_manifest.dll;#1`

资源 ID 是可选项，winuser.h 中默认为 CREATEPROCESS_MANIFEST_RESOURCE_ID。

**嵌入清单**<br/>
- 若选择“是”，则指定项目系统将应用程序清单文件嵌入到程序集中。

- 若选择“否”，则指定项目系统将应用程序清单文件创建为独立的文件。

**输出清单文件**<br/>
指定输出清单文件的名称。 当清单工具仅处理一个清单文件时，此属性是可选项。

**清单资源文件**<br/>
指定用于将清单嵌入项目输出的输出资源文件。

**生成目录文件**<br/>
使用“/makecdfs”选项指定清单工具将生成目录定义文件（即 .cdf 文件，用于创建目录）。

**基于 ManagedAssembly 生成清单**<br/>
基于托管程序集生成清单。 （-managedassemblyname：<em>文件</em>）。

**取消依赖元素**<br/>
与“-managedassembly”选项一起使用。 此标记取消在最终清单中生成依赖元素。

**生成类别标记**<br/>
与“-managedassembly”选项一起使用。 此标记会导致生成类别标记。

**启用 DPI 感知功能**<br/>
指定应用程序是否具有 DPI 感知功能。 默认情况下，MFC 项目设置为“是”，其他项目设置为“否”，因为只有 MFC 项目内置有 DPI 感知功能。 如果添加代码来处理其他 DPI 设置，可将设置改为“是”。 如果在应用程序非 DPI 感知型时将其设置为此类型，应用程序可能显示失真或显示较小。

## <a name="see-also"></a>请参阅

[ndptecclick](/visualstudio/deployment/clickonce-application-manifest)<br/>
[清单工具属性页](../ide/manifest-tool-property-pages.md)<br/>
[使用项目属性](../ide/working-with-project-properties.md)<br/>
