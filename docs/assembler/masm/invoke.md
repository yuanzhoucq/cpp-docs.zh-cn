---
title: INVOKE
ms.date: 08/30/2018
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: efa8f710701e15845c3a6a22ba024c9cf1882457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579018"
---
# <a name="invoke"></a>INVOKE

在给定的地址调用该过程*表达式*，将自变量传递到堆栈上或在寄存器中根据语言类型的标准调用约定。

## <a name="syntax"></a>语法

> INVOKE*表达式*[[，*自变量*]]

## <a name="remarks"></a>备注

每个自变量传递给该过程可能是表达式、 是注册的对或地址表达式 (表达式前面`ADDR`)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>