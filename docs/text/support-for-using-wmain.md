---
title: 支持使用 wmain
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: 4af389c00f6065df631f891dadcb0b2f350f984d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491202"
---
# <a name="support-for-using-wmain"></a>支持使用 wmain

Visual C++支持定义**wmain**函数, 并将宽字符自变量传递给 Unicode 应用程序。 使用类似于`main`的格式将形参声明为**wmain**。 然后可以将宽字符自变量和宽字符环境指针（可选）传递给该程序。 wmain 的 `argv` 和 `envp` 参数为 `wchar_t*` 类型。 例如:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> MFC Unicode 应用程序`wWinMain`使用作为入口点。 在此示例中`CWinApp::m_lpCmdLine` , 是一个 Unicode 字符串。 请确保设置`wWinMainCRTStartup`了[/ENTRY](../build/reference/entry-entry-point-symbol.md)链接器选项。

如果程序使用 main 函数，则多字节字符环境由运行时库在程序启动时创建。 环境的宽字符副本仅在需要时创建（如调用 `_wgetenv` 或 `_wputenv` 函数时）。 第一次调用`_wputenv` `_wgetenv`时, 或首次调用时, 如果 MBCS 环境已存在, 则会创建相应的宽字符字符串环境。 然后由`_wenviron`全局变量指向该环境, 该变量是`_environ`全局变量的宽字符版本。 此时, 同时存在两个环境副本 (MBCS 和 Unicode), 在程序的整个生命周期内都由运行时系统维护。

同样，如果程序使用 wmain 函数，则在程序启动时创建宽字符环境并用 `_wenviron` 全局变量指向该环境。 MBCS (ASCII) 环境是在首次调用`_putenv`或`getenv` `_environ`时创建的, 由全局变量指向。

## <a name="see-also"></a>请参阅

[支持 Unicode](../text/support-for-unicode.md)<br/>
[Unicode 编程摘要](../text/unicode-programming-summary.md)<br/>
[WinMain 函数](/windows/win32/api/winbase/nf-winbase-winmain)
