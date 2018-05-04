---
title: 函数类型 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 322bd45abbfe217671fd39f0617987fde21445db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="function-types"></a>函数类型
基本上，有两种类型的函数。 需要的堆栈帧的函数称为帧函数。 Leaf 函数调用函数，不需要的堆栈帧。  
  
 帧函数是分配堆栈空间、 调用其他函数，将保存非易失寄存器，或使用异常处理的函数。 它还要求函数表项。 帧函数需要 prolog 和 epilog。 帧函数可以动态分配堆栈空间，并且可以使用帧指针。 帧函数具有完整功能此调用在可供使用的标准。  
  
 如果帧函数不调用另一个函数，则它不需要对齐堆栈 (中部分引用[堆栈分配](../build/stack-allocation.md))。  
  
 Leaf 函数是指不需要函数表项。 它不能对任何非易失性寄存器，包括 RSP，这意味着它不能调用任何函数或分配堆栈空间进行更改。 它允许它执行的同时保留堆栈对齐。  
  
## <a name="see-also"></a>请参阅  
 [堆栈使用](../build/stack-usage.md)
