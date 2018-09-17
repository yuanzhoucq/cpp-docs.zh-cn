---
title: 目标 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: edb75258c548526c68ed33f7f8037656750f6855
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713788"
---
# <a name="targets"></a>目标

在依赖关系行中，指定一个或多个目标，使用任何有效的文件名、 目录名称，或[伪目标](../build/pseudotargets.md)。 使用一个或多个空格或制表符分隔多个目标。 目标是不区分大小写。 路径允许使用的文件名。 目标不能超过 256 个字符。 如果位于冒号之前的目标是单个字符，使用的分隔空间;否则，NMAKE 将解释为驱动器说明符的字母冒号组合。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[伪目标](../build/pseudotargets.md)

[多个目标](../build/multiple-targets.md)

[累计依赖项](../build/cumulative-dependencies.md)

[多个描述块中的目标](../build/targets-in-multiple-description-blocks.md)

[依赖项副作用](../build/dependency-side-effects.md)

## <a name="see-also"></a>请参阅

[描述块](../build/description-blocks.md)