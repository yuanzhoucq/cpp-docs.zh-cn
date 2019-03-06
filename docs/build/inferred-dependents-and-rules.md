---
title: 推导出的依赖项和规则
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: 125d64c47fb8ac9cd86269bedf246a131eda57e7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414828"
---
# <a name="inferred-dependents-and-rules"></a>推导出的依赖项和规则

如果存在适用的推理规则 NMAKE 采用推断的目标的依赖项。 如果，应用了一个规则：

- *toext*匹配目标的文件扩展名。

- *fromext*匹配项的当前或指定的目录中存在具有目标的基名称，且文件的扩展名。

- *fromext*处于[。后缀](../build/dot-directives.md); 没有其他*fromext*匹配规则中具有更高 **。后缀**优先级。

- 没有显式依赖项具有更高 **。后缀**优先级。

推断出的依赖项可能会导致意外的副作用。 如果目标的描述块中包含的命令，NMAKE 规则中执行这些命令而不是命令。

## <a name="see-also"></a>请参阅

[推理规则](../build/inference-rules.md)
