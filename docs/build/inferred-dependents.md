---
title: 推导出的依赖项
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: d4d12d0ab686c604ce0d4495df89ec62c6160ebe
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414143"
---
# <a name="inferred-dependents"></a>推导出的依赖项

推断出依赖于派生自的推断规则并进行评估之前显式依赖项。 如果推断出依赖于相对于其目标过期，NMAKE 调用的依赖项的命令块。 如果推断出依赖于不存在或已过期相对于其自己的依赖项，NMAKE 首先更新推理依赖项。 有关推理依赖项的详细信息，请参阅[推理规则](../build/inference-rules.md)。

## <a name="see-also"></a>请参阅

[依赖项](../build/dependents.md)
