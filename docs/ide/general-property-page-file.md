---
title: 常规属性页 （文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
dev_langs:
- C++
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 523ac16a647116f4d18da7e516adb4f0e6bb7fc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="general-property-page-file"></a>“常规”属性页（文件）

文件中的选定时**解决方案资源管理器**、**常规**下的属性页**配置属性**节点包含以下属性：

**从生成中排除**  
指定文件是否应在当前配置的生成中。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>。

**工具**  
将用于生成此文件中的工具。 请参阅[指定自定义生成工具](../ide/specifying-custom-build-tools.md)有关详细信息。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>。

有关如何访问信息**常规**下的属性页**配置属性**节点，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

对于非 Windows 项目，请参阅[Linux c + + 属性页引用](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->。

## <a name="see-also"></a>请参阅

[属性页](../ide/property-pages-visual-cpp.md)  