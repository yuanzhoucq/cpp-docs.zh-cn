---
title: 环境名称
ms.date: 11/04/2016
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
ms.openlocfilehash: 43e1254b4c1ee61a92fbb6499d9396e8b15a3047
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234122"
---
# <a name="environment-names"></a>环境名称

**ANSI 4.10.4.4** 环境名称集和用于更改 [getenv](../c-runtime-library/reference/getenv-wgetenv.md) 函数使用的环境列表的方法

环境名称集是不受限的。

若要从 C 程序中更改环境变量，请调用 [_putenv](../c-runtime-library/reference/putenv-wputenv.md) 函数。 若要从 Windows 命令行中更改环境变量，请使用 SET 命令（例如，SET LIB = D:\ LIBS）。

C 程序内的环境变量集仅在操作系统命令外壳（CMD.EXE 或 COMMAND.COM）的主机副本运行时存在。 例如，行

```
system( SET LIB = D:\LIBS );
```

将运行命令外壳 (CMD.EXE) 的副本、设置环境变量 LIB 并返回 C 程序，同时退出 CMD.EXE 的辅助副本。 退出 CMD.EXE 的副本将移除临时环境变量 LIB。

同样，仅保留 `_putenv` 函数所做的更改，直到该程序结束。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)<br/>
[_putenv、_wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[getenv、_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)
