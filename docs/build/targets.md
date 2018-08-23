---
title: 目标 |Microsoft 文档
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
ms.openlocfilehash: 79e9d72d2b2fb999d987a6781caace9a0360facb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380257"
---
# <a name="targets"></a>目标
在依赖项行中，指定一个或多个目标，使用任何有效的文件名、 目录名或[伪目标](../build/pseudotargets.md)。 用一个或多个空格或制表符分隔多个目标。 目标不区分大小写。 路径被允许对文件名。 目标不能超过 256 个字符。 如果位于冒号前的目标是单个字符，使用分隔开来将空间;否则，NMAKE 将解释为一个驱动器说明符的字母冒号组合。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [伪目标](../build/pseudotargets.md)  
  
 [多个目标](../build/multiple-targets.md)  
  
 [累计依赖项](../build/cumulative-dependencies.md)  
  
 [多个描述块中的目标](../build/targets-in-multiple-description-blocks.md)  
  
 [依赖项副作用](../build/dependency-side-effects.md)  
  
## <a name="see-also"></a>请参阅  
 [描述块](../build/description-blocks.md)