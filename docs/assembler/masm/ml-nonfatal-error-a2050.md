---
title: ML 非致命错误 A2050 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 159ed131c13166435114234b3b16a82cd4d41d1f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056189"
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非致命错误 A2050
**实时或不允许的 BCD 数字**  
  
 浮点 （实际） 数字或二进制编码的十进制 (BCD) 常量使用了除为数据初始值设定项。  
  
 出现以下之一：  
  
-   一个实数或 BCD 在表达式中使用了。  
  
-   一个实数用来初始化指令以外[DWORD](../../assembler/masm/dword.md)， [QWORD](../../assembler/masm/qword.md)，或[TBYTE](../../assembler/masm/tbyte.md)。  
  
-   BCD 用来初始化指令以外`TBYTE`。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)