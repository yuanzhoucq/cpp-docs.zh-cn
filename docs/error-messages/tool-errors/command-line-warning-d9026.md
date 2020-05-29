---
title: 命令行警告 D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 59dfcdc97fb9caf60a018cb20583ee6fca3dcb27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196698"
---
# <a name="command-line-warning-d9026"></a>命令行警告 D9026

选项应用于整个命令行

指定文件名后，在命令上指定了一个选项。 此选项已应用于其前面的文件。

例如，在命令

```
CL verdi.c /G5 puccini.c
```

将使用/G5 选项而不是/G4 默认值编译文件 VERDI。

此行为不同于一些以前版本的行为，这种行为仅应用文件名之前指定的选项，导致 VERDI 使用/G4 和 PUCCINI 进行编译，并使用/G5. 进行编译
