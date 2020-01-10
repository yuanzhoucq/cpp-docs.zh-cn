---
title: ML 错误 A1010
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: b3141f8819a33281c70e34bd7772d4475886e557
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312581"
---
# <a name="ml-fatal-error-a1010"></a>ML 错误 A1010

**不匹配的块嵌套：**

块开始没有匹配的结尾，或块结束没有匹配的开头。 可能涉及以下内容之一：

- 高级指令，如[。如果](dot-if.md)为，则为[。重复](dot-repeat.md)或[。WHILE](dot-while.md)。

- 条件程序集指令，如[IF](if-masm.md)、 [REPEAT](repeat.md)或**WHILE**。

- 结构或联合定义。

- 过程定义。

- 分段定义。

- [POPCONTEXT](popcontext.md)指令。

- 条件程序集指令，例如[ELSE](else-masm.md)、 [ELSEIF](elseif-masm.md)或**ENDIF** ，无需匹配[IF](if-masm.md)。

## <a name="see-also"></a>另请参阅

[ML 错误消息](ml-error-messages.md)
