---
title: 命令行警告 D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: f89e7416efe7a0069ee2dae8df921933bbe76bcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214100"
---
# <a name="command-line-warning-d9027"></a>命令行警告 D9027

源文件\<文件名 > 被忽略

CL.exe 忽略输入的源文件。

此警告可能被引起 /Fo 选项与带有 /c 选项的命令行上输出文件名之间留一个空格。 例如：

```
cl /c /Fo output.obj input.c
```

因为 /Fo 之间没有空格和`output.obj`，CL.exe 将`output.obj`作为输入文件的名称。 若要解决此问题，请删除空间：

```
cl /c /Fooutput.obj input.c
```