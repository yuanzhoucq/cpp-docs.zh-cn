---
title: "快捷键的 Key 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Key 属性"
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 快捷键的 Key 属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面是快捷键对应表中 Key 属性的合法项：  
  
-   十进制格式中 0 到 255 之间的整数。  该值确定值被视为 ASCII 还是 ANSI，如下所示：  
  
    -   单个数字始终解释为相应的键，而不是 ASCII 或 ANSI 值。  
  
    -   当从 1 到 26 的值之前有零时，它们被解释为 ^A 到 ^Z，表示在与 Ctrl 键同时按下时字母表字母的 ASCII 值。  
  
    -   从 27 到 32 的值始终解释为从 027 到 032 的三位数十进制值。  
  
    -   从 033 到 255 的值前面无论是否有零都被解释为 ANSI 值。  
  
-   单个键盘字符。  大写字母 A \- Z 或数字 0 \- 9 既可以是 ASCII 值又可以是虚拟键值；而其他任何字符只能是 ASCII。  
  
-   前面有插入符号 \(^\) 且范围在 A \- Z（仅为大写）的单个键盘字符（如 ^C）。  当按住 Ctrl 键时按该键将输入该键的 ASCII 值。  
  
    > [!NOTE]
    >  当输入 ASCII 值时，修饰符属性选项会受到限制。  仅有的可用控制键是 Alt 键。  
  
-   任何有效的虚拟键标识符。  快捷键对应表中的“项”下拉框包含一系列标准的虚拟键标识符。  
  
    > [!TIP]
    >  另一种定义快捷键的方式是：右击快捷键对应表中的一项或多个项，从快捷菜单中选择**“键入的下一个键”**，然后按键盘上的任何键或组合键。  也可从“编辑”菜单中使用“键入的下一个键”命令。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Editing in an Accelerator Table](../windows/editing-in-an-accelerator-table.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)