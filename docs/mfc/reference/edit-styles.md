---
title: "编辑样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ES_READONLY"
  - "ES_WANTRETURN"
  - "ES_UPPERCASE"
  - "ES_NUMBER"
  - "ES_AUTOHSCROLL"
  - "ES_LOWERCASE"
  - "ES_RIGHT"
  - "ES_MULTILINE"
  - "ES_PASSWORD"
  - "ES_NOHIDESEL"
  - "ES_OEMCONVERT"
  - "ES_LEFT"
  - "ES_CENTER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "编辑样式 [MFC]"
  - "ES_AUTOHSCROLL 常量"
  - "ES_AUTOVSCROLL 常量"
  - "ES_CENTER 常量"
  - "ES_LEFT 常量"
  - "ES_LOWERCASE 常量"
  - "ES_MULTILINE 常量"
  - "ES_NOHIDESEL 常量"
  - "ES_NUMBER 常量"
  - "ES_OEMCONVERT 常量"
  - "ES_PASSWORD 常量"
  - "ES_READONLY 常量"
  - "ES_RIGHT 常量"
  - "ES_UPPERCASE 常量"
  - "ES_WANTRETURN 常量"
ms.assetid: e6291dd6-f2cb-4ce2-ac31-32272526625c
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 编辑样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **ES\_AUTOHSCROLL** 自动滚动文本右侧由 10 字符，它在用户键入字符行尾。  当用户按 Enter 键时，控件回所有滚动文本位置 0。  
  
-   当用户在最后一行中按 Enter，**ES\_AUTOVSCROLL** 自动滚动文本的页。  
  
-   **ES\_CENTER** 中心在单行或多行编辑控件的文本。  
  
-   **ES\_LEFT** 左对齐在单行或多行编辑控件的文本。  
  
-   在键入编辑控件，**ES\_LOWERCASE** 所有字符转换为小写。  
  
-   **ES\_MULTILINE** 指定一个多行编辑控件。\(默认为单行。\)如果 **ES\_AUTOVSCROLL** 指定样式一样，编辑控件显示很多行作为可能和垂直滚动，则用户按 Enter 键。  如果不为 **ES\_AUTOVSCROLL**，编辑控件显示很多行作为可能和提示音，如果按下 Enter，在没有其他行不能显示时。  如果 **ES\_AUTOHSCROLL** 指定样式，多行编辑控件水平自动滚动，则插入符号访问用于控件的右边缘时。  若要开始新行，用户必须按 Enter。  如果不为 **ES\_AUTOHSCROLL**，则该控件自动包装 Word 到下一行的开头，如果必要；，如果按下 Enter，新的行来启动。  窗口大小由换行的位置。  如果窗口范围更改，换行位置更改，而文本将重新显示。  多行编辑控件可以有滚动条。  带有滚动条中的 Edit 控件处理自己的滚动条消息。  不使用滚动条的滚动控件编辑 \(如上所述\) 并处理父窗口发送的所有滚动信息。  
  
-   **ES\_NOHIDESEL** 的，编辑控件隐藏选定，则控件失去输入点时并反转选项，在控件接收输入焦点时。  指定 **ES\_NOHIDESEL** 默认删除该操作。  
  
-   **ES\_NUMBER** 只允许数值输入到编辑控件。  
  
-   在编辑控件中输入的文本将 ANSI 字符集转换为 OEM**ES\_OEMCONVERT** 然后回到 ANSI 字符集。  当应用程序调用 `AnsiToOem` Windows 函数转换在编辑控件中的 ANSI 字符串为 OEM 字符时，这确保适当的字符转换。  此样式。包含文件名的编辑控件都最为有用。  
  
-   **ES\_PASSWORD** 显示所有字符，星号 \(\#\#\#\*\)，将在编辑控件中键入内容。  应用程序可使用 `SetPasswordChar` 成员函数来更改显示的字符。  
  
-   **ES\_READONLY** 可以防止用户输入或编辑用编辑控件的文本。  
  
-   **ES\_RIGHT** 右对齐在单行或多行编辑控件的文本。  
  
-   在键入编辑控件，**ES\_UPPERCASE** 所有字符转换为大写。  
  
-   **ES\_WANTRETURN** 指定插入一个回车，则用户按 Enter 键时，在对话框输入文本时的多行编辑控件。  若无此样式，按 Enter 键对话框按默认按钮具有相同的效果。  此样式没有在单行编辑控件的效果。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CEdit::Create](../Topic/CEdit::Create.md)   
 [Edit Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb775464)