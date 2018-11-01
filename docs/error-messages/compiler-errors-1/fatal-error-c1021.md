---
title: 错误 C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 35b94e6cea177121c38d06706b42437ec610c38a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587094"
---
# <a name="fatal-error-c1021"></a>错误 C1021

无效的预处理器命令“string”

`string` 不是有效的 [预处理器指令](../../preprocessor/preprocessor-directives.md)。 若要解决此错误，请使用对于 `string`有效预处理器名称。

下面的示例生成 C1021：

```
// C1021.cpp
#BadPreProcName    // C1021 delete line
```