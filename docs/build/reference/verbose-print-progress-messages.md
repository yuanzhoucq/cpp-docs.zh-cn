---
title: -VERBOSE （打印进度消息） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
dev_langs:
- C++
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee1bf99cdf27e432bf8bdf6b7c0e48a84aeaac21
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377464"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE（打印进度消息）
```  
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]  
```  
  
## <a name="remarks"></a>备注  
 链接器将发送到的链接会话进度信息**输出**窗口。 命令行上的信息发送到标准输出和可以定向到一个文件。  
  
|选项|描述|  
|------------|-----------------|  
|/VERBOSE|显示有关链接过程的详细信息。|  
|/VERBOSE: ICF|显示有关的使用得到的结果的链接器活动的信息[/opt: icf](../../build/reference/opt-optimizations.md)。|  
|/VERBOSE: INCR|有关增量链接过程的信息。|  
|/VERBOSE: LIB|显示进度消息，该消息仅指示所搜索的库。<br /><br /> 显示的信息，包括库搜索进程，并列出每个库和对象名称 （完整路径），正在从库中，和引用的符号的对象列表中解析的符号。|  
|/VERBOSE: REF|显示信息的使用得到的结果的链接器活动[/opt: ref](../../build/reference/opt-optimizations.md)。|  
|/VERBOSE: SAFESEH|显示有关与安全异常处理时不兼容的模块的信息[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)未指定。|  
|/VERBOSE:UNUSEDLIBS|显示有关在创建映像时未使用的任何库文件的信息。|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**链接器**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  添加到选项**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)