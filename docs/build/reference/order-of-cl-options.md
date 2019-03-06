---
title: CL 选项的顺序
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: d87e3214d4829f81258acd00abebced34d7d969d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423685"
---
# <a name="order-of-cl-options"></a>CL 选项的顺序

选项可以显示在 CL 命令行中，除了 /link 选项，它必须出现在最后的任意位置。 编译器首先处理中指定的选项[CL 环境变量](../../build/reference/cl-environment-variables.md)，然后从左到右读取命令行-按顺序会在遇到命令文件处理。 每个选项适用于在命令行上的所有文件。 如果 CL 遇到冲突的选项，它使用的最右侧的选项。

## <a name="see-also"></a>请参阅

[编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)
