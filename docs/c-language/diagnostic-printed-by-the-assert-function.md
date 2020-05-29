---
title: assert 函数输出的诊断
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234216"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>assert 函数输出的诊断

**ANSI 4.2** assert  函数输出的诊断和终止行为

如果表达式为 false (0)，则 assert  函数将输出诊断消息并调用 abort  例程。 诊断消息具有以下形式

> **Assertion failed**: <em>expression</em> **, file** <em>filename</em> **, line** *linenumber*

其中，filename 是源文件的名称，linenumber 是源文件中失败的断言的行号   。 如果表达式为 true（非零），则不执行任何操作  。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)
