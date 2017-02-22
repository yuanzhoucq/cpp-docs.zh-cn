---
title: "/IGNORE（忽略特定警告） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ignore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IGNORE 链接器选项"
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# /IGNORE（忽略特定警告）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IGNORE:warning[,warning]  
```  
  
## 参数  
 `warning`  
 要禁止显示的链接器警告编号，在 4000 到 4999 的范围内。  
  
## 备注  
 默认情况下，链接会报告所有警告。  指定 **\/IGNORE:**`warning` 通知链接器禁止显示特定的警告编号。  若要忽略多个警告，请用逗号分隔警告编号。  
  
 链接器不允许忽略某些警告。  此表列出了由 **\/IGNORE** 禁止显示的警告：  
  
|链接器警告||  
|-----------|-|  
|LNK4017|目标平台不支持 `keyword` 语句持；已忽略|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|无法识别的选项“`option`”；已忽略|  
|LNK4062|'“`option`”与“`architecture`”目标计算机不兼容；选项已忽略|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|由于“`option2`”规范而忽略“`option1`”|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|入口点“`function`”不是带参数“`number`”字节的 \_\_stdcall；图像可能无法运行|  
|LNK4088|图像生成的原因是 \/FORCE 选项；图像可能无法运行|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|无使用选项“`option`”指定的参数；忽略转换|  
|LNK4203|读取项目数据库“`filename`”时出错；正在链接对象，如同没有调试信息一样|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`”缺少引用模块的调试信息；正在链接对象，如同没有调试信息一样|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`”缺少引用模块的当前调试信息；正在链接对象，如同没有调试信息一样|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|未找到预编译的类型信息；“`filename`”未链接或未重写；正在链接对象，如同没有调试信息一样|  
|LNK4207|'`filename`”已编译 \/Yc \/Yu \/Z7；无法创建 PDB；重新编译 \/Zi；正在链接对象，如同没有调试信息一样|  
|LNK4208|“`filename`”中的 PDB 格式不兼容；删除并重新生成；正在链接对象，如同没有调试信息一样|  
|LNK4209|调试信息损坏；重新编译模块；正在链接对象，如同没有调试信息一样|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|不再支持 `option`；已忽略|  
|LNK4228|'`option`”对 DLL 无效；已忽略|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|发现无效的指令 \/`directive`；已忽略|  
  
 通常，不能忽略的链接器警告显示你应修复的生成故障、命令行错误或配置错误。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”对话框。  有关详细信息，请参阅 [使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在“链接器”文件夹中，选择“命令行”属性页。  
  
3.  修改“附加选项”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。