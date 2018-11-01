---
title: ARM 汇编程序命令行参考
ms.date: 08/30/2018
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: f49b59a81fbe5f11c0f219d1e1fe83a4ee811c7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579223"
---
# <a name="arm-assembler-command-line-reference"></a>ARM 汇编程序命令行参考

本文提供了有关 Microsoft ARM 汇编程序命令行信息*armasm*，这将 ARMv7 Thumb 程序集语言编译为 Microsoft 实现的通用对象文件格式 (COFF)。 链接器可以链接 COFF 代码和通过 ARM 汇编程序或由 C 编译器，以及创建的库管理器的对象库生成的对象代码。

## <a name="syntax"></a>语法

> **armasm** [*选项*] *sourcefile* *objectfile*
> **armasm** [*选项*] **-o** *objectfile* *sourcefile*

### <a name="parameters"></a>参数

*options*<br/>
零个或多个以下的组合：

- **-错误***文件名*<br/>
   将错误和警告消息到重定向*文件名*。

- **-i** *dir*[**;**<em>dir</em>]<br/>
   将指定的目录添加到包含搜索路径。

- **-预定义***指令*<br/>
   指定如果、 SETL 或集的指令预定义符号。<br/>
   示例： **armasm.exe-预定义"计数如果 150"source.asm**<br/>
   有关详细信息，请参阅[ARM 编译器 armasm 参考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。

- **-nowarn**<br/>
   禁用所有警告消息。

- **-忽略***警告*<br/>
   禁用指定的警告。 可能的值，请参阅有关的警告的部分。

- **-help**<br/>
   打印命令行帮助消息。

- **-machine** *机*<br/>
   指定要 PE 标头中设置的计算机类型。  可能的值*机*是：<br/>
   **ARM**— 计算机类型设置为 IMAGE_FILE_MACHINE_ARMNT。 这是默认设置。<br/>
   **THUMB**— 计算机类型设置为 IMAGE_FILE_MACHINE_THUMB。

- **-oldit**<br/>
   生成 ARMv7 样式 IT 块。  默认情况下，ARMv8 兼容生成 IT 块。

- **-通过***文件名*<br/>
   读取其他命令行参数从*文件名*。

- **-16**<br/>
   作为 16 位 Thumb 说明组合源。  这是默认设置。

- **-32**<br/>
   作为 32 位 ARM 指令组合源。

- **-g**<br/>
   生成调试信息。

- **-errorReport:** *选项*<br/>
   指定如何将内部汇编程序错误报告给 Microsoft。  可能的值*选项*是：<br/>
   **无**-不发送报告。<br/>
   **提示符**-提示用户立即发送报告。<br/>
   **队列**-提示用户在下一步的管理员登录时发送报告。 这是默认设置。<br/>
   **发送**-自动发送报告。

*sourcefile*<br/>
源文件的名称。

*objectfile*<br/>
在对象 （输出） 文件的名称。

## <a name="remarks"></a>备注

下面的示例演示如何在典型方案中使用 armasm。 首先，使用 armasm 生成的对象 (.obj) 文件的程序集语言源 (.asm) 文件。 然后，CL 命令行 C 编译器用于编译源 (.c) 文件，并指定链接器选项以将 ARM 对象文件链接。

**armasm myasmcode.asm-o myasmcode.obj**

**cl myccode.c /link myasmcode.obj**

## <a name="see-also"></a>请参阅

[ARM 汇编程序诊断消息](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
[ARM 汇编程序指令](../../assembler/arm/arm-assembler-directives.md)<br/>
