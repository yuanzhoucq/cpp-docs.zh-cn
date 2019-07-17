---
title: /DEPENDENTS
ms.date: 07/15/2019
f1_keywords:
- /dependents
helpviewer_keywords:
- -DEPENDENTS dumpbin option
- /DEPENDENTS dumpbin option
- DEPENDENTS dumpbin option
ms.assetid: 9b31da2a-75ac-4bbf-a3f1-adf8b0ecbbb4
ms.openlocfilehash: 88f0062a6bbca3f9199a12f739c2ade5f9d912cd
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299748"
---
# <a name="dependents"></a>/DEPENDENTS

转储图像从中导入函数的 Dll 的名称。 您可以使用该列表来确定要与应用程序一起重新分发的 Dll, 或查找缺少的依赖项的名称。

## <a name="syntax"></a>语法

> **/DEPENDENTS**

此选项适用于在命令行中指定的所有可执行文件。 它不采用任何参数。

## <a name="remarks"></a>备注

**/DEPENDENTS**选项添加了图像将函数导入到输出的 dll 的名称。 此选项不会转储导入的函数的名称。 若要查看导入函数的名称, 请使用[/IMPORTS](imports-dumpbin.md)选项。

只有 [/HEADERS](headers.md) DUMPBIN 选项可用于由 [/GL](gl-whole-program-optimization.md) 编译器选项产生的文件。

## <a name="example"></a>示例

此示例显示了在演练中[生成的客户端可执行文件上的 **/DEPENDENTS**选项的 DUMPBIN 输出:创建和使用自己的动态链接库](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md):

```cmd
C:\Users\username\Source\Repos\MathClient\Debug>dumpbin /DEPENDENTS MathClient.exe
Microsoft (R) COFF/PE Dumper Version 14.16.27032.1
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file MathClient1322.exe

File Type: EXECUTABLE IMAGE

  Image has the following dependencies:

    MathLibrary.dll
    MSVCP140D.dll
    VCRUNTIME140D.dll
    ucrtbased.dll
    KERNEL32.dll

  Summary

        1000 .00cfg
        1000 .data
        2000 .idata
        1000 .msvcjmc
        3000 .rdata
        1000 .reloc
        1000 .rsrc
        8000 .text
       10000 .textbss
```

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](dumpbin-options.md)
