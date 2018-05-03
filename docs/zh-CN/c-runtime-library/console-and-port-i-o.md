---
title: 控制台和端口 I/O | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db5532b35e915f69927699ce9678d5bd5ffb5579
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="console-and-port-io"></a>控制台和端口 I/O

这些例程在控制台或指定端口上读写。 控制台 I/O 例程与流 I/O 或低级 I/O 库例程不兼容。 在执行 I/O 前，不必打开或关闭控制台或端口，因此此类别中没有打开或关闭例程。 在 Windows 操作系统中，来自这些函数的输出始终将定向到控制台，且无法重定向。

## <a name="console-and-port-io-routines"></a>控制台和端口 I/O 例程

|例程所返回的值|使用|
|-------------|---------|
|[_cgets、_cgetws](../c-runtime-library/cgets-cgetws.md)、[_cgets_s、_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|从控制台读取字符串|
|[_cprintf、_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)、[_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|将格式化的数据写入控制台|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|把字符串写入控制台|
|[_cscanf、_cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)、[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|从控制台读取格式化的数据|
|[_getch、_getwch](../c-runtime-library/reference/getch-getwch.md)|从控制台读取字符|
|[_getche、_getwche](../c-runtime-library/reference/getch-getwch.md)|从控制台读取字符并回显|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|从指定的 I/O 端口读取一个字节|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|从指定 I/O 端口读取双字|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|读取指定 I/O 端口 2 字节的字|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|在控制台检查键击；在尝试从控制台读取前使用|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|将字节写入指定 I/O 端口|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|将双字写入指定 I/O 端口|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|将字写入指定的 I/O 端口|
|[_putch、_putwch](../c-runtime-library/reference/putch-putwch.md)|将字符写入控制台|
|[_ungetch、_ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|“取消获取”从控制台读取的最后一个字符，以便让它成为下一个被读取的字符|

## <a name="see-also"></a>请参阅

[输入和输出](../c-runtime-library/input-and-output.md)<br/>
 [按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>