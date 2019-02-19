---
title: 系统函数
ms.date: 11/04/2016
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
ms.openlocfilehash: e37de4e084de6727cf2858117945fd162f6b0d63
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151216"
---
# <a name="system-function"></a>系统函数

**ANSI 4.10.4.5** system 函数执行字符串的内容和模式

system 函数执行内部操作系统命令，或者 C 程序中（而不是命令行中）的 .EXE、.COM（Windows NT 中的 .CMD）或 .BAT 文件。

系统函数查找命令解释器，它通常是 Windows NT 操作系统中的 CMD.EXE 或 Windows 中的 COMMAND.COM。 系统函数随后将自变量字符串传递到命令解释器。

有关详细信息，请参阅 [system、_wsystem](../c-runtime-library/reference/system-wsystem.md)。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)
