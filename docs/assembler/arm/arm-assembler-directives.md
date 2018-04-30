---
title: ARM 汇编程序指令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9f5ab97fb9ccdff19206b829383c622efd3f7921
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="arm-assembler-directives"></a>ARM 汇编程序指令
大多数情况下，Microsoft ARM 汇编程序使用 ARM 程序集语言，这记录在的第 7 章[ARM 汇编程序工具指南](http://go.microsoft.com/fwlink/p/?linkid=246102)。 但是，某些程序集指令的 Microsoft 实现与不同 ARM 程序集指令。 本文介绍的区别。  
  
## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Microsoft 实现的 ARM 程序集指令  
 区域  
 Microsoft ARM 汇编程序支持这些区域属性： 对齐，代码、 CODEALIGN、 数据、 NOINIT、 READONLY、 READWRITE、 THUMB、 ARM。  
  
 用拇指和臂除外工作如中所述[ARM 汇编程序工具指南](http://go.microsoft.com/fwlink/p/?linkid=246102)。  
  
 在 Microsoft ARM 汇编程序 THUMB 指示代码节包含 Thumb 代码，并且是代码段的默认值。  ARM 指示的部分包含 ARM 代码。  
  
 ATTR  
 不支持。  
  
 代码 16  
 不支持，因为它意味着 Microsoft ARM 汇编程序不允许的前期 UAL Thumb 语法。  请改用 THUMB 指令，以及 UAL 语法。  
  
 常见  
 不支持的常见区域的对齐方式的规范。  
  
 DCDO  
 不支持。  
  
 DN，QN，SN  
 不支持的类型或上注册别名 lane 的规范。  
  
 条目  
 不支持。  
  
 EQU  
 不支持规范定义的符号的类型。  
  
 导出和全局  
 ```  
EXPORTsym {[type]}  
```  
  
 `sym` 是要导出的符号。  `[type]`如果指定，可以是`[DATA]`以指示符号指向数据或`[FUNC]`以指示符号指向代码。  
  
 全局是导出的同义词。  
  
 EXPORTAS  
 不支持。  
  
 帧  
 不支持。  
  
 函数和过程  
 虽然程序集语法支持的规范的自定义过程通过列出调用方保存和那些被调用方保存的寄存器调用约定 Microsoft ARM 汇编程序接受语法但忽略寄存器列表中。  由汇编程序生成的调试信息支持的默认调用约定。  
  
 导入和 EXTERN  
 ```  
IMPORT sym{, WEAK alias{, TYPE t}}  
```  
  
 `sym` 是要导入的符号的名称。  
  
 如果弱`alias`指定，它表明`sym`是弱外部。 如果在链接时，找到的它没有定义，则对它的所有引用改为都绑定到`alias`。  
  
 如果类型`t`未指定，则`t`指示如何链接器将尝试解决`sym`。  有关这些值`t`还可能有：   
1-不执行库搜索 `sym`  
2-执行库搜索 `sym`  
3-`sym`是的别名`alias`（默认值）  
  
 EXTERN 是导入，只不过的同义词`sym`仅在没有引用了它在当前程序集导入。  
  
 MACRO  
 不支持的一个变量以保存宏的条件代码使用。 宏不支持参数的默认值。  
  
 NOFP  
 不支持。  
  
 选择，TTL、 SUBT  
 不支持，因为 Microsoft ARM 汇编程序不会生成列表。  
  
 PRESERVE8  
 不支持。  
  
 RELOC  
 `RELOC n` 仅可以按照指令或数据定义指令。 没有任何"匿名符号"可重新定位。  
  
 需要  
 不支持。  
  
 REQUIRE8  
 不支持。  
  
 THUMBX  
 中不受支持，因为 Microsoft ARM 汇编程序不支持 Thumb 2EE 指令集。  
  
## <a name="see-also"></a>请参阅  
 [ARM 汇编程序命令行参考](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM 汇编程序诊断消息](../../assembler/arm/arm-assembler-diagnostic-messages.md)