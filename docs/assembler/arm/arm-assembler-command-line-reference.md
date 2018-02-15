---
title: "ARM 汇编程序命令行参考 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb6b395ec8f47e820cb3184c0d88b4c91e712eb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="arm-assembler-command-line-reference"></a>ARM 汇编程序命令行参考
这篇文章提供有关 Microsoft ARM 汇编程序命令行信息*armasm*，用于编译到的 Microsoft 实现的通用对象文件格式 (COFF) 的 ARMv7 Thumb 程序集语言。 链接器可以将 COFF 代码与通过 ARM 汇编程序或由 C 编译器，结合了由管理员创建的对象库生成的对象代码链接。  
  
## <a name="syntax"></a>语法  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### <a name="parameters"></a>参数  
 `options`  
 -错误 `filename`  
 重定向错误和警告消息到`filename`。  
  
 -i `dir[;dir]`  
 将指定的目录添加到包含搜索路径。  
  
 -预定义 `directive`  
 指定一个种设置、 SETL 或集的指令，用于预定义符号。 示例： **armasm.exe 的预定义表单"计数设置 150"source.asm**。有关详细信息，请参阅[ARM 汇编程序工具指南](http://go.microsoft.com/fwlink/p/?linkid=246102)。  
  
 -nowarn  
 禁用所有警告消息。  
  
 -忽略 `warning`  
 禁用指定的警告。 有关可能的值，请参阅有关警告的部分。  
  
 -帮助  
 打印命令行帮助消息。  
  
 -计算机 `machine`  
 指定要 PE 标头中设置的计算机类型。  可能的值有`machine`是：  
**ARM**-将机类型设置为 IMAGE_FILE_MACHINE_ARMNT。 这是默认设置。   
**THUMB**-将机类型设置为 IMAGE_FILE_MACHINE_THUMB。  
  
 -oldit  
 生成 ARMv7 样式 IT 块。  默认情况下，ARMv8 兼容生成 IT 块。  
  
 -via `filename`  
 读取从其他命令行参数`filename`。  
  
 -16  
 为 16 位 Thumb 说明组建源。  这是默认设置。  
  
 -32  
 作为 32 位 ARM 指令组建源。  
  
 -g  
 生成调试信息。  
  
 -errorReport: `option`  
 指定如何将内部汇编程序错误报告给 Microsoft。  可能的值有`option`是：   
**无**— 不发送报告。   
**提示符**— 提示用户立即发送报告。   
**队列**— 提示用户在下一步的管理员登录名发送报告。 这是默认设置。   
**发送**-自动发送报告。  
  
 `sourcefile`  
 源文件的名称。  
  
 `objectfile`  
 在对象 （输出） 文件的名称。  
  
 下面的示例演示如何在典型的方案中使用 armasm。 首先，使用 armasm 生成的对象 (.obj) 文件的程序集语言源 (.asm) 文件。 然后，使用 CL 命令行 C 编译器来编译源 (.c) 文件，并还指定链接器选项将 ARM 对象文件链接。  
  
 **armasm myasmcode.asm-o myasmcode.obj**  
  
 **cl myccode.c /link myasmcode.obj**  
  
## <a name="see-also"></a>请参阅  
 [ARM 汇编程序诊断消息](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [ARM 汇编程序指令](../../assembler/arm/arm-assembler-directives.md)