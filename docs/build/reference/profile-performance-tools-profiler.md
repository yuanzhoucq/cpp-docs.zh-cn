---
title: -PROFILE (性能工具 Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Profile
dev_langs:
- C++
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 859ea4091502fa6c339a809a5b9e439c91462bd7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707755"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE（性能工具分析器）

生成一个可与“性能工具”探查器结合使用的输出文件。

## <a name="syntax"></a>语法

```
/PROFILE
```

## <a name="remarks"></a>备注

/ 配置文件表示以下链接器选项：

- [/OPT: REF](../../build/reference/opt-optimizations.md)

- /OPT: NOICF

- [/INCREMENTAL: NO](../../build/reference/incremental-link-incrementally.md)

- [/FIXED: NO](../../build/reference/fixed-fixed-base-address.md)

/ 配置文件会导致链接器在程序映像中生成重定位节。  重定位节允许探查器来转换在程序映像，以获取配置文件数据。

**/ 分析**只是仅在 Enterprise （团队开发） 版本中可用。  PREfast 的详细信息，请参阅[的代码分析 C/c + + 概述](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**高级**属性页。

1. 修改**配置文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)