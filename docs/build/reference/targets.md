---
title: 目标
ms.date: 11/04/2016
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
ms.openlocfilehash: 52b2f3293b97955b605e2821102247f506c2950b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040843"
---
# <a name="targets"></a>目标

在依赖关系行中，指定一个或多个目标，使用任何有效的文件名、 目录名称，或[伪目标](pseudotargets.md)。 使用一个或多个空格或制表符分隔多个目标。 目标是不区分大小写。 路径允许使用的文件名。 目标不能超过 256 个字符。 如果位于冒号之前的目标是单个字符，使用的分隔空间;否则，NMAKE 将解释为驱动器说明符的字母冒号组合。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[伪目标](pseudotargets.md)

[多个目标](multiple-targets.md)

[累计依赖项](cumulative-dependencies.md)

[多个描述块中的目标](targets-in-multiple-description-blocks.md)

[依赖项副作用](dependency-side-effects.md)

## <a name="see-also"></a>请参阅

[描述块](description-blocks.md)