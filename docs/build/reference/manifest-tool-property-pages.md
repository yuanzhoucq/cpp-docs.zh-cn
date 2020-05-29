---
title: 清单工具属性页
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: e1d0f1ac889cb915216ceb70d48e36efe4ad21bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336297"
---
# <a name="manifest-tool-property-pages"></a>清单工具属性页

使用这些页面为[Mt.exe](/windows/win32/sbscs/mt-exe)指定常规选项。 这些页面位于**项目** > **属性** > **配置属性** > **清单工具**下。

## <a name="general-property-page"></a>“常规属性”页

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

   如果为“是(/nologo)”，则指定在启动清单工具时隐藏标准 Microsoft 版权所有数据****。 将 mt.exe 作为生成过程的一部分运行或从生成环境运行 mt.exe 时，使用此选项取消显示日志文件中不需要的输出。

### <a name="verbose-output"></a>详细输出

   如果为“是(/verbose)”，则指定在清单生成期间显示其他生成信息****。

### <a name="assembly-identity"></a>程序集标识

使用 /标识选项指定标识字符串，该字符串包含[\<程序集标识>元素](/visualstudio/deployment/assemblyidentity-element-clickonce-application)的属性。 标识字符串以`name`属性的值开头，后跟*属性* = *值*对。 标识字符串中的特性以逗号隔开。

这是一个示例标识字符串：`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>输入和输出属性页

### <a name="additional-manifest-files"></a>其他清单文件

使用“/manifest”选项指定清单工具将处理或合并的其他清单文件的完整路径****。 以分号分隔完整路径。 （-清单[清单1][清单2]...）

### <a name="input-resource-manifests"></a>输入资源清单

使用“/inputresource”选项指定 RT_MANIFEST 类型资源的完整路径，以输入到清单工具中****。 该路径的后面可紧跟指定的资源 ID。 例如：

`dll_with_manifest.dll;#1`

### <a name="embed-manifest"></a>嵌入清单

- 若选择“是”，则指定项目系统将应用程序清单文件嵌入到程序集中****。

- 若选择“否”，则指定项目系统将应用程序清单文件创建为独立的文件****。

### <a name="output-manifest-file"></a>输出清单文件

指定输出清单文件的名称。 当清单工具仅处理一个清单文件时，此属性是可选项。 （外：[文件];[资源 ID]）

### <a name="manifest-resource-file"></a>清单资源文件

指定用于将清单嵌入项目输出的输出资源文件。

### <a name="generate-catalog-files"></a>生成目录文件

使用“/makecdfs”选项指定清单工具将生成目录定义文件（即 .cdf 文件，用于创建目录）****。 （/makecdfs）

### <a name="generate-manifest-from-managedassembly"></a>基于 ManagedAssembly 生成清单

基于托管程序集生成清单。 （托管程序集名称：\[文件*）

### <a name="suppress-dependency-element"></a>取消依赖元素

与 -托管装配一起使用。 禁止生成最终清单中的依赖项元素。 （-不依赖）

### <a name="generate-category-tags"></a>生成类别标记

与 -托管装配一起使用。 -类别导致生成类别标记。 （类别）

### <a name="dpi-awareness"></a>DPI 意识

指定应用程序是否具有 DPI 感知功能。 默认情况下，MFC 项目设置为“是”，其他项目设置为“否”，因为只有 MFC 项目内置有 DPI 感知功能********。 如果添加代码来处理其他 DPI 设置，可将设置改为“是”****。 如果在应用程序非 DPI 感知型时将其设置为此类型，应用程序可能显示失真或显示较小。

**选择**

- **无**
- **高 DPI 感知**
- **每个监视器高 DPI 感知**

## <a name="isolated-com-property-page"></a>隔离 COM 属性页

有关隔离 COM 的详细信息，请参阅[隔离应用程序](/windows/win32/SbsCs/isolated-applications)以及如何[：构建独立应用程序以使用 COM 组件](../how-to-build-isolated-applications-to-consume-com-components.md)。

### <a name="type-library-file"></a>类型库文件

指定用于注册免费 COM 清单支持的类型库。 （-tlb：[文件]）

### <a name="registrar-script-file"></a>注册器脚本文件

指定用于注册商脚本文件以用于注册 COM 清单支持。 （-rgs：[文件]）

### <a name="component-file-name"></a>组件文件名

指定从指定的 .tlb 或 .rgs 生成的组件的文件名。 （-dll：[文件]）

### <a name="replacements-file"></a>替换文件

指定包含 RGS 文件中可替换字符串的值的文件。 （替换：[文件]）

## <a name="advanced-property-page"></a>高级属性页

### <a name="update-file-hashes"></a>更新文件哈希

计算文件元素中指定的文件的哈希值，并更新具有此值的哈希属性。 （哈希更新：[路径]）

### <a name="update-file-hashes-search-path"></a>更新文件哈希搜索路径

指定更新文件哈希时要使用的搜索路径。

### <a name="additional-options"></a>其他选项

其他选项

## <a name="see-also"></a>另请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)
