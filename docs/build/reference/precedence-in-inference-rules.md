---
title: 推理规则中的优先级
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: ca24134fd1829ad3d97ca67b8c30aae3af4109ee
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824865"
---
# <a name="precedence-in-inference-rules"></a>推理规则中的优先级

如果有多个定义推理规则，NMAKE 使用优先级最高的定义。 以下列表显示了从最高优先级到最低的优先级顺序：

1. 生成文件; 中定义的推理规则更高版本的定义具有的优先级。

1. Tools.ini; 中定义的推理规则更高版本的定义具有的优先级。

1. 预定义的推理规则。

## <a name="see-also"></a>请参阅

[推理规则](inference-rules.md)
