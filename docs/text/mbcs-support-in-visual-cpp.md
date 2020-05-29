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
ms.openlocfilehash: 404fcee5e48d8db28e56a005f24f8cac5892240e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375784"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支持

在启用 MBCS 的 Windows 版本上运行时，Visual C++开发系统（包括集成源代码编辑器、调试器和命令行工具）将启用 MBCS，内存窗口除外。

内存窗口不将数据的字节解释为 MBCS 字符，即使它可以将这些字节解释为 ANSI 或 Unicode 字符。 ANSI 字符的大小始终为 1 个字节，而 Unicode 字符的大小为 2 个字节。 在 MBCS 中，字符的大小可以是 1 个或 2 个字节，其解释取决于正在使用的代码页。 因此，内存窗口很难可靠地显示 MBCS 字符。 内存窗口无法知道哪些字节是字符的开头。 开发人员可以在内存窗口中查看字节值，并在表中查找值以确定字符表示形式。 这是可能的，因为开发人员知道基于源代码的字符串的起始地址。

可视化C++在适当的情况下接受双字节字符。 这包括对话框中的路径名称和文件名以及 Visual C++ 资源编辑器中的文本条目（例如，对话框编辑器中的静态文本和图标编辑器中的静态文本条目）。 此外，预处理器可识别一些双字节指令，例如，语句中`#include`的文件名，以及 作为 和`code_seg``data_seg`实例的参数。 在源代码编辑器中，接受注释和字符串文本中的双字节字符，尽管 C/C++语言元素（如变量名称）中不接受。

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>支持输入方法编辑器 （IME）

为使用 MBCS（例如日本）的东亚市场编写的应用程序通常支持 Windows IME 输入单字节和双字节字符。 可视化C++开发环境包含对 IME 的完全支持。

日语键盘不直接支持汉字字符。 IME 将用其他日语字母（罗马吉、卡塔卡纳或平假名）输入的拼音字符串转换为其可能的汉字表示形式。 如果存在歧义，可以从多个备选方案中选择。 选择预期的汉字字符后，IME 会向控制应用程序传递两`WM_CHAR`条消息。

由 ALT+\`键组合激活的 IME 显示为一组按钮（指示器）和转换窗口。 应用程序将窗口定位在文本插入点。 应用程序必须通过重新定位转换`WM_MOVE`窗口`WM_SIZE`来处理和消息，以符合目标窗口的新位置或大小。

如果希望应用程序的用户能够输入汉字字符，则应用程序必须处理 Windows IME 消息。 有关 IME 编程的详细信息，请参阅[输入方法管理器](/windows/win32/intl/input-method-manager)。

## <a name="visual-c-debugger"></a>可视化C++调试器

可视化C++调试器提供在 IME 消息上设置断点的能力。 此外，内存窗口可以显示双字节字符。

## <a name="command-line-tools"></a>命令行工具

VisualC++命令行工具，包括编译器、NMAKE 和资源编译器 （RC）。EXE），已启用 MBCS。 在编译应用程序的资源时，可以使用资源编译器的 /c 选项更改默认代码页。

要更改源代码编译时间的默认区域设置，请使用[#pragma设置区域设置](../preprocessor/setlocale.md)。

## <a name="graphical-tools"></a>图形工具

基于 Windows 的可视化C++工具（如 Spy+ 和资源编辑工具）完全支持 IME 字符串。

## <a name="see-also"></a>另请参阅

[支持多字节字符集 （MBCS）](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS 编程提示](../text/mbcs-programming-tips.md)
