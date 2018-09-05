---
title: 优化内联程序集 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49660bdc6d2eb84e6e1bbaeb5ebf0d57e484e9e1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687871"
---
# <a name="optimizing-inline-assembly"></a>优化内联汇编程序

**Microsoft 专用**

如果函数中存在 `__asm` 块，则会在多个方面影响优化。 首先，编译器不会尝试优化 `__asm` 块本身。 您在汇编语言中编写的内容就是您获得的内容。 第二，存在 `__asm` 块将影响寄存器变量存储。 如果寄存器的内容将被 `__asm` 块更改，编译器将避免在 `__asm` 块中注册变量。 最后，其他某些函数范围的优化将受函数中包含的汇编语言的影响。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>