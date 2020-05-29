---
title: 链接器工具警告 LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 706ab843f4b079b507033af76a7f407816fce820
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183353"
---
# <a name="linker-tools-warning-lnk4092"></a>链接器工具警告 LNK4092

共享的可写节 "section" 包含重定位;图像可能无法正确运行

当你有共享部分时，链接器将发出此警告，以便警告你潜在的严重问题。

在多个进程之间共享数据的一种方法是将节标记为 "shared"。 但是，将节标记为共享可能会导致问题。 例如，你有一个 DLL，它在共享数据部分中包含如下所示的声明：

```
int var = 1;
int *pvar = &var;
```

链接器无法解析 `pvar`，因为它的值取决于在内存中加载 DLL 的位置，因此它将重定位记录置于 DLL 中。 将 DLL 加载到内存中时，可以解析 `var` 的地址并 `pvar` 分配。 如果其他进程加载同一 DLL 但无法在同一地址加载它，则将为第二个进程更新 `var` 地址的重定位，第一个进程的地址空间将指向错误的地址。
