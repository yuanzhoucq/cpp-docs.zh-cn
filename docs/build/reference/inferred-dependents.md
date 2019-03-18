---
title: 推导出的依赖项
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 2382dec960ef93fc2f73987ad27b4670768a68cc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824885"
---
# <a name="inferred-dependents"></a>推导出的依赖项

推断出依赖于派生自的推断规则并进行评估之前显式依赖项。 如果推断出依赖于相对于其目标过期，NMAKE 调用的依赖项的命令块。 如果推断出依赖于不存在或已过期相对于其自己的依赖项，NMAKE 首先更新推理依赖项。 有关推理依赖项的详细信息，请参阅[推理规则](inference-rules.md)。

## <a name="see-also"></a>请参阅

[依赖项](dependents.md)
