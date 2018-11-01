---
title: /NXCOMPAT（与数据执行保护兼容）
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: 815719468e7dcf9325d19efe879b8f4ace040094
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490488"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT（与数据执行保护兼容）

指示可执行文件是与 Windows 数据执行保护功能兼容。

## <a name="syntax"></a>语法

> **/NXCOMPAT**[**： 否**]

## <a name="remarks"></a>备注

默认情况下 **/NXCOMPAT**上。

**/Nxcompat: no**可用于显式指定为不与数据执行保护兼容的可执行文件。

有关数据执行保护的详细信息，请参阅以下文章：

- [数据执行保护 (DEP) 功能的详细的说明](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [数据执行保护](/windows/desktop/Memory/data-execution-prevention)

- [数据执行保护 (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**框。 选择**确定**或**应用**以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
