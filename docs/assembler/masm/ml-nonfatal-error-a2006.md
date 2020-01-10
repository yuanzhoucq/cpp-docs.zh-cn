---
title: ML 非致命错误 A2006
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 058100984acbd42ac2993732ab619c0a27c0edd2
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317079"
---
# <a name="ml-nonfatal-error-a2006"></a>ML 非致命错误 A2006

**未定义的符号：标识符**

尝试使用未定义的符号。

可能发生了下列情况之一：

- 未定义符号。

- 某个字段不是指定结构的成员。

- 未包含在包含文件中的符号。

- 在没有[EXTERN](extern-masm.md)或[EXTERNDEF](externdef.md)指令的情况下使用了外部符号。

- 符号名拼写错误。

- 在其范围之外引用了本地代码标签。

## <a name="see-also"></a>另请参阅

[ML 错误消息](ml-error-messages.md)
