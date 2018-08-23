---
title: 伪目标 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67dbc6ae3ad331ab3297b62d00044c3edf679994
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368403"
---
# <a name="pseudotargets"></a>伪目标
伪目标是代替是依赖项的行中的文件名的标签。 它被解释为不存在，因此可能会过期的文件。 NMAKE 假定伪目标的时间戳是最新创建的所有依赖项。 如果已没有依赖项，则假定当前时间。 如果伪目标用作目标，则始终执行其命令。 伪目标用作依赖还必须显示为另一个依赖项中的目标。 但是，该依赖关系不必命令块。  
  
 伪目标名称遵循目标的文件名语法规则。 但是，如果名称不具有扩展名 （即，不包含句点），它可以超出 8 个字符的限制文件名，可以最多 256 个字符。  
  
## <a name="see-also"></a>请参阅  
 [目标](../build/targets.md)