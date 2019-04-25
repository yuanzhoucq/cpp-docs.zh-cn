---
title: ML 错误 A1007
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 98933c3a24da22f447174a3b51c4855690aba83e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177898"
---
# <a name="ml-fatal-error-a1007"></a>ML 错误 A1007

**嵌套级别太深**

在组装器已经达到其嵌套限制。 限制为 20 除外另行级别。

以下被嵌套太深：

- 如高级指令[。如果](../../assembler/masm/dot-if.md)， [。重复](../../assembler/masm/dot-repeat.md)，或[。虽然](../../assembler/masm/dot-while.md)。

- 结构定义。

- 一个条件程序集的指令。

- 过程定义。

- 一个[PUSHCONTEXT](../../assembler/masm/pushcontext.md)指令 （限制为 10）。

- 段定义。

- 包含文件。

- 宏。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>