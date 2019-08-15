---
title: 清单工具属性页
ms.date: 7/24/2019
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
ms.openlocfilehash: c8413a28024361db82ca74858453202393987e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492691"
---
# <a name="manifest-tool-property-pages"></a>清单工具属性页

使用这些页面指定[mt.exe](/windows/win32/sbscs/mt-exe)的常规选项。 这些页面位于 "**项目** > **属性** > " "**配置属性** > " "**清单工具**" 下。

## <a name="general-property-page"></a>"常规属性" 页

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

   如果为“是(/nologo)”，则指定在启动清单工具时隐藏标准 Microsoft 版权所有数据。 将 mt.exe 作为生成过程的一部分运行或从生成环境运行 mt.exe 时，使用此选项取消显示日志文件中不需要的输出。

### <a name="verbose-output"></a>详细输出

   如果为“是(/verbose)”，则指定在清单生成期间显示其他生成信息。

### <a name="assembly-identity"></a>程序集标识 * *

使用 /identity 选项指定标识字符串，该字符串包含 [\<assemblyIdentity> 元素](/visualstudio/deployment/assemblyidentity-element-clickonce-application)的特性。 标识字符串以 `name` 特性的值开头，后面跟特性 = 值对。 标识字符串中的特性以逗号隔开。

下面是一个示例标识字符串:`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>"输入和输出" 属性页     

###  <a name="additional-manifest-files"></a>附加清单文件

使用“/manifest”选项指定清单工具将处理或合并的其他清单文件的完整路径。 以分号分隔完整路径。 (-manifest [manifest1] [manifest2] ...)

###  <a name="input-resource-manifests"></a>输入资源清单

使用“/inputresource”选项指定 RT_MANIFEST 类型资源的完整路径，以输入到清单工具中。 该路径的后面可紧跟指定的资源 ID。 例如：

`dll_with_manifest.dll;#1`

###  <a name="embed-manifest"></a>嵌入清单

- 若选择“是”，则指定项目系统将应用程序清单文件嵌入到程序集中。

- 若选择“否”，则指定项目系统将应用程序清单文件创建为独立的文件。

###  <a name="output-manifest-file"></a>输出清单文件

指定输出清单文件的名称。 当清单工具仅处理一个清单文件时，此属性是可选项。 (-out: [文件]; # [资源 ID])

###  <a name="manifest-resource-file"></a>清单资源文件

指定用于将清单嵌入项目输出的输出资源文件。

###  <a name="generate-catalog-files"></a>生成目录文件

使用“/makecdfs”选项指定清单工具将生成目录定义文件（即 .cdf 文件，用于创建目录）。 /makecdfs

###  <a name="generate-manifest-from-managedassembly"></a>从 ManagedAssembly 生成清单

基于托管程序集生成清单。 (-managedassemblyname: [文件])

###  <a name="suppress-dependency-element"></a>禁止依赖项元素

与-managedassembly 一起使用。 禁止生成最终清单中的依赖项元素。 (-nodependency)

###  <a name="generate-category-tags"></a>生成类别标记

与-managedassembly 一起使用。 -category 导致生成类别标记。 (-category)

###  <a name="dpi-awareness"></a>DPI 感知

指定应用程序是否具有 DPI 感知功能。 默认情况下，MFC 项目设置为“是”，其他项目设置为“否”，因为只有 MFC 项目内置有 DPI 感知功能。 如果添加代码来处理其他 DPI 设置，可将设置改为“是”。 如果在应用程序非 DPI 感知型时将其设置为此类型，应用程序可能显示失真或显示较小。

**方案**

- **无**
- **高 DPI 感知**
- **每个监视器高 DPI 识别**

## <a name="isolated-com-property-page"></a>独立 COM 属性页

有关独立 COM 的详细信息, 请参阅[独立应用程序](/windows/win32/SbsCs/isolated-applications)和[如何:生成独立应用程序以使用 COM](../how-to-build-isolated-applications-to-consume-com-components.md)组件。

###  <a name="type-library-file"></a>类型库文件

指定用于 regfree COM 清单支持的类型库。 (-tlb: [文件])

###  <a name="registrar-script-file"></a>注册器脚本文件

指定用于 regfree COM 清单支持的注册器脚本文件。 (-rgs: [文件])

###  <a name="component-file-name"></a>组件文件名

指定从指定的 .tlb 或 .rgs 生成的组件的文件名。 (-dll: [文件])

###  <a name="replacements-file"></a>替换文件

指定包含 RGS 文件中可替换字符串的值的文件。 (替换: [文件])

## <a name="advanced-property-page"></a>"高级" 属性页

###  <a name="update-file-hashes"></a>更新文件哈希

计算在文件元素中指定的文件的哈希值, 并将哈希属性更新为此值。 (hashupdate: [路径])

###  <a name="update-file-hashes-search-path"></a>更新文件哈希搜索路径

指定更新文件哈希时要使用的搜索路径。

###  <a name="additional-options"></a>附加选项

附加选项


## <a name="see-also"></a>请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)
