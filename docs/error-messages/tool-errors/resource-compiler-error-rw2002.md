---
title: 资源编译器错误 RW2002 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2002
dev_langs:
- C++
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50d2993c4f8e7053867aa0757e90a0f7f1b1190c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112897"
---
# <a name="resource-compiler-error-rw2002"></a>资源编译器错误 RW2002

分析错误

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. **加速器类型所需 （ASCII 或 VIRTKEY）**

     `type` ACCELERATORS **语句中的** 字段中必须包含 ASCII 或 VIRTKEY 值。

1. **快捷键对应表中需要 BEGIN**

     **BEGIN** 关键字必须紧跟在 **ACCELERATORS** 关键字后面。

1. **在对话框中需要 BEGIN**

     **开始**关键字必须紧跟**对话框**关键字。

1. **在菜单中需要 BEGIN**

     **BEGIN** 关键字必须紧跟 **MENU** 关键字。

1. **RCData 中应具有 BEGIN**

     **BEGIN** 关键字必须紧跟在 **RCDATA** 关键字之后。

1. **字符串表中需要 BEGIN 关键字**

     **开始**关键字必须紧跟**STRINGTABLE**关键字。

1. **不能重新使用字符串常量**

     使用相同的值在两次**STRINGTABLE**语句。 请确保您没有混合出现重复的十进制和十六进制值。 在每个 ID **STRINGTABLE**必须是唯一的。 实现最大效率使用连续的 16 倍启动的常量。

1. **控制字符超出范围 [^ A-^ Z]**

     **ACCELERATORS** 语句中的控制字符无效。 插入符号 (**^**) 后面的字符必须介于 A 和 Z（包含 A 和 Z）。

9. **不允许空菜单**

     **最终**中定义任何菜单项之前，将显示关键字**菜单**语句。 资源编译器不允许使用空菜单。 请确保你没有任何左引号内**菜单**语句。

10. **在对话框中应具有 END**

     **最终**关键字必须出现在末尾**对话框**语句。 请确保没有剩下的上一个语句中的左引号。

11. **在菜单中应具有 END**

     **END** 关键字必须出现在 **MENU** 语句的末尾。 确保没有任何左引号或不匹配的 **BEGIN** 和 **END** 语句对。

12. **快捷键对应表中需要的逗号**

     资源编译器在 `event` ACCELERATORS *语句中的* 与 **idvalue** 字段之间需要逗号。

13. **预期的控件类名**

     `class`字段**控制**中的语句**对话框**语句必须是以下类型之一： 按钮、 组合框、 编辑、 列表框、 滚动条、 静态的或用户定义。 请确保类的拼写正确。

14. **预期字体名称**

     *DIALOG* 语句中的 FONT 选项的 **typeface** 字段必须为括在双引号内的 ASCII 字符字符串。 此字段指定字体名称。

15. **菜单项的预期的 ID 值**

     “菜单”  语句必须包含 *menuID* 字段，该字段指定用于标识菜单资源的名称或数字。

16. **需要的菜单字符串**

     每个 **MENUITEM** 和 **POPUP** 语句必须包含一个 *文本* 字段，它是一个括在双引号中的字符串，用于指定菜单项或弹出菜单的名称。 一个**菜单项分隔符**语句需要不带引号的字符串。

17. **应输入数字的命令值**

     资源编译器需要数值*idvalue*字段中**加速器**语句。 请确保你已使用`#define`常量，以指定的值和常量拼写正确。

18. **字符串表中的预期数值常量**

     在 `#define` 语句中定义的数值常量必须在后面紧跟 **STRINGTABLE** 语句中的 **BEGIN** 关键字。

19. **预期数值点大小**

     *DIALOG* 语句中的 FONT 选项的 **Pointsize** 字段必须为整数点大小值。

20. **预期数值对话框常量**

     一个**对话框中**语句要求的整数值*x、 y、 宽度*，并*高度*字段。 请确保这些值后包含**对话框**关键字，它们不负。

21. **应为 STRINGTABLE 中的字符串**

     *STRINGTABLE* 语句中的每一个 **stringid** 值后应有一个字符串。

22. **预期的字符串或常数加速器命令**

     资源编译器无法确定为加速器设置的项的种类。 `event` ACCELERATORS **语句中的** 字段可能无效。

23. **id 应为数字**

     应为一个数字`id`字段中的控制语句**对话框**语句。 请确保您有很多或`#define`语句的控件 id。

24. **对话框类中需要带引号的字符串**

     `class` DIALOG **语句中 CLASS 选项的** 字段必须为括在双引号内整数或字符串。

25. **对话框的标题中需要带引号的字符串**

     `captiontext` DIALOG **语句中 CAPTION 选项的** 字段必须为括在双引号内的 ASCII 字符字符串。

26. **找不到文件： filename**

     找不到资源编译器命令行中指定的文件。 检查以确定文件是否已被移动到另一个目录，以及是否正确键入文件名或路径。 使用搜索文件**INCLUDE**环境变量或 Visual Workbench 设置，如果可用。

27. **字体名称必须是序号**

     *Pointsize*字体语句中的字段必须是一个整数，而不是字符串。

28. **无效的加速器**

     `event` ACCELERATORS **语句中的** 字段无法识别或长度超过两个字符。

29. **无效的加速器类型 （ASCII 或 VIRTKEY）**

     `type` ACCELERATORS **语句中的** 字段中必须包含 ASCII 或 VIRTKEY 值。

30. **无效的控制字符**

     **ACCELERATORS** 语句中的控制字符无效。 有效的控制字符包含插入符号 (^) （仅限） 后跟一个字母。

31. **无效的控件类型**

     在每个控制语句**对话框**语句必须是以下值之一： 复选框、 组合框、 控件、 CTEXT、 DEFPUSHBUTTON、 EDITTEXT、 GROUPBOX、 图标、 列表框、 LTEXT、 PUSHBUTTON、 RADIOBUTTON、 RTEXT、 滚动条。 请确保这些控制语句拼写正确。

32. **无效的类型**

     资源类型未在 WINDOWS.h 文件中定义的类型。

33. **文本字符串或控件中的预期序号**

     *文本*字段**控件**中的语句**对话框**语句必须是文本字符串或对控件的类型引用的序号。 如果使用序号，请确保你有用于此控件的 `#define` 语句。

34. **括号不匹配**

     请确保已关闭每个左括号**对话框**语句。

35. **RCData 中的意外的值**

     *RCDATA* 语句中的 **原始数据** 值必须是整数或字符串，每个值用逗号分隔。 请确保未遗漏逗号或字符串周围的引号。

36. **未知的菜单的子类型**

     *项定义*字段**菜单**语句只能包含**MENUITEM**并**弹出**语句。