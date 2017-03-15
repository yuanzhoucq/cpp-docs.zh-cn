---
title: "资源编译器错误 RW2002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2002"
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RW2002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分析错误  
  
### 通过检查以下可能的原因进行修复  
  
1.  **需要快捷键类型（ASCII 或 VIRTKEY）**  
  
     **ACCELERATORS** 语句中的 `type` 字段必须包含 ASCII 或 VIRTKEY 值。  
  
2.  **快捷键对应表中需要 BEGIN**  
  
     **BEGIN** 关键字必须紧跟在 **ACCELERATORS** 关键字后面。  
  
3.  **对话框中需要 BEGIN**  
  
     **BEGIN** 关键字必须紧跟在 **DIALOG** 关键字后面。  
  
4.  **菜单中需要 BEGIN**  
  
     **BEGIN** 关键字必须紧跟在 **MENU** 关键字后面。  
  
5.  **RCDATA 中需要 BEGIN**  
  
     **BEGIN** 关键字必须紧跟在 **RCDATA** 关键字后面。  
  
6.  **字符串表中需要 BEGIN 关键字**  
  
     **BEGIN** 关键字必须紧跟在 **STRINGTABLE** 关键字后面。  
  
7.  **无法重用字符串常数**  
  
     在 **STRINGTABLE** 语句中您正在将同一个值使用两次。  确保您没有混合重叠十进制数值和十六进制数值。  **STRINGTABLE** 中的每个 ID 都必须是唯一的。  为取得最大效率，请使用从 16 的倍数开始的连续常数。  
  
8.  **控制字符超出范围 \[^A \- ^Z\]**  
  
     在 **ACCELERATORS** 语句中的控制字符无效。  跟在插入符号 \(**^**\) 后面的字符必须介于 A 和 Z 之间，包括 A 和 Z 在内。  
  
9. **不允许空菜单**  
  
     在 **MENU** 语句中定义的任何菜单项之前有 **END** 关键字。  资源编译器不允许空菜单。  确保在 **MENU** 语句内没有任何左引号。  
  
10. **对话框中应有 END**  
  
     **END** 关键字必须出现在 **DIALOG** 语句的结尾。  确保没有前一语句剩下的左引号。  
  
11. **菜单中应有 END**  
  
     **MENU** 语句的结尾必须有 **END** 关键字。  确保没有任何左引号或者不匹配的 **BEGIN** 和 **END** 语句对。  
  
12. **应在快捷键对应表中输入逗号**  
  
     资源编译器要求 **ACCELERATORS** 语句的 `event` 字段和 *idvalue* 字段之间有逗号。  
  
13. **应输入控件类名**  
  
     **DIALOG** 语句中的 **CONTROL** 语句的 `class` 字段必须为下列类型之一：BUTTON、COMBOBOX、EDIT、LISTBOX、SCROLLBAR、STATIC 或用户定义的。  确保正确拼写此类。  
  
14. **应输入字体名**  
  
     **DIALOG** 语句中 FONT 选项的 *typeface* 字段必须是用双引号括起来的 ASCII 字符串。  该字段指定字体的名称。  
  
15. **应输入菜单项的 ID 值**  
  
     **MENU** 语句必须包含 *menuID* 字段，该字段指定标识菜单资源的名称或序号。  
  
16. **应输入菜单字符串**  
  
     每个 **MENUITEM** 语句和 **POPUP** 语句都必须包含 *text* 字段，该字段是用双引号括起来、指定菜单项或弹出菜单名称的字符串。  **MENUITEM SEPARATOR** 语句不要求用引号括起来的字符串。  
  
17. **应输入数字命令值**  
  
     资源编译器希望在 **ACCELERATORS** 语句中有一个数字 *idvalue* 字段。  确保您已经使用 `#define` 常数指定了该值并且正确拼写了该常数。  
  
18. **应在字符串表中输入数值常数**  
  
     `#define` 语句中定义的数字常数必须紧跟在 **STRINGTABLE** 语句中 **BEGIN** 关键字之后。  
  
19. **应输入数字磅值**  
  
     **DIALOG** 语句中 FONT 选项的 *pointsize* 字段必须是整数磅值。  
  
20. **应输入数值对话框常数**  
  
     对于 *x、y、width* 和 *height* 字段，**DIALOG** 语句要求整数值。  确保这些值包括在 **DIALOG** 关键字后并且不为负数。  
  
21. **应在 STRINGTABLE 中输入字符串**  
  
     应在 **STRINGTABLE** 语句中每个 *stringid* 值之后输入字符串。  
  
22. **应输入字符串或常数快捷键命令**  
  
     资源编译器不能确定正在为快捷键设置何种键。  **ACCELERATORS** 语句中的 `event` 字段可能无效。  
  
23. **应输入 ID 号**  
  
     应为 **DIALOG** 语句中控制语句的 `id` 字段输入数字。  确保此控件 ID 有数字或 `#define` 语句。  
  
24. **应在对话框类中输入带引号的字符串**  
  
     **DIALOG** 语句中 CLASS 选项的 `class` 字段必须是整数或者用双引号括起来的字符串。  
  
25. **应在对话框标题中输入带引号的字符串**  
  
     **DIALOG** 语句中 CAPTION 选项的 `captiontext` 字段必须是用双引号括起来的 ASCII 字符串。  
  
26. **未找到文件：filename**  
  
     资源编译器命令行中指定的文件未找到。  检查该文件是否已被移动到其他目录以及文件名或路径是否正确键入。  如可用，使用 **INCLUDE** 环境变量或 Visual Workbench 设置搜索文件。  
  
27. **字体名称必须是序号**  
  
     FONT 语句中的 *pointsize* 字段必须是整数，而不是字符串。  
  
28. **无效的快捷键**  
  
     **ACCELERATORS** 语句中的 `event` 字段不能被识别或者长度超过两个字符。  
  
29. **无效的快捷键类型（ASCII 或 VIRTKEY）**  
  
     **ACCELERATORS** 语句中的 `type` 字段必须包含 ASCII 或 VIRTKEY 值。  
  
30. **无效的控制字符**  
  
     在 **ACCELERATORS** 语句中的控制字符无效。  一个有效的控制字符由插入符号 \(^\) 后跟一个字母（并且只有一个）组成。  
  
31. **无效的控件类型**  
  
     **DIALOG** 语句中的每一个 CONTROL 语句必须为下列之一：CHECKBOX、COMBOBOX、CONTROL、CTEXT、DEFPUSHBUTTON、EDITTEXT、GROUPBOX、ICON、LISTBOX、LTEXT、PUSHBUTTON、RADIOBUTTON、RTEXT、SCROLLBAR。  确保这些 CONTROL 语句拼写正确。  
  
32. **无效的类型**  
  
     该资源类型不属于 WINDOWS.h 文件中定义的类型。  
  
33. **控件中需要文本字符串或序号**  
  
     在 **DIALOG** 语句中，**CONTROL** 语句的 *text* 字段必须是文本字符串或者是对控件类型的序号引用。  如果使用序号，确保对该控件有 `#define` 语句。  
  
34. **括号不匹配**  
  
     确保已经关闭 **DIALOG** 语句中每个左括号。  
  
35. **RCDATA 中的意外值**  
  
     **RCDATA** 语句中的 *raw\-data* 值必须是整数或字符串，各个值之间用逗号分隔。  确保在字符串前后没有遗漏逗号或引号。  
  
36. **未知的菜单子类型**  
  
     **MENU** 语句的 *item\-definition* 字段只能包含 **MENUITEM** 和 **POPUP** 语句。