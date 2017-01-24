---
title: "SEGMENT | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEGMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SEGMENT directive"
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# SEGMENT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义调用具有 *的* 名称为程序段区段功能  
  
## 语法  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### 参数  
 *对齐*  
 的内存地址的范围段的一个起始地址中选择。  对齐类型可以是下列任一操作:  
  
|对齐类型|起始地址|  
|----------|----------|  
|**BYTE**|下一个可用的字节地址。|  
|**WORD**|下一个可用的运行地址 \(每个单词 2 个字节\)。|  
|**DWORD**|下一个可用的双字地址 \(每双字 4 个字节\)。|  
|**巴拉**|下一个可用的段地址 \(每个段落 16 个字节\)。|  
|**页**|下一个可用的页的地址 \(每页的 256 个字节\)。|  
|**对齐**\(n\)|下一个可用的 *第 n 个*字节地址。  请参见 " 备注 " 部分有关更多信息。|  
  
 如果此参数未指定，则使用默认情况下 **巴拉** 。  
  
 *合并*  
 **公共**， **堆栈**， **常见**， **内存**， **在***地址*， **专用**  
  
 *使用*  
 **USE16**， **USE32**， **简单**  
  
 `characteristics`  
 **信息**、 **读取**、 **写入**、 **执行**、 **共享**、 **NOPAGE**、 **NOCACHE**和 **放弃**  
  
 这些仅为 COFF 支持和对应于相同名称的 COFF 部分属性 \(例如， **共享** 对应于 IMAGE\_SCN\_MEM\_SHARED\)。  读取设置 IMAGE\_SCN\_MEM\_READ 标志。  该过时只读标志使该部分清除 IMG\_SCN\_MEM\_WRITE 标志。  如果任何 `characteristics` 设置，不使用默认属性，并且只程序员指定的标志有效。  
  
 `ALIAS(` `string` `)`  
 此字符串用作该节的名称在发出的 COFF 对象。  使用相同的外部名称创建多个部分，带 DISTINCT MASM 段名。  
  
 不支持与 **\/omf**。  
  
 `class`  
 指定如何在汇编的文件应合并和排序段。  典型的值为， `'DATA'`、 `'CODE'`、 `'CONST'` 和 `'STACK'`  
  
## 备注  
 为 `ALIGN(``n``)`， `n` 可能为任何 2 的次幂从 1 到 8192;不支持与 **\/omf**。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)