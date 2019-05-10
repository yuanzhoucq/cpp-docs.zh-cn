---
title: 国际化策略
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
ms.openlocfilehash: f8c5cec680072ffa34b1ee0bef9e09231de5f1ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410624"
---
# <a name="internationalization-strategies"></a>国际化策略

具体取决于您的目标操作系统和市场，有几个国际化策略：

- 你的应用程序使用 Unicode。

   使用特定于 Unicode 的功能和所有字符宽度都为 16 位 （尽管出于特殊目的，可以在程序的某些部分中使用 ANSI 字符）。 C 运行时库提供用于仅限 Unicode 的编程函数、 宏和数据类型。 MFC 是完全支持 Unicode 的。

- 应用程序使用 MBCS，并可以在任何 Win32 平台上运行。

   使用特定于 MBCS 的功能。 字符串可以包含单字节字符、 双字节字符，或两者。 C 运行时库提供用于仅使用 MBCS 编程函数、 宏和数据类型。 MFC 是完全启用 MBCS 的。

- 为应用程序的源代码编写的完整可移植性 — 通过使用符号重新编译`_UNICODE`或符号`_MBCS`定义，您可以生成使用的版本。 有关详细信息，请参阅[tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。

   使用完全可移植的 C 运行时函数、 宏和数据类型。 MFC 的灵活性支持任何这些策略。

这些主题的其余部分集中精力编写完全可移植代码，可以生成为 Unicode 或 MBCS。

## <a name="see-also"></a>请参阅

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[区域设置和代码页](../text/locales-and-code-pages.md)
