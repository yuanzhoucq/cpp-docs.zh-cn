---
title: ML 非致命错误 A2133
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 9e13dd48c77b9574229023e3cfc4cc2f2221d153
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62201205"
---
# <a name="ml-nonfatal-error-a2133"></a>ML 非致命错误 A2133

**注册调用被覆盖的值**

寄存器作为参数传递给过程，但生成的代码[INVOKE](../../assembler/masm/invoke.md)传递其他参数销毁寄存器的内容。

AX、 AL、 AH、 EAX、 DX、 DL、 DH 和 EDX 寄存器可能由组装器，用于执行数据转换。

使用不同的注册。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>