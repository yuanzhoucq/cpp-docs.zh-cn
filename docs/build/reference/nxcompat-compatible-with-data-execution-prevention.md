---
title: /NXCOMPAT （与数据执行保护兼容） |Microsoft 文档
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /NXCOMPAT
dev_langs:
- C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb4f8a91545a196bc92fdc0ec44e89a7d5680185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374799"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT（与数据执行保护兼容）

指示可执行文件是与 Windows 数据执行保护功能兼容。

## <a name="syntax"></a>语法

> **/NXCOMPAT**[**： 否**]

## <a name="remarks"></a>备注

默认情况下， **/NXCOMPAT**上。

**/NXCOMPAT:NO**可用来显式指定为不与数据执行保护兼容的可执行文件。

有关数据执行保护的详细信息，请参阅这些文章：

- [数据执行保护 (DEP) 功能的详细的说明](http://go.microsoft.com/fwlink/p/?linkid=157771)

- [数据执行保护](http://go.microsoft.com/fwlink/p/?linkid=157770)

- [数据执行保护 (Windows Embedded)](http://go.microsoft.com/fwlink/p/?linkid=157768)

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**框。 选择**确定**或**应用**以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)  
[链接器选项](../../build/reference/linker-options.md)  
