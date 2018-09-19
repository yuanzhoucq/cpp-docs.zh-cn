---
title: 推断出的依赖项 |Microsoft Docs
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
ms.openlocfilehash: 631c5631b60f0e05dd1f1541facc767f35944d3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701475"
---
# <a name="inferred-dependents"></a>推导出的依赖项

推断出依赖于派生自的推断规则并进行评估之前显式依赖项。 如果推断出依赖于相对于其目标过期，NMAKE 调用的依赖项的命令块。 如果推断出依赖于不存在或已过期相对于其自己的依赖项，NMAKE 首先更新推理依赖项。 有关推理依赖项的详细信息，请参阅[推理规则](../build/inference-rules.md)。

## <a name="see-also"></a>请参阅

[依赖项](../build/dependents.md)