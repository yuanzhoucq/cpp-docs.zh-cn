---
title: 伪目标
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
ms.openlocfilehash: bf0f1e2feb91611222ade366a7644e89cbe22600
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541071"
---
# <a name="pseudotargets"></a>伪目标

伪目标是用来替代依赖关系行中的文件名的标签。 它被解释为的文件不存在，因此已过期。 NMAKE 假定伪目标的时间戳是最新创建的所有依赖项。 如果不有任何依赖项，则假定当前时间。 如果伪目标用作目标，始终执行其命令。 用作一个相关的伪必须也显示为另一个依赖项中的目标。 但是，该依赖项不需要具有命令块。

伪目标名称遵循目标的文件名语法规则。 但是，如果名称不具有扩展名 （即，不包含句点），它可能会超过 8 个字符的文件名长度限制，可以是最多 256 个字符之间。

## <a name="see-also"></a>请参阅

[目标](../build/targets.md)