---
title: CL 选项的顺序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffe9a440396df14823775db335e52bca6cacdb3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725011"
---
# <a name="order-of-cl-options"></a>CL 选项的顺序

选项可以显示在 CL 命令行中，除了 /link 选项，它必须出现在最后的任意位置。 编译器首先处理中指定的选项[CL 环境变量](../../build/reference/cl-environment-variables.md)，然后从左到右读取命令行-按顺序会在遇到命令文件处理。 每个选项适用于在命令行上的所有文件。 如果 CL 遇到冲突的选项，它使用的最右侧的选项。

## <a name="see-also"></a>请参阅

[编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)