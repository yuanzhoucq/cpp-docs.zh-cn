---
title: /VERBOSE（打印进度消息）
ms.date: 06/13/2019
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: bbf7b5966c741535f26202979cbfd71f839cc537
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141666"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE（打印进度消息）

在链接过程中的输出进度消息。

## <a name="syntax"></a>语法

> **/VERBOSE**\[ **:** {**CLR**|**ICF**|**INCR**|**LIB**|**REF**|**SAFESEH**|**UNUSEDDELAYLOAD**|**UNUSEDLIBS**}\]

## <a name="remarks"></a>备注

链接器将发送到链接的会话的进度信息**输出**窗口。 命令行上的信息发送到标准输出和重定向到一个文件。

| 选项 | 描述 |
| ------------ | ----------------- |
| /VERBOSE | 显示有关链接的过程的详细信息。 |
| /VERBOSE:CLR | 显示有关特定链接器活动的信息对对象和元数据使用编译的[/clr](clr-common-language-runtime-compilation.md)。 |
| /VERBOSE:ICF | 显示有关链接器活动的使用而得出的信息[/opt: icf](opt-optimizations.md)。 |
| /VERBOSE:INCR | 有关增量链接过程的信息。 |
| /VERBOSE:LIB | 显示进度消息，该消息仅指示所搜索的库。<br/> 显示的信息，包括库搜索过程。 它列出了每个库和对象名称 （包含完整路径），从库中和一系列对象引用的符号解析的符号。 |
| /VERBOSE:REF | 显示有关链接器活动的使用而得出的信息[/opt: ref](opt-optimizations.md)。 |
| /VERBOSE:SAFESEH | 显示有关与安全结构化异常处理时不兼容的模块的信息[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)未指定。 |
| /VERBOSE:UNUSEDDELAYLOAD | 显示有关的任何延迟的信息加载时创建的映像，使用无符号的 Dll。 |
| /VERBOSE:UNUSEDLIBS | 显示有关在创建映像时未使用的任何库文件的信息。 |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 将选项添加到**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
