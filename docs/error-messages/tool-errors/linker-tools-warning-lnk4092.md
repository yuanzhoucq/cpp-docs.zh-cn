---
title: 链接器工具警告 LNK4092 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b47b347e11e640425bc7840a0f78a33e9e3b7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113417"
---
# <a name="linker-tools-warning-lnk4092"></a>链接器工具警告 LNK4092

共享的可写节部分包含重定位;映像可能无法正确运行

只要您有共享的章节来警告你潜在的严重问题，链接器将发出此警告。

多个进程之间共享数据的一种方法是将标记为"共享"部分 但是，将标记为共享部分可能会导致问题。 例如，您有一个 DLL，它包含此类共享的数据节中的声明：

```
int var = 1;
int *pvar = &var;
```

链接器无法解析`pvar`因为其值取决于在内存中加载该 DLL 的位置，因此它放入一个重定位记录在 DLL 中。 如果 DLL 加载到内存的地址`var`可以解析和`pvar`分配。 如果另一个进程加载同一个 DLL，但不能加载它在同一地址，地址的重定位`var`将第二个进程和第一个进程的地址空间将指向错误的地址更新。