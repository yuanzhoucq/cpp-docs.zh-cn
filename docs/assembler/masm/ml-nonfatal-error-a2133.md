---
title: ML 非致命错误 A2133
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: c2d13aefe02543129340bcc307771a1026776d61
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854610"
---
# <a name="ml-nonfatal-error-a2133"></a>ML 非致命错误 A2133

**register 值被调用覆盖**

寄存器作为参数传递给过程，但由[调用](../../assembler/masm/invoke.md)生成的代码通过其他自变量来传递注册的内容。

汇编程序可以使用 AX、AL、AH、EAX、DX、DL、DH 和 EDX 寄存器来执行数据转换。

使用其他寄存器。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>