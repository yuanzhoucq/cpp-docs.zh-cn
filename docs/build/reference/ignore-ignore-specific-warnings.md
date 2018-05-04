---
title: -忽略 （忽略特定警告） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /OVERWRITE
dev_langs:
- C++
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b096fc12f69fbe637a3067646c20f6d520a9250f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE（忽略特定警告）
```  
/IGNORE:warning[,warning]  
```  
  
## <a name="parameters"></a>参数  
 `warning`  
 要禁止显示的链接器警告编号，在 4000 到 4999 的范围内。  
  
## <a name="remarks"></a>备注  
 默认情况下，链接会报告所有警告。 指定**忽略：** `warning`以告知链接器禁止显示特定的警告编号。 若要忽略多个警告，请用逗号分隔警告编号。  
  
 链接器不允许忽略某些警告。 此表列出了不抑制的警告**忽略**:  
  
|链接器警告||  
|--------------------|-|  
|LNK4017|目标平台不支持 `keyword` 语句持；已忽略|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|无法识别的选项“`option`”；已忽略|  
|LNK4062|`option`与不兼容`architecture`目标计算机; 忽略的选项|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|由于“`option1`”规范而忽略“`option2`”|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|入口点“`function`”不是带参数“`number`”字节的 __stdcall；图像可能无法运行|  
|LNK4088|图像生成的原因是 /FORCE 选项；图像可能无法运行|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|无使用选项“`option`”指定的参数；忽略转换|  
|LNK4203|读取项目数据库“`filename`”时出错；正在链接对象，如同没有调试信息一样|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|`filename`缺少的调试信息引用模块中; 正在链接对象，如同没有调试信息|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|`filename`缺少当前的调试信息，用于引用模块中; 正在链接对象，如同没有调试信息|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|未找到预编译的类型信息；“`filename`”未链接或未重写；正在链接对象，如同没有调试信息一样|  
|LNK4207|`filename`编译 /Yc /Yu /Z7; 无法创建 PDB; 重新编译使用 /Zi; 链接对象如同没有调试信息|  
|LNK4208|“`filename`”中的 PDB 格式不兼容；删除并重新生成；正在链接对象，如同没有调试信息一样|  
|LNK4209|调试信息损坏；重新编译模块；正在链接对象，如同没有调试信息一样|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|不再支持 `option`；已忽略|  
|LNK4228|`option`dll 无效; 已忽略|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|发现无效的指令 /`directive`；已忽略|  
  
 通常，不能忽略的链接器警告显示你应修复的生成故障、命令行错误或配置错误。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在**链接器**文件夹，选择**命令行**属性页。  
  
3.  修改**其他选项**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。