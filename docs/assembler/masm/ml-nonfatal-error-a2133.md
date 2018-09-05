---
title: ML 非致命错误 A2133 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0df094f5e7135ffb3b9a5f09383e03e411755de3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678061"
---
# <a name="ml-nonfatal-error-a2133"></a>ML 非致命错误 A2133

**注册调用被覆盖的值**

寄存器作为参数传递给过程，但生成的代码[INVOKE](../../assembler/masm/invoke.md)传递其他参数销毁寄存器的内容。

AX、 AL、 AH、 EAX、 DX、 DL、 DH 和 EDX 寄存器可能由组装器，用于执行数据转换。

使用不同的注册。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>