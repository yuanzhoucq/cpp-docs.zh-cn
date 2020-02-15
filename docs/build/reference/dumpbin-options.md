---
title: DUMPBIN 选项
description: Microsoft DUMPBIN 实用程序命令行选项的参考指南。
ms.date: 02/09/2020
f1_keywords:
- dumpbin
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 98a4fd221d66b93f945667deadaba3180f8d3e66
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257723"
---
# <a name="dumpbin-options"></a>DUMPBIN 选项

选项包括一个*选项说明符*，该说明符为短划线（`-`）或正斜杠（`/`），后跟选项的名称。 不能缩写选项名称。 某些选项采用冒号（`:`）之后指定的参数。 选项规范内不允许有空格或制表符。 在命令行上使用一个或多个空格或制表符分隔选项规范。 选项名及其关键字或文件名参数不区分大小写。 大多数选项都适用于所有二进制文件，但一些选项仅适用于某些类型的文件。 默认情况下，DUMPBIN 会将信息发送到标准输出。 使用[/out](out-dumpbin.md)选项将输出发送到文件。

## <a name="options-list"></a>选项列表

DUMPBIN 具有以下选项：

- [/ALL](all.md)

- [/ARCHIVEMEMBERS](archivemembers.md)

- [/CLRHEADER](clrheader.md)

- [/DEPENDENTS](dependents.md)

- [/DIRECTIVES](directives.md)

- [/DISASM\[： {BYTES\|NOBYTES}\]](disasm.md)

- [/ERRORREPORT： {NONE |PROMPT |QUEUE |发送}](errorreport-dumpbin-exe.md) （不推荐使用）

- [/EXPORTS](dash-exports.md)

- [/FPO](fpo.md)

- [/HEADERS](headers.md)

- [/IMPORTS\[： filename\]](imports-dumpbin.md)

- [/LINENUMBERS](linenumbers.md)

- [/LINKERMEMBER\[： {1 | 2}\]](linkermember.md)

- [/LOADCONFIG](loadconfig.md)

- [/NOPDB](nopdb.md)

- [/OUT： filename](out-dumpbin.md)

- [/PDATA](pdata.md)

- [/PDBPATH\[： VERBOSE\]](pdbpath.md)

- [/RANGEE： vaMin\[，vaMax\]](range.md)

- [/RAWDATA\[： {NONE\|1\|2\|4\|8}\[，#\]\]](rawdata.md)

- [/RELOCATIONS](relocations.md)

- [/SECTION：名称](section-dumpbin.md)

- [/SUMMARY](summary.md)

- [/SYMBOLS](symbols.md)

- [/TLS](tls.md)

若要列出命令行上的 DUMPBIN 支持的选项，请使用 **/？** 。

## <a name="see-also"></a>另请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)\
[DUMPBIN 命令行](dumpbin-command-line.md)\
[DUMPBIN 引用](dumpbin-reference.md)
