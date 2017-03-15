---
title: "Visual C++ 中的 MBCS 支持 | Microsoft Docs"
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
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "亚洲语言 [C++]"
  - "字符集 [C++], 多字节"
  - "中文字符 [C++]"
  - "代码编辑器 [C++], MBCS 支持"
  - "调试器 [C++], MBCS 支持"
  - "双字节字符集 [C++]"
  - "IME [C++]"
  - "IME [C++], MBCS"
  - "输入法编辑器 [C++]"
  - "输入法编辑器 [C++], MBCS"
  - "日语字符 [C++]"
  - "日文汉字字符支持 [C++]"
  - "MBCS [C++], 启用"
  - "多字节字符 [C++]"
  - "NMAKE 程序, MBCS 支持"
  - "资源编辑器 [C++], MBCS 支持"
  - "工具 [C++], MBCS 支持"
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Visual C++ 中的 MBCS 支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在支持 MBCS 的 Windows 2000 或 Windows XP 操作系统版本上运行时，除内存窗口外，Visual C\+\+ 开发系统（包括集成的源代码编辑器、调试器和命令行工具）支持 MBCS。  
  
 内存窗口不把字节数据解释为 MBCS，字符，即使它能够把它们解释为 ANSI 或 Unicode 字符。  ANSI 字符的大小始终为 1 个字节，Unicode 字符的大小为 2 字节。  MBCS，字符可以是 1 或 2 字节在大小及其的解释取决于代码页仍在使用中。  因此，内存窗口很难可靠地显示 MBCS 字符。  内存窗口无法知道哪些字节是字符的开头。  开发人员可以在内存窗口中查看字节值，然后在表中查找该值，以确定字符表示形式。  开发人员根据源代码可以知道字符串的开始地址，因此这是可行的。  
  
 Visual C\+\+ 在任何适合条件下都接受双字节字符。  这包括对话框中的路径名和文件名，以及 Visual C\+\+ 资源编辑器中的文本项（例如，对话框编辑器中的静态文本和图标编辑器中的静态文本项）。  此外，预处理器识别一些双字节指令（例如，`#include` 语句中的文件名），作为 **code\_seg** 和 **data\_seg** 伪指令的参数。  在源代码编辑器中接受注释和字符串中的双字节字符，但在 C\/C\+\+ 语言元素（如变量名）中不接受。  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> 对输入法编辑器 \(IME\) 的支持  
 为使用 MBCS 的东亚市场（如日本）编写的应用程序通常支持 Windows IME 输入单字节和双字节字符。  Visual C\+\+ 开发环境完全支持 IME。  有关更多信息，请参见 [IME 示例：演示如何控制 IME 模式和实现 IME 级别 3](http://msdn.microsoft.com/zh-cn/87ebdf65-cef0-451d-a6fc-d5fb64178b14)。  
  
 日文键盘不直接支持日文汉字字符。  IME 将用其他日文字母表（罗马字、片假名或平假名）输入的语音字符串转换为其可能的日文汉字表示形式。  如果存在多义性，则可以从几个选项中选择。  选择日文汉字字符后，IME 将两条 `WM_CHAR` 消息传递给控制应用程序。  
  
 IME 由 Alt\+\` 组合键激活，显示为一组按钮（一个指示符）和一个转换窗口。  应用程序将窗口定位在文本插入点。  应用程序必须通过重新定位转换窗口使其符合目标窗口的新位置或大小来处理 `WM_MOVE` 和 `WM_SIZE` 消息。  
  
 如果希望应用程序的用户具有输入日文汉字字符的能力，应用程序必须能够处理 Windows IME 消息。  有关 IME 编程的更多信息，请参见[输入法编辑器](https://msdn.microsoft.com/en-us/library/ms776145.aspx)。  
  
## Visual C\+\+ 调试器  
 Visual C\+\+ 调试器提供在 IME 消息上设置断点的能力。  另外，“内存”窗口可以显示双字节字符。  
  
## 命令行工具  
 Visual C\+\+ 命令行工具（包括编译器、NMAKE 和资源编译器 \(RC.EXE\)）支持 MBCS。  编译应用程序的资源时，可以使用资源编译器的 \/c 选项以更改默认的代码页。  
  
 若要在源代码编译时更改默认的区域设置，请使用 [\#pragma setlocale](../preprocessor/setlocale.md)。  
  
## 图形工具  
 基于 Windows 的 Visual C\+\+ 工具（如 Spy\+\+ 和资源编辑工具）完全支持 IME 字符串。  
  
## 请参阅  
 [支持多字节字符集 \(MBCS\)](../text/support-for-multibyte-character-sets-mbcss.md)   
 [MBCS 编程提示](../text/mbcs-programming-tips.md)