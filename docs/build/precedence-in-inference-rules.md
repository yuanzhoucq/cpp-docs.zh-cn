---
title: 推理规则中的优先级
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: 30dee54c99115c076f7662bafb8aa22d97f234fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548728"
---
# <a name="precedence-in-inference-rules"></a>推理规则中的优先级

如果有多个定义推理规则，NMAKE 使用优先级最高的定义。 以下列表显示了从最高优先级到最低的优先级顺序：

1. 生成文件; 中定义的推理规则更高版本的定义具有的优先级。

1. Tools.ini; 中定义的推理规则更高版本的定义具有的优先级。

1. 预定义的推理规则。

## <a name="see-also"></a>请参阅

[推理规则](../build/inference-rules.md)