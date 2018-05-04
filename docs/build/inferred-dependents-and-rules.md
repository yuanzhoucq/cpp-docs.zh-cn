---
title: 推断出的依赖项和规则 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aae09fd756e0eb4eab3031beb5b4cba8c4d35a40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="inferred-dependents-and-rules"></a>推导出的依赖项和规则
如果存在适用的推理规则 NMAKE 采用推断的目标的依赖项。 规则适用下列情况：  
  
-   *toext*匹配目标的文件扩展名。  
  
-   *fromext*匹配项的当前或指定的目录中存在具有目标的基名称，且文件的扩展名。  
  
-   *fromext*处于[。后缀](../build/dot-directives.md); 任何其他*fromext*在匹配规则具有更高**。后缀**优先级。  
  
-   没有显式依赖项具有更高**。后缀**优先级。  
  
 推理依赖项可能会导致意外的副作用。 如果目标的描述块包含命令，NMAKE 规则中执行这些命令而不是命令。  
  
## <a name="see-also"></a>请参阅  
 [推理规则](../build/inference-rules.md)