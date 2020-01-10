---
title: /NXCOMPAT（与数据执行保护兼容）
description: 描述 Microsoft C/C++ （MSVC）/NXCOMPAT 链接器选项，该选项将可执行文件标记为与数据执行保护（DEP）兼容。
ms.date: 12/17/2019
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: f3a0906a49e3524fff3e1ef1643d1eceee28f169
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298982"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT（与数据执行保护兼容）

指示可执行文件与 Windows 数据执行保护功能兼容。

## <a name="syntax"></a>语法

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>备注

默认情况下， **/NXCOMPAT**为 on。

**/NXCOMPAT： NO**可用于将可执行文件显式指定为与数据执行保护不兼容。

有关数据执行保护的详细信息，请参阅以下文章：

- [数据执行保护](/windows/win32/Memory/data-execution-prevention)

- [数据执行保护（Windows Embedded）](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1.  > **链接器** > "**命令行**" 属性页选择**配置属性**。

1. 在 "**附加选项**" 框中输入选项。 选择 **"确定" 或 "** **应用**" 以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>另请参阅

[MSVC 链接器引用](linking.md)\
[MSVC 链接器选项](linker-options.md)
