---
title: Visual C++ 中的 MBCS 支持
ms.date: 11/04/2016
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
ms.openlocfilehash: b5f2b6dd56d3a755ee73058c024152e12157a6bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501950"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支持

在启用了 MBCS 的 Windows 版本上运行时, 可视C++开发系统 (包括集成源代码编辑器、调试器和命令行工具) 将启用 MBCS, 但内存窗口除外。

内存窗口不将数据的字节解释为 MBCS 字符，即使它可以将这些字节解释为 ANSI 或 Unicode 字符。 ANSI 字符的大小始终为 1 个字节，而 Unicode 字符的大小为 2 个字节。 在 MBCS 中，字符的大小可以是 1 个或 2 个字节，其解释取决于正在使用的代码页。 因此，内存窗口很难可靠地显示 MBCS 字符。 内存窗口无法知道哪些字节是字符的开头。 开发人员可以在 "内存" 窗口中查看字节值, 并在表中查找值以确定字符表示形式。 这是可能的, 因为开发人员知道基于源代码的字符串的起始地址。

视觉C++对象在适当的位置接受双字节字符。 这包括对话框中的路径名称和文件名以及可视化C++资源编辑器中的文本项 (例如, 对话框编辑器中的静态文本和图标编辑器中的静态文本项)。 此外, 预处理器还识别一些双字节指令 (例如, 语句中`#include`的文件名), 并识别为和`data_seg`杂注`code_seg`的参数。 在源代码编辑器中, 将接受注释和字符串文本中的双字节字符, 但不能在 C/C++ language 元素 (例如变量名称) 中用到。

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>支持输入法编辑器 (IME)

为使用 MBCS (例如日本) 的东亚市场编写的应用程序通常支持用于输入单字节和双字节字符的 Windows IME。 可视化C++开发环境包含对 IME 的完全支持。

日语键盘不直接支持日文汉字字符。 IME 将输入的拼音字符串转换为另一种日本字母表 (罗马字、片假名或平假名)。 如果存在多义性, 则可以从几个替代项中进行选择。 选择了预期的日文汉字字符后, IME 将两`WM_CHAR`条消息传递给控制应用程序。

IME 由 ALT +\`组合键激活, 作为一组按钮 (指示器) 和转换窗口显示。 应用程序将窗口置于文本插入点处。 应用程序必须通过`WM_MOVE`重`WM_SIZE`定位转换窗口以符合目标窗口的新位置或大小来处理和消息。

如果希望应用程序的用户能够输入日文汉字字符, 则应用程序必须处理 Windows IME 消息。 有关 IME 编程的详细信息, 请参阅[输入法管理器](/windows/win32/intl/input-method-manager)。

## <a name="visual-c-debugger"></a>可视化C++调试器

可视化C++调试器提供了在 IME 消息上设置断点的能力。 此外, "内存" 窗口还可以显示双字节字符。

## <a name="command-line-tools"></a>命令行工具

可视化C++命令行工具, 包括编译器、NMAKE 和资源编译器 (RC)。EXE), 启用 MBCS。 在编译应用程序的资源时, 可以使用资源编译器的/c 选项来更改默认的代码页。

若要更改源代码编译时的默认区域设置, 请使用[#pragma setlocale](../preprocessor/setlocale.md)。

## <a name="graphical-tools"></a>图形工具

基于 Visual C++ Windows 的工具 (如 Spy + + 和资源编辑工具) 完全支持 IME 字符串。

## <a name="see-also"></a>请参阅

[支持多字节字符集 (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS 编程提示](../text/mbcs-programming-tips.md)
