---
title: "伪目标 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b018cd586e48f344b93b31571ba60ae9982ad4fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pseudotargets"></a>伪目标
伪目标是代替是依赖项的行中的文件名的标签。 它被解释为不存在，因此可能会过期的文件。 NMAKE 假定伪目标的时间戳是最新创建的所有依赖项。 如果已没有依赖项，则假定当前时间。 如果伪目标用作目标，则始终执行其命令。 伪目标用作依赖还必须显示为另一个依赖项中的目标。 但是，该依赖关系不必命令块。  
  
 伪目标名称遵循目标的文件名语法规则。 但是，如果名称不具有扩展名 （即，不包含句点），它可以超出 8 个字符的限制文件名，可以最多 256 个字符。  
  
## <a name="see-also"></a>另请参阅  
 [目标](../build/targets.md)