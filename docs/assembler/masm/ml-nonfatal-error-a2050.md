---
title: ML 非致命错误 A2050 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd2e0e6c2fc818ef9286fd303c07a26bdd8b4e5a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680666"
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非致命错误 A2050

**实际或不允许使用 BCD 数字**

（实际） 的浮点数或二进制编码的十进制 (BCD) 常量而不使用作为数据初始值设定项。

出现下列情况之一：

- 表达式中使用的一个实数或者 BCD。

- 一个实数用于初始化一个指令之外[DWORD](../../assembler/masm/dword.md)， [QWORD](../../assembler/masm/qword.md)，或[TBYTE](../../assembler/masm/tbyte.md)。

- BCD 用于初始化一个指令之外`TBYTE`。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>