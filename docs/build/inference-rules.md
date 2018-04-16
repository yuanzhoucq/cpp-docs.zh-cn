---
title: "推理规则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 932aad860cd2b78208857ca7b028e35cd96d481e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="inference-rules"></a>推理规则
推理规则提供命令来更新目标，并可以推断目标的依赖项。 推理规则中的扩展匹配单个目标并具有相同的基名称的依赖。 推理规则是用户定义的或预定义的;可以重新定义预定义的规则。  
  
 如果过期的依赖项不具有任何命令，并且如果[。后缀](../build/dot-directives.md)包含依赖项的扩展，NMAKE 使用其扩展匹配的目标和现有的规则文件中的当前或指定的目录。 如果多个规则匹配现有文件的文件， **。后缀**列表确定使用哪; 从左到右的列表优先级递减。 如果依赖文件不存在，并且不被列为在另一个描述块中的目标，推理规则可以创建缺少的依赖从具有相同的基名称的另一个文件。 如果描述块的目标没有依赖项或命令，推理规则可以更新目标。 推理规则可以生成的命令行目标，即使不存在描述块。 NMAKE 可能会调用推理依赖项的规则，即使指定了显式依赖项。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [定义规则](../build/defining-a-rule.md)  
  
 [批模式规则](../build/batch-mode-rules.md)  
  
 [预定义的规则](../build/predefined-rules.md)  
  
 [推断出的依赖项和规则](../build/inferred-dependents-and-rules.md)  
  
 [推理规则中的优先级](../build/precedence-in-inference-rules.md)  
  
## <a name="see-also"></a>请参阅  
 [NMAKE 参考](../build/nmake-reference.md)