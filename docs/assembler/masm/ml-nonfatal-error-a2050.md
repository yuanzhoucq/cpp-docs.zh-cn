---
title: ML 非致命错误 A2050
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 311aedd0cc739fd862efb0a18cc444b3fb75b165
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316975"
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非致命错误 A2050

**不允许使用 real 或 BCD 号**

使用了浮点（实数）数字或二进制编码的十进制（BCD）常量，而不是作为数据初始值设定项。

出现下列情况之一：

- 表达式中使用了实数或 BCD。

- 实数用于初始化[DWORD](dword.md)、 [QWORD](qword.md)或[TBYTE](tbyte.md)以外的指令。

- BCD 用于初始化除 `TBYTE`以外的指令。

## <a name="see-also"></a>另请参阅

[ML 错误消息](ml-error-messages.md)
