---
title: 命令行警告 D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 3fd8d442dfabaf2f03d8b564c9fdfb1537f6ff28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599428"
---
# <a name="command-line-warning-d9026"></a>命令行警告 D9026

选项适用于整个命令行

指定文件名后，在命令中指定一个选项。 该选项被应用于它前面有该文件。

例如，在命令中

```
CL verdi.c /G5 puccini.c
```

将使用用 /G5 选项，而不是 /G4 默认编译文件 VERDI.c。

此行为是不同的某些早期版本中，此方法仅指定文件名，从而导致 VERDI.c 之前的选项所编译使用/G4 和 PUCCINI.c 正在编译使用用 /G5。