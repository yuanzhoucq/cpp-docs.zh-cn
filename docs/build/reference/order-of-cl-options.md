---
title: CL 选项的顺序 |Microsoft 文档
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
ms.openlocfilehash: 165e20eefecd20ad9dec9e01b38c5eaa7926e4eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372804"
---
# <a name="order-of-cl-options"></a>CL 选项的顺序
选项可以显示在 CL 命令行中，除 /link 选项，它必须出现在最后的任意位置。 编译器开头中指定的选项[CL 环境变量](../../build/reference/cl-environment-variables.md)，然后从左到右读取命令行-处理命令文件中遇到它们的顺序。 每个选项适用于命令行上的所有文件。 如果 CL 遇到冲突的选项，它将使用最右边的选项。  
  
## <a name="see-also"></a>请参阅  
 [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)