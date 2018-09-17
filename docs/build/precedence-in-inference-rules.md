---
title: 推理规则中的优先级 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4f2e7ff55e935b7e425b552ba85f47f134c6b80
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725226"
---
# <a name="precedence-in-inference-rules"></a>推理规则中的优先级

如果有多个定义推理规则，NMAKE 使用优先级最高的定义。 以下列表显示了从最高优先级到最低的优先级顺序：

1. 生成文件; 中定义的推理规则更高版本的定义具有的优先级。

1. Tools.ini; 中定义的推理规则更高版本的定义具有的优先级。

1. 预定义的推理规则。

## <a name="see-also"></a>请参阅

[推理规则](../build/inference-rules.md)