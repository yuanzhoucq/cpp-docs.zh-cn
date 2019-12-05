---
title: ML 非致命错误 A2008
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 192d82186a58d4e6b534ab5ec65b696d4d7ce3ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856748"
---
# <a name="ml-nonfatal-error-a2008"></a>ML 非致命错误 A2008

**语法错误：**

当前位置的标记导致了语法错误。

可能发生了下列情况之一：

- 在指令中添加或省略了点前缀。

- 保留字（如**C**或**SIZE**）用作标识符。

- 使用的指令不适用于当前处理器或协处理器选择。

- 比较运行时运算符（如 `==`）在条件程序集语句中使用，而不是在关系运算符（如[EQ](../../assembler/masm/operator-eq.md)）中使用。

- 给定的指令或指令的操作数太少。

- 使用了过时的指令。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>