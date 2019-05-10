---
title: ML 非致命错误 A2050
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 59d08b9c2743a3b45633527bcc54b3e1c4d6a58c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177547"
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