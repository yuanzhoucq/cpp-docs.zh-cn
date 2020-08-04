---
title: 使用调试版本检查内存改写
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 152f72749d2ebdacd46dd3e4db671bc5705d4b6a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213744"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>使用调试版本检查内存改写

要使用调试版本检查内存覆盖，必须首先重新生成用于调试的项目。 然后，转到应用程序 `InitInstance` 函数的开头，并添加以下行：

```
afxMemDF |= checkAlwaysMemDF;
```

调试内存分配器会在所有内存分配周围放置保护字节。 但这些保护字节没有任何用处，除非检查它们是否已被更改（这将指示内存覆盖）。 否则，这只是提供一个缓冲区，实际上可能允许你摆脱内存覆盖。

通过启用 `checkAlwaysMemDF`，你将强制 MFC 在每次调用 `new` 或 `delete` 时都调用 `AfxCheckMemory` 函数。 如果检测到内存覆盖，它将生成类似于以下内容的 TRACE 消息：

```
Damage Occurred! Block=0x5533
```

如果看到这些消息之一，则需要单步执行代码以确定发生损坏的位置。 若要更精确地隔离内存覆盖发生的位置，可以自行显式调用 `AfxCheckMemory`。 例如：

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

如果第一个 ASSERT 成功，而第二个 ASSERT 失败，则意味着内存覆盖一定发生在这两个调用之间的函数中。

根据应用程序的特性，你可能会发现 `afxMemDF` 会导致程序运行太慢，甚至无法进行测试。 `afxMemDF` 变量会导致每次调用 new 和 delete 时都调用 `AfxCheckMemory`。 在这种情况下，应分散对 `AfxCheckMemory`( ) 的调用（如上所示），并尝试隔离内存覆盖。

## <a name="see-also"></a>请参阅

[修复发行版本问题](fixing-release-build-problems.md)
