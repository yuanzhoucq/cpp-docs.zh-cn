---
title: 扩展通配符自变量
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: 2224d01eeb3ec54a9c0ff895dfa45574135f7c0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443415"
---
# <a name="expanding-wildcard-arguments"></a>扩展通配符自变量

**Microsoft 专用**

在运行 C 程序时，你可以使用两个通配符（问号 (?) 和星号 (*)）之一以便在命令行上指定文件名和路径参数。

默认情况下，命令行参数中不展开通配符。 你可以通过链接 setargv.obj 或 wsetargv.obj 文件将普通参数向量 `argv` 加载例程替换为不展开通配符的版本。 如果程序使用 `main` 函数，请与 setargv.obj 链接。如果程序使用 `wmain` 函数，请与 wsetargv.obj 链接。它们具有等效的行为。

若要与 setargv.obj 或 wsetargv.obj 链接，请使用 **/link** 选项。 例如:

cl example.c /link setargv.obj

按照与操作系统命令相同的方式展开通配符。 （如果您不熟悉通配符，请参阅操作系统的用户指南。）

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[链接选项](../c-runtime-library/link-options.md)<br/>
[main 函数和程序执行](../c-language/main-function-and-program-execution.md)