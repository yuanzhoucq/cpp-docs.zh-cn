---
title: /NXCOMPAT（与数据执行保护兼容）
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: a8550337189f9c92a1c8a8d86f2f9b2b829bbc3e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813313"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT（与数据执行保护兼容）

指示可执行文件是与 Windows 数据执行保护功能兼容。

## <a name="syntax"></a>语法

> **/NXCOMPAT**[**:NO**]

## <a name="remarks"></a>备注

默认情况下 **/NXCOMPAT**上。

**/Nxcompat: no**可用于显式指定为不与数据执行保护兼容的可执行文件。

有关数据执行保护的详细信息，请参阅以下文章：

- [数据执行保护 (DEP) 功能的详细的说明](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [数据执行保护](/windows/desktop/Memory/data-execution-prevention)

- [数据执行保护 (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**框。 选择**确定**或**应用**以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
