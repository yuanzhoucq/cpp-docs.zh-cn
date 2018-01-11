---
title: "Visual c + + 中的 MBCS 支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdc00509d8660d8111ff1b966b7a881a153cb6c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支持
当在 MBCS 支持的版本的 Windows 2000 或 Windows XP 操作系统上运行，Visual c + + 开发系统 （包括集成的源代码编辑器、 调试器和命令行工具） 是 MBCS 支持，除了内存窗口。  
  
 内存窗口不将数据的字节解释为 MBCS 字符，即使它可以将这些字节解释为 ANSI 或 Unicode 字符。 ANSI 字符的大小始终为 1 个字节，而 Unicode 字符的大小为 2 个字节。 在 MBCS 中，字符的大小可以是 1 个或 2 个字节，其解释取决于正在使用的代码页。 因此，内存窗口很难可靠地显示 MBCS 字符。 内存窗口无法知道哪些字节是字符的开头。 开发人员可以在内存窗口中查看的字节值，并查找表来确定字符表示形式中的值。 这可能是字符串的因为开发人员知道基于的源代码的起始地址。  
  
 Visual c + + 接受双字节字符，只要它适合若要这样做。 这包括选择了路径名称和文件名称为中的对话框和 Visual c + + 资源编辑器 （例如，在对话框编辑器中的静态文本） 和图标编辑器中的静态文本项中的文本项。 此外，预处理器可识别某些双字节指令 — 例如，文件名中`#include`语句，并为变量**code_seg**和**data_seg**杂注。 在源代码编辑器中，注释和字符串文本中的双字节字符接受，尽管不是在 C/c + + 语言元素 （如变量名）。  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>支持用于输入法编辑器 (IME)  
 编写通常使用 MBCS （例如，日语） 的东亚市场支持 Windows IME 用于输入这两个单字节和双字节字符的应用程序。 Visual c + + 开发环境包含完整 IME 支持。 有关详细信息，请参阅[IME 示例： 演示如何控制 IME 模式和实现 IME 级别 3](http://msdn.microsoft.com/en-us/87ebdf65-cef0-451d-a6fc-d5fb64178b14)。  
  
 日语键盘不直接支持日文汉字字符。 IME 将转换的语音的字符串，其中一个其他日文字母表 （罗马字、 片假名或平假名） 中输入到其可能日文汉字表示形式。 如果存在多义性，可以从多种可选方案中进行选择。 当你选择了日文的汉字字符时，IME 将传递两个`WM_CHAR`到控制应用程序的消息。  
  
 IME，激活的 ALT +\`密钥组合，显示为一组按钮 （一个指示符） 和一个转换窗口。 应用程序将文本插入点处窗口定位。 应用程序必须处理`WM_MOVE`和`WM_SIZE`通过重新定位转换窗口的消息，以符合新位置或目标窗口的大小。  
  
 如果你希望用户的应用程序拥有输入日文汉字字符的能力，应用程序必须处理 Windows IME 消息。 有关 IME 编程的详细信息，请参阅[输入法编辑器](https://msdn.microsoft.com/en-us/library/ms776145.aspx)。  
  
## <a name="visual-c-debugger"></a>Visual c + + 调试器  
 Visual c + + 调试器能够在 IME 消息上设置断点。 此外，内存窗口可以显示双字节字符。  
  
## <a name="command-line-tools"></a>命令行工具  
 Visual c + + 命令行工具，包括编译器、 NMAKE 和资源编译器 (RC。EXE)，MBCS 启用了。 资源编译器 /c 选项可用于更改编译应用程序的资源时的默认代码页。  
  
 若要在源代码编译时更改默认区域设置，请使用[#pragma setlocale](../preprocessor/setlocale.md)。  
  
## <a name="graphical-tools"></a>图形工具  
 Visual c + + Windows 基于等工具，Spy + + 和编辑工具，资源完全支持 IME 字符串。  
  
## <a name="see-also"></a>请参阅  
 [多字节字符集 (Mbcs) 的支持](../text/support-for-multibyte-character-sets-mbcss.md)   
 [MBCS 编程提示](../text/mbcs-programming-tips.md)