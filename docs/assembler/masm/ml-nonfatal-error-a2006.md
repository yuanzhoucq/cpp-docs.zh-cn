---
title: ML 非致命错误 A2006 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f287c6ab46c6af71ba6dc0032f332ce3cc489454
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677400"
---
# <a name="ml-nonfatal-error-a2006"></a>ML 非致命错误 A2006

**未定义的符号： 标识符**

尝试使用未定义的符号。

可能会发生下列情况之一：

- 未定义符号。

- 字段不是结构的指定的成员。

- 未包含的包含文件中定义了符号。

- 在未使用的外部符号[EXTERN](../../assembler/masm/extern-masm.md)或[EXTERNDEF](../../assembler/masm/externdef.md)指令。

- 符号名称时拼写错误。

- 在作用域外引用了本地代码标签。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>