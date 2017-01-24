---
title: "ARM Assembler Directives | Microsoft Docs"
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
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ARM Assembler Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

大多数情况下，Microsoft 臂组装器使用 ARM 程序集语言中，在第 7 章的[臂组装器工具指南](http://go.microsoft.com/fwlink/?LinkId=246102)。  但是，某些程序集指令的 Microsoft 实现不同臂程序集指令。  这篇文章解释的差异。  
  
## Microsoft 臂的程序集指令的实现  
 区域  
 Microsoft 臂汇编程序支持这些区域属性： 对齐、 代码、 CODEALIGN、 数据、 NOINIT、 只读、 读写、 缩略图、 臂。  
  
 除缩略图和 ARM 之外的所有工作中所述[臂组装器工具指南](http://go.microsoft.com/fwlink/?LinkId=246102)。  
  
 Microsoft 臂组装器中，在滚动块表示的代码段包含缩略图的代码，是代码节的默认值。  ARM 表示该部分包含臂代码。  
  
 属性  
 不支持。  
  
 代码 16  
 因为它意味着前的双重拇指语法中，Microsoft 臂汇编程序不允许不受支持。  滚动块的指令，以及双重语法使用。  
  
 通用  
 不支持的公共区域对齐方式的规范。  
  
 DCDO  
 不支持。  
  
 DN，QN，SN  
 不支持类型或车道上注册别名的规范。  
  
 条目  
 不支持。  
  
 EQU  
 规范定义的符号的类型不受支持。  
  
 导出和全球  
 ```  
  
EXPORTsym {[type]}  
  
```  
  
 `sym`为要导出的符号。  `[type]`如果指定，可以是`[DATA]`表示该符号所指向的数据或`[FUNC]`表示该符号所指向的代码。  
  
 导出全局是同义词。  
  
 EXPORTAS  
 不支持。  
  
 框架  
 不支持。  
  
 函数和过程  
 尽管该程序集的语法支持自定义规范过程调用约定，通过列出被调用方保存以及那些被调用方保存的寄存器 Microsoft 臂组装器接受语法但忽略寄存器列表。  调试信息生成汇编程序的支持的默认调用约定。  
  
 导入和外部  
 ```  
  
IMPORT sym{, WEAK alias{, TYPE t}}  
  
```  
  
 `sym`是要导入的元件的名称。  
  
 如果弱`alias`指定，则说明没有`sym`是弱外部。  如果在链接时，发现它没有定义，则对它的所有引用而是都绑定到`alias`。  
  
 如果类型 `t`指定，然后`t`指示如何尝试链接器解析`sym`。  这些值的`t`可能会：   
1\-不执行库搜索功能`sym`   
2\-执行库搜索功能`sym`   
3\-\-`sym`是`alias` （默认值）  
  
 外部是导入，只是同义词`sym`只有在当前程序集的引用，则导入。  
  
 宏  
 不支持一个变量来保存宏的状态代码的使用。  宏不支持参数的默认值。  
  
 NOFP  
 不支持。  
  
 可选，TTL，SUBT  
 不支持，因为 Microsoft 臂汇编程序不生成列表。  
  
 PRESERVE8  
 不支持。  
  
 重定位  
 `RELOC n`只有按照指令或数据定义指令。  没有任何"匿名"的符号可以重新定位。  
  
 要求  
 不支持。  
  
 REQUIRE8  
 不支持。  
  
 THUMBX  
 不支持，因为 Microsoft 臂组装器不支持滚动块 2EE 指令集。  
  
## 请参阅  
 [ARM Assembler Command\-Line Reference](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM Assembler Diagnostic Messages](../../assembler/arm/arm-assembler-diagnostic-messages.md)