---
title: Visual C++ 中的 MBCS 支持
ms.date: 11/04/2016
f1_keywords:
- _mbcs
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
ms.openlocfilehash: b292bb12888ce0c08f96d3c46e27297f61bc428d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750489"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支持

MBCS 启用的 Windows 版本上运行，Visual c + + 开发系统 （包括集成的源代码代码编辑器、 调试器和命令行工具） 时，MBCS 启用的除了内存窗口。

内存窗口不将数据的字节解释为 MBCS 字符，即使它可以将这些字节解释为 ANSI 或 Unicode 字符。 ANSI 字符的大小始终为 1 个字节，而 Unicode 字符的大小为 2 个字节。 在 MBCS 中，字符的大小可以是 1 个或 2 个字节，其解释取决于正在使用的代码页。 因此，内存窗口很难可靠地显示 MBCS 字符。 内存窗口无法知道哪些字节是字符的开头。 开发人员可以查看内存窗口中的字节值，并查找表来确定字符表示形式中的值。 这可能是字符串的因为开发人员知道基于源代码的起始地址。

Visual c + + 接受双字节字符，只要适合执行此操作。 这包括对话框和 Visual c + + 资源编辑器 （例如，在对话框编辑器中的静态文本） 和图标编辑器中的静态文本项中的文本项中的路径名和文件名。 此外，预处理器可识别某些双字节指令，例如，文件中的名称`#include`语句，并作为参数`code_seg`和`data_seg`杂注。 在源代码编辑器中，双字节字符的注释和字符串文本中接受，尽管不在 C/c + + 语言元素 （如变量的名称）。

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> 支持的输入法编辑器 (IME)

编写用于输入这两个单字节和双字节字符的东亚语言市场的正常使用 MBCS （例如，日本） 支持 Windows IME 的应用程序。 Visual c + + 开发环境包含完全 IME 支持。

日语键盘不直接支持日文汉字字符。 IME 转换拼音的字符串，其可能的日文汉字表示形式输入其他日文字母表 （罗马字、 片假名或平假名） 之一。 如果存在多义性，可以从多种可选方案中进行选择。 当选择了日文的汉字字符时，IME 传递两个`WM_CHAR`控制应用程序的消息。

IME，激活的 ALT +\`组合键，将显示为一系列按钮 （指标） 和转换窗口。 应用程序定位文本插入点处的窗口。 应用程序必须处理`WM_MOVE`和`WM_SIZE`通过重新定位转换窗口的消息，以符合新位置或目标窗口的大小。

如果你希望用户的应用程序输入日文汉字字符的功能，该应用程序必须处理 Windows IME 消息。 有关输入法进行编程的详细信息，请参阅[输入法管理器](/windows/desktop/intl/input-method-manager)。

## <a name="visual-c-debugger"></a>Visual c + + 调试器

Visual c + + 调试器提供 IME 消息上设置断点的能力。 此外，内存窗口可以显示双字节字符。

## <a name="command-line-tools"></a>命令行工具

Visual c + + 命令行工具，包括编译器、 NMAKE，以及资源编译器 (RC。Exe 文件），MBCS 启用了。 资源编译器 /c 选项，可用于更改编译应用程序的资源时的默认代码页。

若要在源的代码编译时更改默认区域设置，请使用[#pragma setlocale](../preprocessor/setlocale.md)。

## <a name="graphical-tools"></a>图形工具

基于 Visual c + + Windows 的工具，如 Spy + + 和编辑工具，该资源完全支持 IME 的字符串。

## <a name="see-also"></a>请参阅

[支持多字节字符集 (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS 编程提示](../text/mbcs-programming-tips.md)
