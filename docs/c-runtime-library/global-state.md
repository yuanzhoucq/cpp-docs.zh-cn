---
title: CRT 中的全球状态
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 487418da104b2edbc45b5d3a664e4385394ada31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377598"
---
# <a name="global-state-in-the-crt"></a>CRT 中的全球状态

通用 C 运行时 （UCRT） 中的某些函数使用全局状态。 例如，`setlocale()`为整个程序设置区域设置，这会影响数字分隔符、文本代码页等。

UCRT 的全局状态不会在应用程序和操作系统之间共享。 例如，如果应用程序调用`setlocale()`，则不会影响使用 C 运行时的任何操作系统组件的区域设置，反之亦然。

## <a name="os-specific-versions-of-crt-functions"></a>特定于操作系统的 CRT 功能版本

在 UCRT 中，与全局状态交互的函数具有"双"函数，以`_o_`预缀于 。 例如：

    `setlocale()` affects global state specific to the app.
    `_o_setlocale()` affects global state shared by all OS components, but not apps.

这些"孪生"函数的唯一区别是，当他们读取/写入全局 CRT 状态时，特定于操作系统的版本（即以`_o_`开头的版本）使用全局状态的 OS 副本，而不是应用的全局状态副本。

这些函数的特定于操作系统的版本在 中`ucrt.osmode.lib`。 例如，特定于操作系统的版本`setlocale()`是`_o_setlocale()`

有两种方法可以将组件的 CRT 状态与应用的 CRT 状态隔离开来：

- 使用编译器选项 /MT（发布）或 MTd（调试）静态链接组件。 有关详细信息，请参阅[/MD、/MT、/LD](https://docs.microsoft.com/cpp/build/reference/md-mt-ld-use-run-time-library?view=vs-2019)。 请注意，静态链接可以大大增加二进制大小。
- 从 Windows 10 20H2 开始，通过动态链接到 CRT 但调用 OS 模式导出（以_o_开头的函数）来获取 CRT 状态隔离。 要调用 OS 模式导出，请像以前一样静态链接，但使用链接器选项`/NODEFAULTLIB:libucrt.lib`（发布）或`/NODEFAULTLIB:libucrtd.lib`（调试）忽略静态 UCRT，请参阅[/NODEFAULTLIB（忽略库）](https://docs.microsoft.com/cpp/build/reference/nodefaultlib-ignore-libraries?view=vs-2019)了解详细信息。 并添加到`ucrt.osmode.lib`链接器输入。

> [!Note]
> 在源代码中，写入`setlocale()`而不是`_o_setlocale()`。 当您链接到 时`ucrt.osmode.lib`，链接器将自动替换特定于操作系统的函数版本。 也就是说，`setlocale()`将替换为`_o_setlocale()`。

链接将`ucrt.osmode.lib`禁用仅在应用模式下可用的某些 UCRT 调用。 尝试调用这些将导致链接错误。

## <a name="global-state-affected-by-appos-separation"></a>受应用/操作系统分离影响的全局状态

受应用和操作系统状态分离影响的全局状态包括：

- [区域设置数据](locale.md)
- 信号处理程序由[信号](reference/signal.md)设置
- 终止设置的[终止](reference/set-terminate-crt.md)例程
- [厄诺和_doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- [兰特](reference/rand.md)和[srand](reference/srand.md)使用的随机数生成状态
- 返回用户不需要释放的缓冲区的功能[：strtok、wcstok、_mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam、_wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime、_wasctime](reference/asctime-wasctime.md) [gmtime、_gmtime32、_gmtime64_fcvt_ecvt](reference/gmtime-gmtime32-gmtime64.md)[_fcvt](reference/fcvt.md)[_ecvt](reference/ecvt.md)[串错误、_strerror、_wcserror、__wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- [_putch使用的缓冲区，_putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md)和[_set_new_mode](reference/set-new-mode.md)
- [fmode]（text-and-binary-mode-file-i-o.md）
- [时区信息](time-management.md)

## <a name="see-also"></a>另请参阅

[C 运行时库引用](c-run-time-library-reference.md)