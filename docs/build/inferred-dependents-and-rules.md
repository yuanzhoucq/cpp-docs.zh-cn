---
title: "推断出的依赖项和规则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe7c49607f466d8fd1d333883414b24d7837432b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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