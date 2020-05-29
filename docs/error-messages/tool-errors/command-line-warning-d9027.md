---
title: 命令行警告 D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 46ed5750bd1f315f20658ace9b83fac532fbbabb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196672"
---
# <a name="command-line-warning-d9027"></a>命令行警告 D9027

已忽略源文件 "\<filename >"

CL 已忽略输入源文件。

此警告可能由使用/c 选项的命令行上的/Fo 选项和输出文件名之间的空格引起。 例如：

```
cl /c /Fo output.obj input.c
```

由于/Fo 与 `output.obj`之间有一个空格，因此 node.js 会将 `output.obj` 作为输入文件的名称。 若要解决此问题，请删除以下空间：

```
cl /c /Fooutput.obj input.c
```
