---
title: “常规”属性页（文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 224a205bb87b89f073676275d67e3cdd127b79af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655243"
---
# <a name="general-property-page-file"></a>“常规”属性页（文件）

在“解决方案资源管理器”中选定文件时，“配置属性”节点下的“常规”属性页包含以下属性：

- **从生成中排除**

   指定文件是否应位于当前配置的生成中。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>。

- **工具**

   该工具将用于生成此文件。 请参阅[指定自定义生成工具](../ide/specifying-custom-build-tools.md)，获取详细信息。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>。

有关如何访问“配置属性”节点下的“常规”属性页，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

对于非 Windows 项目，请参阅 [Linux C++ 属性页参考](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->。

## <a name="see-also"></a>请参阅

[属性页](../ide/property-pages-visual-cpp.md)