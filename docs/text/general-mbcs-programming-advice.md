---
title: 常规 MBCS 编程建议
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 887387220105614eb3257f008ec601a6fc0adc18
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491189"
---
# <a name="general-mbcs-programming-advice"></a>常规 MBCS 编程建议

使用以下提示:

- 出于灵活性, 请尽可能使用运行时宏 ( `_tcschr`如`_tcscpy`和)。 有关详细信息, 请参阅[tchar 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。

- 使用 C 运行时`_getmbcp`函数获取有关当前代码页的信息。

- 不要重复使用字符串资源。 根据目标语言, 给定的字符串在翻译时可能具有不同的含义。 例如, 应用程序主菜单上的 "文件" 可能以不同于对话框中的字符串 "File" 进行转换。 如果需要使用具有相同名称的多个字符串, 请使用不同的字符串 Id。

- 你可能想要了解你的应用程序是否在支持 MBCS 的操作系统上运行。 为此, 请在程序启动时设置一个标志;不要依赖于 API 调用。

- 设计对话框时, 允许在静态文本控件末尾留出约 30% 的额外空间用于 MBCS 转换。

- 为应用程序选择字体时要小心, 因为某些字体在所有系统上都不可用。

- 选择对话框的字体时, 请使用[Ms Shell Dlg](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) , 而不是 Ms Sans Serif 或 Helvetica。 创建对话框之前, 系统会将 MS Shell Dlg 替换为正确的字体。 使用 MS Shell Dlg 可确保操作系统所做的任何更改都能自动使用。 (MFC 将 MS Shell Dlg 替换为 Windows 95、Windows 98 和 Windows NT 4 上的 DEFAULT_GUI_FONT 或系统字体, 因为这些系统不会正确处理 MS Shell Dlg。)

- 设计应用程序时, 请确定哪些字符串可本地化。 如果有疑问, 假设将本地化任何给定的字符串。 因此, 请不要混合使用无法本地化的字符串。

## <a name="see-also"></a>请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)<br/>
[递增和递减指针](../text/incrementing-and-decrementing-pointers.md)
