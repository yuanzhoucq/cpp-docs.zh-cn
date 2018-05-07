---
title: -ERRORREPORT （报告内部链接器错误） |Microsoft 文档
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
dev_langs:
- C++
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72e620e5347d422a8de66cba3ea9cfd601bb3f29
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT（报告内部链接器错误）

> **/errorreport:**[**无** | **提示符** | **队列** | **发送**]

## <a name="arguments"></a>自变量

**none**  
不收集有关内部编译器错误的报告，或不向 Microsoft 发送报告。

**提示**  
当您收到内部编译器错误时，提示您发送报告。 **提示符**在开发环境中编译应用程序是默认设置。

**queue**  
将错误报告排入队列。 当使用管理员特权登录时，将显示一个窗口，以便您可以记录中被记录的上次报告任何失败 （你不会提示发送故障报告一次以上每隔三天）。 **队列**时在命令提示符下编译的应用程序是默认设置。

**发送**  
如果报表通过 Windows 错误报告服务设置自动向 Microsoft 发送报告内部编译器错误。

## <a name="remarks"></a>备注

**/ERRORREPORT**选项允许您直接向 Microsoft 提供内部编译器错误 (ICE) 信息。

选项 **/errorreport:send**自动将错误信息发送给 Microsoft，如果启用了 Windows 错误报告服务设置。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 打开**配置属性** > **链接器** > **高级**属性页。

1. 修改**错误报告**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>。

## <a name="see-also"></a>请参阅

[/errorReport（报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)  
[设置链接器选项](../../build/reference/setting-linker-options.md)  
[链接器选项](../../build/reference/linker-options.md)  
