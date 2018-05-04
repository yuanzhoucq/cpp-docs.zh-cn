---
title: 推断出的依赖项 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86ed1a8fe6c97ae11af50f59cb639ef6fd7c1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="inferred-dependents"></a>推导出的依赖项
推理依赖项从推理规则中派生，并进行评估之前显式依赖项。 如果相对于其目标过期推理依赖项，NMAKE 调用依赖项的命令块。 如果推断依赖于不存在或已过期相对于其自身的依赖项，则 NMAKE 首先更新推理依赖项。 有关推理依赖项的详细信息，请参阅[推理规则](../build/inference-rules.md)。  
  
## <a name="see-also"></a>请参阅  
 [依赖项](../build/dependents.md)