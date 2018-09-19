---
title: 命令行警告 D9027 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 105ebbf62027ac3d9377c513c4f7c59e261b983d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112520"
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