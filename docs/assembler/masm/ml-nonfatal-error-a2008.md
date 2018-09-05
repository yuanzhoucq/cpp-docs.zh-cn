---
title: ML 非致命错误 A2008 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 774cf4c2a51bf084fb63e572cc99b0c8e3cba26f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679370"
---
# <a name="ml-nonfatal-error-a2008"></a>ML 非致命错误 A2008

**语法错误：**

在当前位置令牌导致语法错误。

可能会发生下列情况之一：

- 圆点前缀已添加到或从一个指令中省略。

- 保留的字 (如**C**或**大小**) 用作标识符。

- 使用不可用与当前的处理器或协处理器选择一条指令。

- 比较运行时运算符 (如`==`) 而不是关系运算符的条件的程序集语句中使用 (如[EQ](../../assembler/masm/operator-eq.md))。

- 指令提供过少的操作数。

- 使用已过时的指令。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>