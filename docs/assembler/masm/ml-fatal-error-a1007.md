---
title: ML 错误 A1007
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: c9527769e0d9397de90f49cbce98b2cca42bed50
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317118"
---
# <a name="ml-fatal-error-a1007"></a>ML 错误 A1007

**嵌套级别太深**

汇编程序已达到其嵌套限制。 限制为20个级别，但在其他情况下除外。

下面其中一个内容嵌套太深：

- 高级指令，如[。如果](dot-if.md)为，则为[。重复](dot-repeat.md)或[。WHILE](dot-while.md)。

- 结构定义。

- 条件程序集指令。

- 过程定义。

- [PUSHCONTEXT](pushcontext.md)指令（限制为10）。

- 分段定义。

- 包含文件。

- 宏。

## <a name="see-also"></a>另请参阅

[ML 错误消息](ml-error-messages.md)
