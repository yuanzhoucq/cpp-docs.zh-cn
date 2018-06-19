---
title: 描述块 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0784f08c479a8c8f3968ef61a01431cd9e0ca71e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367103"
---
# <a name="description-blocks"></a>描述块
描述块是依赖项行 （可选） 后跟命令块：  
  
```  
targets... : dependents...  
    commands...  
```  
  
 依赖项行指定一个或多个目标和零个或多个依赖项。 目标必须是在行的开头。 不允许从以冒号 （:） 的依赖项的单独目标; 空格或制表符。 若要拆分的行，目标或依赖项之后，使用反斜杠 (\)。 如果目标不存在，具有较早的时间戳比相关，或者为[伪目标](../build/pseudotargets.md)，NMAKE 执行的命令。 如果依赖于其他地方是目标并不存在或已过期相对于其自身的依赖项，NMAKE 更新当前依赖项之前更新依赖项。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [目标](../build/targets.md)  
  
 [依赖项](../build/dependents.md)  
  
## <a name="see-also"></a>请参阅  
 [NMAKE 参考](../build/nmake-reference.md)