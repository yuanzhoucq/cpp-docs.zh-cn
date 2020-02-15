---
title: ARM 汇编程序命令行参考
description: Microsoft ARM 组装器命令行选项的参考指南。
ms.date: 02/09/2020
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: a63273e8d21e7a28574ec79d62c15f29ee59cd50
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257374"
---
# <a name="arm-assembler-command-line-reference"></a>ARM 汇编程序命令行参考

本文提供了有关 Microsoft ARM 汇编程序**armasm**的命令行信息。 **armasm**将 ARMv7 Thumb 汇编语言组合到 Microsoft 的通用对象文件格式（COFF）实现中。 链接器可以链接 ARM 组装器和 C 编译器生成的 COFF 代码对象。 它可以链接到管理员创建的对象库。

## <a name="syntax"></a>语法

> **`armasm`** [*options*] *source_file* *object_file*\
> **`armasm`** [*options*] **`-o`** *object_file* *source_file*

### <a name="parameters"></a>parameters

*选项*\
以下零个或多个选项的组合：

- **`-errors`** *文件名*\
   将错误和警告消息重定向到*文件名*。

- **`-i`** *dir*[ **`;`** <em>dir</em>] \
   将指定的目录添加到包含搜索路径。

- **`-predefine`** *指令*\
   指定设置、SETL 或 SETS 指令以预定义符号。 \
   示例： `armasm.exe -predefine "COUNT SETA 150" source.asm`\
   有关详细信息，请参阅[ARM 编译器 Armasm 参考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。

- **`-nowarn`**\
   禁用所有警告消息。

- **`-ignore`** *警告*\
   禁用指定的警告。 有关可能的值，请参阅有关警告的部分。

- **`-help`**\
   打印命令行帮助消息。

- **`-machine`** *机*\
   指定要在 PE 标头中设置的计算机类型。  *计算机*的可能值为： \
   **ARM**-将计算机类型设置为 IMAGE_FILE_MACHINE_ARMNT。 此选项是默认选项。
   **THUMB**-将计算机类型设置为 IMAGE_FILE_MACHINE_THUMB。

- **`-oldit`**\
   生成 ARMv7 样式的块。  默认情况下，将生成与 ARMv8 兼容的 IT 块。

- **`-via`** *文件名*\
   从*文件名*中读取其他命令行参数。

- **`-16`**\
   将源组装为16位拇指说明。  此选项为默认值。

- **`-32`**\
   将源组装为32位 ARM 指令。

- **`-g`**\
   生成调试信息。

- **`-errorReport:`** *选项*\
   已弃用此选项。 从 Windows Vista 开始，错误报告由[Windows 错误报告（WER）](/windows/win32/wer/windows-error-reporting)设置控制。

*source_file*\
源文件名。

*object_file*\
对象（输出）文件的名称。

## <a name="remarks"></a>备注

下面的示例演示如何在典型方案中使用 armasm。 首先，使用 armasm 将程序集语言源（.asm）文件生成到对象（.obj）文件。 然后，使用 CL 命令行 C 编译器编译源（.c）文件，并指定链接 ARM 对象文件的链接器选项。

```cmd
armasm myasmcode.asm -o myasmcode.obj
cl myccode.c /link myasmcode.obj
```

## <a name="see-also"></a>另请参阅

[ARM 汇编程序诊断消息](../../assembler/arm/arm-assembler-diagnostic-messages.md)\
[ARM 汇编程序指令](../../assembler/arm/arm-assembler-directives.md)
