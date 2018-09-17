---
title: 推理规则 |Microsoft Docs
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
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed45e5ad61ea1cc50172cd86716b357baa64fa39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724374"
---
# <a name="inference-rules"></a>推理规则

推理规则提供命令以更新目标并可以推断目标的依赖项。 推理规则中的扩展匹配单个目标，并依赖于具有相同的基名称。 推理规则是用户定义的或预定义;可以重新定义预定义的规则。

如果过期的依赖项不具有任何命令，并且如果[。后缀](../build/dot-directives.md)包含依赖项的扩展，NMAKE 会使用当前或指定目录中文件的扩展名匹配的目标和现有的规则。 如果多个规则匹配现有的文件， **。后缀**列表确定使用哪个; 列表优先级自从左到右。 如果依赖文件不存在，并且未列为另一个描述块中的目标，推理规则可以创建缺少的依赖从另一个文件具有相同基名称。 如果描述块的目标没有依赖项或命令，推理规则可以更新目标。 推理规则可以生成命令行目标，即使不存在描述块。 NMAKE 可能调用推理依赖项规则，即使指定了显式依赖项。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[定义规则](../build/defining-a-rule.md)

[批模式规则](../build/batch-mode-rules.md)

[预定义的规则](../build/predefined-rules.md)

[推断出的依赖项和规则](../build/inferred-dependents-and-rules.md)

[推理规则中的优先级](../build/precedence-in-inference-rules.md)

## <a name="see-also"></a>请参阅

[NMAKE 参考](../build/nmake-reference.md)