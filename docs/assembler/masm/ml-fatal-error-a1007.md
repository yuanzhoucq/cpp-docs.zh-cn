---
title: ML 错误 A1007
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 01633b4fa084b7d5e14af5a5c6e51e3dca684d2a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856912"
---
# <a name="ml-fatal-error-a1007"></a>ML 错误 A1007

**嵌套级别太深**

汇编程序已达到其嵌套限制。 限制为20个级别，但在其他情况下除外。

下面其中一个内容嵌套太深：

- 高级指令，如[。如果](../../assembler/masm/dot-if.md)为，则为[。重复](../../assembler/masm/dot-repeat.md)或[。WHILE](../../assembler/masm/dot-while.md)。

- 结构定义。

- 条件程序集指令。

- 过程定义。

- [PUSHCONTEXT](../../assembler/masm/pushcontext.md)指令（限制为10）。

- 分段定义。

- 包含文件。

- 宏。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>