---
title: 指定内联文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73983094f10088920100b4fbbb8d870aee13f05e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720559"
---
# <a name="specifying-an-inline-file"></a>指定内联文件

指定两个尖括号 (<<) 命令中位置*文件名*将出现。 在尖括号内不能是宏扩展。

## <a name="syntax"></a>语法

```
<<[filename]
```

## <a name="remarks"></a>备注

当运行该命令时，替换尖括号*文件名*、 如果指定，或通过将 NMAKE 生成的唯一名称。 如果指定，*文件名*必须遵循尖括号而无需空格或制表符。允许的路径。 需要或采用没有扩展名。 如果*文件名*文件创建在当前的指定或指定的目录，该名称覆盖任何现有文件; 否则为 TMP 目录中创建 (或当前目录中，如果 TMP 环境变量未定义）。 如果上一次*文件名*是重复使用，NMAKE 取代了以前的文件。

## <a name="see-also"></a>请参阅

[生成文件中的内联文件](../build/inline-files-in-a-makefile.md)