---
title: ARM 汇编程序指令 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c37e010caa6c7cfb44ddaf2f7dd1e28bbb5c291
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717699"
---
# <a name="arm-assembler-directives"></a>ARM 汇编程序指令

大多数情况下，Microsoft ARM 汇编程序结合使用 ARM 程序集语言中所述[ARM 编译器 armasm 参考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。 但是，某些程序集指令的 Microsoft 实现不同于 ARM 程序集指令。 本文介绍的差异。

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Microsoft 实现的 ARM 程序集指令

- 区域

   Microsoft ARM 汇编程序支持这些`AREA`属性： `ALIGN`， `CODE`， `CODEALIGN`， `DATA`， `NOINIT`， `READONLY`， `READWRITE`， `THUMB`， `ARM`。

   除之外的所有`THUMB`并`ARM`工作中所述[ARM 编译器 armasm 参考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。

   在 Microsoft ARM 汇编程序`THUMB`指示`CODE`节包含 Thumb 代码，并且是默认值为`CODE`部分。  `ARM` 指示的部分包含 ARM 代码。

- ATTR

   不支持。

- 代码 16

   不支持，因为它意味着 Microsoft ARM 汇编程序不允许的 pre UAL Thumb 语法。  使用`THUMB`指令相反，以及 UAL 语法。

- 常见

   不支持指定的一种常见区域的对齐方式。

- DCDO

   不支持。

- `DN`, `QN`, `SN`

   不支持指定的类型或通道上注册别名。

- 条目

   不支持。

- EQU

   不支持指定的定义的符号的类型。

- `EXPORT` 和 `GLOBAL`

   指定导出使用此语法：

   > **导出**|**GLOBAL** <em>符号</em>{**[**<em>类型</em>**]**}

   *符号*是要导出的符号。  [*类型*]，如果指定，可以是`[DATA]`以指示数据点符号或`[FUNC]`以指示符号是否指向代码。 `GLOBAL` 是的同义词`EXPORT`。

- EXPORTAS

   不支持。

- 帧

   不支持。

- `FUNCTION` 和 `PROC`

   尽管程序集语法支持的自定义规范对过程调用约定，通过列出调用方保存和被调用方保存的寄存器 Microsoft ARM 汇编程序接受语法但忽略寄存器列表。  在组装器生成的调试信息支持的默认调用约定。

- `IMPORT` 和 `EXTERN`

   指定导入使用此语法：

   > **导入**|**EXTERN** *符号*{**，弱***别名*{**，类型***t*}}

   *符号*是要导入的符号名称。

   如果`WEAK`*别名*未指定，它表明*符号*是弱外部。 如果没有定义为其找到在链接时，则对它的所有引用改为都绑定到*别名*。

   如果`TYPE` *t*指定了，则*t*指示如何链接器将尝试解决*符号*。  有关这些值*t*可使用：

   |“值”|描述|
   |-|-|
   |1|不执行库搜索*符号*|
   |2|执行库搜索*符号*|
   |3|*符号*是其别名*别名*（默认值）|

   `EXTERN` 是的同义词`IMPORT`，只不过*符号*导入仅在没有对它在当前程序集的引用。

- MACRO

   不支持使用变量来保存宏的条件代码。 宏不支持参数的默认值。

- NOFP

   不支持。

- `OPT`, `TTL`, `SUBT`

   不支持，因为 Microsoft ARM 汇编程序不会生成列表。

- PRESERVE8

   不支持。

- 重定位

   `RELOC n` 可以仅按照指令或数据定义指令。 没有任何"匿名符号"可以重新定位。

- 需要

   不支持。

- REQUIRE8

   不支持。

- THUMBX

   不受支持，因为 Microsoft ARM 汇编程序不支持 Thumb 2EE 指令集。

## <a name="see-also"></a>请参阅

[ARM 汇编程序命令行参考](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM 汇编程序诊断消息](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
