---
title: "ARM Assembler Command-Line Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ARM Assembler Command-Line Reference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文提供了有关 Microsoft 臂的汇编程序命令行信息 *armasm*，其中 ARMv7 拇指汇编语言编译 Microsoft 实现的通用对象文件格式 \(COFF\)。  可以将链接器链接 COFF 对象代码通过臂汇编程序或 C 编译器，由管理员创建的对象库一起生成的代码。  
  
## 语法  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### 参数  
 `options`  
 \-错误`filename`  
 重定向错误和警告消息`filename`。  
  
 \-i`dir[;dir]`  
 将指定的目录添加到包含搜索路径。  
  
 \-预定义`directive`  
 指定设置、 SETL 或设置指令来预定义的符号。  示例：**armasm.exe \-predefine "COUNT SETA 150" source.asm**。  有关详细信息，请参阅[臂组装器工具指南](http://go.microsoft.com/fwlink/?LinkId=246102)。  
  
 \-nowarn  
 禁用所有警告消息。  
  
 \-忽略`warning`  
 禁用指定的警告。  可能的值，请参阅有关警告的部分。  
  
 \-帮助  
 打印命令行帮助消息。  
  
 \-计算机`machine`  
 指定要在 PE 标头中设置的计算机类型。  可能的值为`machine`是：   
**ARM**\-将 IMAGE\_FILE\_MACHINE\_ARMNT 设置的计算机类型。  这是默认值。   
**THUMB**\-将 IMAGE\_FILE\_MACHINE\_THUMB 设置的计算机类型。  
  
 \-oldit  
 生成 ARMv7 样式 IT 块。  默认情况下 ARMv8 兼容生成 IT 块。  
  
 \-通过`filename`  
 阅读更多的命令行参数，从`filename`。  
  
 \-16  
 装配源为 16 位滚动块的说明。  这是默认值。  
  
 \-32  
 装配为 32 位 ARM 指令的源。  
  
 \-g  
 生成调试信息。  
  
 \-errorReport：`option`  
 指定内部如何组装器错误报告给 Microsoft。  可能的值为`option`是：   
**none**\-\-不发送报告。  
**prompt**— 提示用户立即发送报告。  
**queue**— 提示用户在下次管理员登录时发送报告。  这是默认值。   
**send**— 自动发送的报告。  
  
 `sourcefile`  
 源文件的名称。  
  
 `objectfile`  
 在对象 （输出） 文件的名称。  
  
 下面的示例演示如何在典型方案中使用 armasm。  首先，使用 armasm 生成一个对象 \(.obj\) 文件的程序集语言源 \(.asm\) 文件。  然后，使用 CL 命令行 C 编译器编译的源 （.c\) 文件，还指定 ARM 的对象文件链接的链接器选项。  
  
 **armasm myasmcode.asm \-o myasmcode.obj**  
  
 **cl myccode.c \/link myasmcode.obj**  
  
## 请参阅  
 [ARM Assembler Diagnostic Messages](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [ARM Assembler Directives](../../assembler/arm/arm-assembler-directives.md)