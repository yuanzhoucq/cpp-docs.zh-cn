---
title: 编译器错误 C2414 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2414
dev_langs:
- C++
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22710e0056a7dea65130a65a3ccb9c5310f1c39f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226158"
---
# <a name="compiler-error-c2414"></a>编译器错误 C2414
非法的操作数的数目  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  操作码不支持的使用的操作数的数目。 检查程序集语言参考手册 》 来确定的正确数目的操作数。  
  
2.  较新的处理器支持的指令与不同数目的操作数。 调整[/arch （最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)选项以使用更高版本的处理器。